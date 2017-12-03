
---

_You are currently looking at **version 1.1** of this notebook. To download notebooks and datafiles, as well as get help on Jupyter notebooks in the Coursera platform, visit the [Jupyter Notebook FAQ](https://www.coursera.org/learn/python-data-analysis/resources/0dhYG) course resource._

---


```python
import pandas as pd
import numpy as np
from scipy.stats import ttest_ind
```

# Assignment 4 - Hypothesis Testing
This assignment requires more individual learning than previous assignments - you are encouraged to check out the [pandas documentation](http://pandas.pydata.org/pandas-docs/stable/) to find functions or methods you might not have used yet, or ask questions on [Stack Overflow](http://stackoverflow.com/) and tag them as pandas and python related. And of course, the discussion forums are open for interaction with your peers and the course staff.

Definitions:
* A _quarter_ is a specific three month period, Q1 is January through March, Q2 is April through June, Q3 is July through September, Q4 is October through December.
* A _recession_ is defined as starting with two consecutive quarters of GDP decline, and ending with two consecutive quarters of GDP growth.
* A _recession bottom_ is the quarter within a recession which had the lowest GDP.
* A _university town_ is a city which has a high percentage of university students compared to the total population of the city.

**Hypothesis**: University towns have their mean housing prices less effected by recessions. Run a t-test to compare the ratio of the mean price of houses in university towns the quarter before the recession starts compared to the recession bottom. (`price_ratio=quarter_before_recession/recession_bottom`)

The following data files are available for this assignment:
* From the [Zillow research data site](http://www.zillow.com/research/data/) there is housing data for the United States. In particular the datafile for [all homes at a city level](http://files.zillowstatic.com/research/public/City/City_Zhvi_AllHomes.csv), ```City_Zhvi_AllHomes.csv```, has median home sale prices at a fine grained level.
* From the Wikipedia page on college towns is a list of [university towns in the United States](https://en.wikipedia.org/wiki/List_of_college_towns#College_towns_in_the_United_States) which has been copy and pasted into the file ```university_towns.txt```.
* From Bureau of Economic Analysis, US Department of Commerce, the [GDP over time](http://www.bea.gov/national/index.htm#gdp) of the United States in current dollars (use the chained value in 2009 dollars), in quarterly intervals, in the file ```gdplev.xls```. For this assignment, only look at GDP data from the first quarter of 2000 onward.

Each function in this assignment below is worth 10%, with the exception of ```run_ttest()```, which is worth 50%.


```python
# Use this dictionary to map state names to two letter acronyms
states = {'OH': 'Ohio', 'KY': 'Kentucky', 'AS': 'American Samoa', 'NV': 'Nevada', 'WY': 'Wyoming', 'NA': 'National', 'AL': 'Alabama', 'MD': 'Maryland', 'AK': 'Alaska', 'UT': 'Utah', 'OR': 'Oregon', 'MT': 'Montana', 'IL': 'Illinois', 'TN': 'Tennessee', 'DC': 'District of Columbia', 'VT': 'Vermont', 'ID': 'Idaho', 'AR': 'Arkansas', 'ME': 'Maine', 'WA': 'Washington', 'HI': 'Hawaii', 'WI': 'Wisconsin', 'MI': 'Michigan', 'IN': 'Indiana', 'NJ': 'New Jersey', 'AZ': 'Arizona', 'GU': 'Guam', 'MS': 'Mississippi', 'PR': 'Puerto Rico', 'NC': 'North Carolina', 'TX': 'Texas', 'SD': 'South Dakota', 'MP': 'Northern Mariana Islands', 'IA': 'Iowa', 'MO': 'Missouri', 'CT': 'Connecticut', 'WV': 'West Virginia', 'SC': 'South Carolina', 'LA': 'Louisiana', 'KS': 'Kansas', 'NY': 'New York', 'NE': 'Nebraska', 'OK': 'Oklahoma', 'FL': 'Florida', 'CA': 'California', 'CO': 'Colorado', 'PA': 'Pennsylvania', 'DE': 'Delaware', 'NM': 'New Mexico', 'RI': 'Rhode Island', 'MN': 'Minnesota', 'VI': 'Virgin Islands', 'NH': 'New Hampshire', 'MA': 'Massachusetts', 'GA': 'Georgia', 'ND': 'North Dakota', 'VA': 'Virginia'}
```


```python
def get_list_of_university_towns():
    '''Returns a DataFrame of towns and the states they are in from the 
    university_towns.txt list. The format of the DataFrame should be:
    DataFrame( [ ["Michigan", "Ann Arbor"], ["Michigan", "Yipsilanti"] ], 
    columns=["State", "RegionName"]  )
    
    The following cleaning needs to be done:

    1. For "State", removing characters from "[" to the end.
    2. For "RegionName", when applicable, removing every character from " (" to the end.
    3. Depending on how you read the data, you may need to remove newline character '\n'. '''
    
    data=[]
    f=open('university_towns.txt')
    state = ''
    for line in f:
        line = line.strip()
        if len(line) < 1:
            continue
        if '[edit]' in line:
            state = line[:line.index('[')]
        else:
            region = line
            if  ' (' in region:
                region = region[:region.index(' (')]
            data.append([state,region])
    f.close()
    df_town = pd.DataFrame(data,columns=['State','RegionName'])
    return df_town

#print(get_list_of_university_towns())
```


```python
def get_recession_start():
    '''Returns the year and quarter of the recession start time as a 
    string value in a format such as 2005q3'''
    
    df_gdp = pd.read_excel('gdplev.xls',skiprows=7, parse_cols="E,F",names=["Quarter","GDP"])
    df_gdp = df_gdp[df_gdp['Quarter']>='2000q1']
    for i in range(2,len(df_gdp)):
        if (df_gdp.iloc[i-2]['GDP'] > df_gdp.iloc[i-1]['GDP']) and (df_gdp.iloc[i-1]['GDP'] > df_gdp.iloc[i]['GDP']):
            return df_gdp.iloc[i-2]['Quarter']

#get_recession_start()
```


```python
def get_recession_end():
    '''Returns the year and quarter of the recession end time as a 
    string value in a format such as 2005q3'''
    
    df_gdp = pd.read_excel('gdplev.xls',skiprows=7, parse_cols="E,F",names=["Quarter","GDP"])
    start = get_recession_start()
    df_gdp = df_gdp[df_gdp['Quarter']> start]
    
    # 最后一次遇到的
#     for i in range(len(df_gdp)-1,1,-1):
#         if df_gdp.iloc[i]['GDP'] > df_gdp.iloc[i-1]['GDP'] and df_gdp.iloc[i-1]['GDP'] > df_gdp.iloc[i-2]['GDP']:
#             return df_gdp.iloc[i]['Quarter']

    # 必须是get_recession_start之后第一次遇到的
    for i in range(2,len(df_gdp)):
        if (df_gdp.iloc[i-2]['GDP'] < df_gdp.iloc[i-1]['GDP']) and (df_gdp.iloc[i-1]['GDP'] < df_gdp.iloc[i]['GDP']):
            return df_gdp.iloc[i]['Quarter']
        
get_recession_end()
```




    '2009q4'




```python
def get_recession_bottom():
    '''Returns the year and quarter of the recession bottom time as a 
    string value in a format such as 2005q3'''
    
    df_gdp = pd.read_excel('gdplev.xls',skiprows=7, parse_cols="E,F",names=["Quarter","GDP"])
    df_gdp = df_gdp[df_gdp['Quarter']>='2000q1']
    start = get_recession_start()
    end = get_recession_end()
    bottom = df_gdp[(df_gdp['Quarter']>start) & (df_gdp['Quarter']<end)]['GDP'].idxmin()
    return df_gdp.loc[bottom]['Quarter']

#get_recession_bottom()
```


```python
# very low performance
# row-wise computation

# df_houses = pd.read_csv('City_Zhvi_AllHomes.csv')
# df_houses.replace({'State':states},inplace=True)

# years = range(2000,2017)
# quarters = range(1,5)

# def convert_to_quarters(row):
#     s = pd.Series()
#     s['State']=row['State']
#     s['RegionName']=row['RegionName']
#     for y in years:
#         for q in quarters:
#             q_name = '%dq%d'%(y,q)
#             if q_name > '2016q3':
#                 continue
#             st = 3*(q-1)+1
#             prices = []
#             for m in range(st,st+3):
#                 y_m = '%d-%02d'%(y,m)
#                 if y_m in row:
#                     prices.append(row['%d-%02d'%(y,m)])
#             s[q_name]=np.mean(prices)
#     return s

# df_q=df_houses.apply(convert_to_quarters,axis=1)
# df_q.set_index(["State","RegionName"],inplace=True)
# print(df_q)



# very high performance
# column-wise computation
def convert_housing_data_to_quarters():
    '''Converts the housing data to quarters and returns it as mean 
    values in a dataframe. This dataframe should be a dataframe with
    columns for 2000q1 through 2016q3, and should have a multi-index
    in the shape of ["State","RegionName"].
    
    Note: Quarters are defined in the assignment description, they are
    not arbitrary three month periods.
    
    The resulting dataframe should have 67 columns, and 10,730 rows.
    '''
    
    df_houses = pd.read_csv('City_Zhvi_AllHomes.csv')
    df_houses.replace({'State':states},inplace=True)

    years = range(2000,2017)
    quarters = range(1,5)

    df_houses.set_index(["State","RegionName"],inplace=True)
    new_columns = []

    for y in years:
        for q in quarters:
            q_name = '%dq%d'%(y,q)
            if q_name > '2016q3':
                continue
            st = 3*(q-1)+1
            months=[]
            for m in range(st,st+3):
                y_m = '%d-%02d'%(y,m)
                if y_m in df_houses:
                    months.append(y_m)
            df_houses[q_name]=df_houses[months].mean(axis=1)
            new_columns.append(q_name)
    df_houses=df_houses[new_columns]

    return df_houses

#convert_housing_data_to_quarters()
```


```python
def prev_quarter(cur):
    year,q=cur.split('q')
    if q == '1':
        y = int(year)-1
        return '%dq4'%y
    else:
        return '%sq%d'%(year,int(q)-1)

def run_ttest():
    '''First creates new data showing the decline or growth of housing prices
    between the recession start and the recession bottom. Then runs a ttest
    comparing the university town values to the non-university towns values, 
    return whether the alternative hypothesis (that the two groups are the same)
    is true or not as well as the p-value of the confidence. 
    
    Return the tuple (different, p, better) where different=True if the t-test is
    True at a p<0.01 (we reject the null hypothesis), or different=False if 
    otherwise (we cannot reject the null hypothesis). The variable p should
    be equal to the exact p value returned from scipy.stats.ttest_ind(). The
    value for better should be either "university town" or "non-university town"
    depending on which has a lower mean price ratio (which is equivilent to a
    reduced market loss).'''
    
    start = get_recession_start()
    prev = prev_quarter(start)
    bottom = get_recession_bottom()

    uni_towns = get_list_of_university_towns()
    uni_towns = set(uni_towns['RegionName'])

    df_houses = convert_housing_data_to_quarters()
    df_houses['price_ratio'] = df_houses[prev] / df_houses[bottom]
    df_houses['is_uni_town'] = df_houses.apply(lambda x : 1 if x.name[1] in uni_towns else 0, axis = 1)

    uni_ratio = df_houses[df_houses['is_uni_town']==1]['price_ratio'].dropna()
    non_uni_ratio = df_houses[df_houses['is_uni_town']==0]['price_ratio'].dropna()

    p = ttest_ind(uni_ratio, non_uni_ratio)[1]
    different = True if p < 0.01 else False
    better = 'university town' if uni_ratio.mean() < non_uni_ratio.mean() else 'non-university town'

    return (different, p, better)

#run_ttest()
```


```python

```
