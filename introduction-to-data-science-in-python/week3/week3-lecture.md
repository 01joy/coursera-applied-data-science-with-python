
---

_You are currently looking at **version 1.0** of this notebook. To download notebooks and datafiles, as well as get help on Jupyter notebooks in the Coursera platform, visit the [Jupyter Notebook FAQ](https://www.coursera.org/learn/python-data-analysis/resources/0dhYG) course resource._

---

# Merging Dataframes



```python
import pandas as pd

df = pd.DataFrame([{'Name': 'Chris', 'Item Purchased': 'Sponge', 'Cost': 22.50},
                   {'Name': 'Kevyn', 'Item Purchased': 'Kitty Litter', 'Cost': 2.50},
                   {'Name': 'Filip', 'Item Purchased': 'Spoon', 'Cost': 5.00}],
                  index=['Store 1', 'Store 1', 'Store 2'])
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Cost</th>
      <th>Item Purchased</th>
      <th>Name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Store 1</th>
      <td>22.5</td>
      <td>Sponge</td>
      <td>Chris</td>
    </tr>
    <tr>
      <th>Store 1</th>
      <td>2.5</td>
      <td>Kitty Litter</td>
      <td>Kevyn</td>
    </tr>
    <tr>
      <th>Store 2</th>
      <td>5.0</td>
      <td>Spoon</td>
      <td>Filip</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['Date'] = ['December 1', 'January 1', 'mid-May']
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Cost</th>
      <th>Item Purchased</th>
      <th>Name</th>
      <th>Date</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Store 1</th>
      <td>22.5</td>
      <td>Sponge</td>
      <td>Chris</td>
      <td>December 1</td>
    </tr>
    <tr>
      <th>Store 1</th>
      <td>2.5</td>
      <td>Kitty Litter</td>
      <td>Kevyn</td>
      <td>January 1</td>
    </tr>
    <tr>
      <th>Store 2</th>
      <td>5.0</td>
      <td>Spoon</td>
      <td>Filip</td>
      <td>mid-May</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['Delivered'] = True
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Cost</th>
      <th>Item Purchased</th>
      <th>Name</th>
      <th>Date</th>
      <th>Delivered</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Store 1</th>
      <td>22.5</td>
      <td>Sponge</td>
      <td>Chris</td>
      <td>December 1</td>
      <td>True</td>
    </tr>
    <tr>
      <th>Store 1</th>
      <td>2.5</td>
      <td>Kitty Litter</td>
      <td>Kevyn</td>
      <td>January 1</td>
      <td>True</td>
    </tr>
    <tr>
      <th>Store 2</th>
      <td>5.0</td>
      <td>Spoon</td>
      <td>Filip</td>
      <td>mid-May</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['Feedback'] = ['Positive', None, 'Negative']
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Cost</th>
      <th>Item Purchased</th>
      <th>Name</th>
      <th>Date</th>
      <th>Delivered</th>
      <th>Feedback</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Store 1</th>
      <td>22.5</td>
      <td>Sponge</td>
      <td>Chris</td>
      <td>December 1</td>
      <td>True</td>
      <td>Positive</td>
    </tr>
    <tr>
      <th>Store 1</th>
      <td>2.5</td>
      <td>Kitty Litter</td>
      <td>Kevyn</td>
      <td>January 1</td>
      <td>True</td>
      <td>None</td>
    </tr>
    <tr>
      <th>Store 2</th>
      <td>5.0</td>
      <td>Spoon</td>
      <td>Filip</td>
      <td>mid-May</td>
      <td>True</td>
      <td>Negative</td>
    </tr>
  </tbody>
</table>
</div>




```python
adf = df.reset_index()
adf['Date'] = pd.Series({0: 'December 1', 2: 'mid-May'})
adf
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>Cost</th>
      <th>Item Purchased</th>
      <th>Name</th>
      <th>Date</th>
      <th>Delivered</th>
      <th>Feedback</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Store 1</td>
      <td>22.5</td>
      <td>Sponge</td>
      <td>Chris</td>
      <td>December 1</td>
      <td>True</td>
      <td>Positive</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Store 1</td>
      <td>2.5</td>
      <td>Kitty Litter</td>
      <td>Kevyn</td>
      <td>NaN</td>
      <td>True</td>
      <td>None</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Store 2</td>
      <td>5.0</td>
      <td>Spoon</td>
      <td>Filip</td>
      <td>mid-May</td>
      <td>True</td>
      <td>Negative</td>
    </tr>
  </tbody>
</table>
</div>




```python
staff_df = pd.DataFrame([{'Name': 'Kelly', 'Role': 'Director of HR'},
                         {'Name': 'Sally', 'Role': 'Course liasion'},
                         {'Name': 'James', 'Role': 'Grader'}])
staff_df = staff_df.set_index('Name')
student_df = pd.DataFrame([{'Name': 'James', 'School': 'Business'},
                           {'Name': 'Mike', 'School': 'Law'},
                           {'Name': 'Sally', 'School': 'Engineering'}])
student_df = student_df.set_index('Name')
print(staff_df.head())
print()
print(student_df.head())
```

                     Role
    Name                 
    Kelly  Director of HR
    Sally  Course liasion
    James          Grader
    
                School
    Name              
    James     Business
    Mike           Law
    Sally  Engineering



```python
pd.merge(staff_df, student_df, how='outer', left_index=True, right_index=True)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Role</th>
      <th>School</th>
    </tr>
    <tr>
      <th>Name</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>James</th>
      <td>Grader</td>
      <td>Business</td>
    </tr>
    <tr>
      <th>Kelly</th>
      <td>Director of HR</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Mike</th>
      <td>NaN</td>
      <td>Law</td>
    </tr>
    <tr>
      <th>Sally</th>
      <td>Course liasion</td>
      <td>Engineering</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(staff_df, student_df, how='inner', left_index=True, right_index=True)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Role</th>
      <th>School</th>
    </tr>
    <tr>
      <th>Name</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>James</th>
      <td>Grader</td>
      <td>Business</td>
    </tr>
    <tr>
      <th>Sally</th>
      <td>Course liasion</td>
      <td>Engineering</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(staff_df, student_df, how='left', left_index=True, right_index=True)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Role</th>
      <th>School</th>
    </tr>
    <tr>
      <th>Name</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Kelly</th>
      <td>Director of HR</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Sally</th>
      <td>Course liasion</td>
      <td>Engineering</td>
    </tr>
    <tr>
      <th>James</th>
      <td>Grader</td>
      <td>Business</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.merge(staff_df, student_df, how='right', left_index=True, right_index=True)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Role</th>
      <th>School</th>
    </tr>
    <tr>
      <th>Name</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>James</th>
      <td>Grader</td>
      <td>Business</td>
    </tr>
    <tr>
      <th>Mike</th>
      <td>NaN</td>
      <td>Law</td>
    </tr>
    <tr>
      <th>Sally</th>
      <td>Course liasion</td>
      <td>Engineering</td>
    </tr>
  </tbody>
</table>
</div>




```python
staff_df = staff_df.reset_index()
student_df = student_df.reset_index()
pd.merge(staff_df, student_df, how='left', left_on='Name', right_on='Name')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Role</th>
      <th>School</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Kelly</td>
      <td>Director of HR</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Sally</td>
      <td>Course liasion</td>
      <td>Engineering</td>
    </tr>
    <tr>
      <th>2</th>
      <td>James</td>
      <td>Grader</td>
      <td>Business</td>
    </tr>
  </tbody>
</table>
</div>




```python
staff_df = pd.DataFrame([{'Name': 'Kelly', 'Role': 'Director of HR', 'Location': 'State Street'},
                         {'Name': 'Sally', 'Role': 'Course liasion', 'Location': 'Washington Avenue'},
                         {'Name': 'James', 'Role': 'Grader', 'Location': 'Washington Avenue'}])
student_df = pd.DataFrame([{'Name': 'James', 'School': 'Business', 'Location': '1024 Billiard Avenue'},
                           {'Name': 'Mike', 'School': 'Law', 'Location': 'Fraternity House #22'},
                           {'Name': 'Sally', 'School': 'Engineering', 'Location': '512 Wilson Crescent'}])
pd.merge(staff_df, student_df, how='left', left_on='Name', right_on='Name')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Location_x</th>
      <th>Name</th>
      <th>Role</th>
      <th>Location_y</th>
      <th>School</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>State Street</td>
      <td>Kelly</td>
      <td>Director of HR</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Washington Avenue</td>
      <td>Sally</td>
      <td>Course liasion</td>
      <td>512 Wilson Crescent</td>
      <td>Engineering</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Washington Avenue</td>
      <td>James</td>
      <td>Grader</td>
      <td>1024 Billiard Avenue</td>
      <td>Business</td>
    </tr>
  </tbody>
</table>
</div>




```python
staff_df = pd.DataFrame([{'First Name': 'Kelly', 'Last Name': 'Desjardins', 'Role': 'Director of HR'},
                         {'First Name': 'Sally', 'Last Name': 'Brooks', 'Role': 'Course liasion'},
                         {'First Name': 'James', 'Last Name': 'Wilde', 'Role': 'Grader'}])
student_df = pd.DataFrame([{'First Name': 'James', 'Last Name': 'Hammond', 'School': 'Business'},
                           {'First Name': 'Mike', 'Last Name': 'Smith', 'School': 'Law'},
                           {'First Name': 'Sally', 'Last Name': 'Brooks', 'School': 'Engineering'}])
staff_df
student_df
pd.merge(staff_df, student_df, how='inner', left_on=['First Name','Last Name'], right_on=['First Name','Last Name'])
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>First Name</th>
      <th>Last Name</th>
      <th>Role</th>
      <th>School</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sally</td>
      <td>Brooks</td>
      <td>Course liasion</td>
      <td>Engineering</td>
    </tr>
  </tbody>
</table>
</div>



# Idiomatic Pandas: Making Code Pandorable


```python
import pandas as pd
df = pd.read_csv('census.csv')
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SUMLEV</th>
      <th>REGION</th>
      <th>DIVISION</th>
      <th>STATE</th>
      <th>COUNTY</th>
      <th>STNAME</th>
      <th>CTYNAME</th>
      <th>CENSUS2010POP</th>
      <th>ESTIMATESBASE2010</th>
      <th>POPESTIMATE2010</th>
      <th>...</th>
      <th>RDOMESTICMIG2011</th>
      <th>RDOMESTICMIG2012</th>
      <th>RDOMESTICMIG2013</th>
      <th>RDOMESTICMIG2014</th>
      <th>RDOMESTICMIG2015</th>
      <th>RNETMIG2011</th>
      <th>RNETMIG2012</th>
      <th>RNETMIG2013</th>
      <th>RNETMIG2014</th>
      <th>RNETMIG2015</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>40</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>0</td>
      <td>Alabama</td>
      <td>Alabama</td>
      <td>4779736</td>
      <td>4780127</td>
      <td>4785161</td>
      <td>...</td>
      <td>0.002295</td>
      <td>-0.193196</td>
      <td>0.381066</td>
      <td>0.582002</td>
      <td>-0.467369</td>
      <td>1.030015</td>
      <td>0.826644</td>
      <td>1.383282</td>
      <td>1.724718</td>
      <td>0.712594</td>
    </tr>
    <tr>
      <th>1</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>1</td>
      <td>Alabama</td>
      <td>Autauga County</td>
      <td>54571</td>
      <td>54571</td>
      <td>54660</td>
      <td>...</td>
      <td>7.242091</td>
      <td>-2.915927</td>
      <td>-3.012349</td>
      <td>2.265971</td>
      <td>-2.530799</td>
      <td>7.606016</td>
      <td>-2.626146</td>
      <td>-2.722002</td>
      <td>2.592270</td>
      <td>-2.187333</td>
    </tr>
    <tr>
      <th>2</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>3</td>
      <td>Alabama</td>
      <td>Baldwin County</td>
      <td>182265</td>
      <td>182265</td>
      <td>183193</td>
      <td>...</td>
      <td>14.832960</td>
      <td>17.647293</td>
      <td>21.845705</td>
      <td>19.243287</td>
      <td>17.197872</td>
      <td>15.844176</td>
      <td>18.559627</td>
      <td>22.727626</td>
      <td>20.317142</td>
      <td>18.293499</td>
    </tr>
    <tr>
      <th>3</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>5</td>
      <td>Alabama</td>
      <td>Barbour County</td>
      <td>27457</td>
      <td>27457</td>
      <td>27341</td>
      <td>...</td>
      <td>-4.728132</td>
      <td>-2.500690</td>
      <td>-7.056824</td>
      <td>-3.904217</td>
      <td>-10.543299</td>
      <td>-4.874741</td>
      <td>-2.758113</td>
      <td>-7.167664</td>
      <td>-3.978583</td>
      <td>-10.543299</td>
    </tr>
    <tr>
      <th>4</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>7</td>
      <td>Alabama</td>
      <td>Bibb County</td>
      <td>22915</td>
      <td>22919</td>
      <td>22861</td>
      <td>...</td>
      <td>-5.527043</td>
      <td>-5.068871</td>
      <td>-6.201001</td>
      <td>-0.177537</td>
      <td>0.177258</td>
      <td>-5.088389</td>
      <td>-4.363636</td>
      <td>-5.403729</td>
      <td>0.754533</td>
      <td>1.107861</td>
    </tr>
    <tr>
      <th>5</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>9</td>
      <td>Alabama</td>
      <td>Blount County</td>
      <td>57322</td>
      <td>57322</td>
      <td>57373</td>
      <td>...</td>
      <td>1.807375</td>
      <td>-1.177622</td>
      <td>-1.748766</td>
      <td>-2.062535</td>
      <td>-1.369970</td>
      <td>1.859511</td>
      <td>-0.848580</td>
      <td>-1.402476</td>
      <td>-1.577232</td>
      <td>-0.884411</td>
    </tr>
    <tr>
      <th>6</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>11</td>
      <td>Alabama</td>
      <td>Bullock County</td>
      <td>10914</td>
      <td>10915</td>
      <td>10887</td>
      <td>...</td>
      <td>-30.953709</td>
      <td>-5.180127</td>
      <td>-1.130263</td>
      <td>14.354290</td>
      <td>-16.167247</td>
      <td>-29.001673</td>
      <td>-2.825524</td>
      <td>1.507017</td>
      <td>17.243790</td>
      <td>-13.193961</td>
    </tr>
    <tr>
      <th>7</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>13</td>
      <td>Alabama</td>
      <td>Butler County</td>
      <td>20947</td>
      <td>20946</td>
      <td>20944</td>
      <td>...</td>
      <td>-14.032727</td>
      <td>-11.684234</td>
      <td>-5.655413</td>
      <td>1.085428</td>
      <td>-6.529805</td>
      <td>-13.936612</td>
      <td>-11.586865</td>
      <td>-5.557058</td>
      <td>1.184103</td>
      <td>-6.430868</td>
    </tr>
    <tr>
      <th>8</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>15</td>
      <td>Alabama</td>
      <td>Calhoun County</td>
      <td>118572</td>
      <td>118586</td>
      <td>118437</td>
      <td>...</td>
      <td>-6.155670</td>
      <td>-4.611706</td>
      <td>-5.524649</td>
      <td>-4.463211</td>
      <td>-3.376322</td>
      <td>-5.791579</td>
      <td>-4.092677</td>
      <td>-5.062836</td>
      <td>-3.912834</td>
      <td>-2.806406</td>
    </tr>
    <tr>
      <th>9</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>17</td>
      <td>Alabama</td>
      <td>Chambers County</td>
      <td>34215</td>
      <td>34170</td>
      <td>34098</td>
      <td>...</td>
      <td>-2.731639</td>
      <td>3.849092</td>
      <td>2.872721</td>
      <td>-2.287222</td>
      <td>1.349468</td>
      <td>-1.821092</td>
      <td>4.701181</td>
      <td>3.781439</td>
      <td>-1.290228</td>
      <td>2.346901</td>
    </tr>
    <tr>
      <th>10</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>19</td>
      <td>Alabama</td>
      <td>Cherokee County</td>
      <td>25989</td>
      <td>25986</td>
      <td>25976</td>
      <td>...</td>
      <td>6.339327</td>
      <td>1.113180</td>
      <td>5.488706</td>
      <td>-0.076806</td>
      <td>-3.239866</td>
      <td>6.416167</td>
      <td>1.420264</td>
      <td>5.757384</td>
      <td>0.230419</td>
      <td>-2.931307</td>
    </tr>
    <tr>
      <th>11</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>21</td>
      <td>Alabama</td>
      <td>Chilton County</td>
      <td>43643</td>
      <td>43631</td>
      <td>43665</td>
      <td>...</td>
      <td>-1.372935</td>
      <td>-2.653369</td>
      <td>0.480044</td>
      <td>0.456017</td>
      <td>-2.253483</td>
      <td>-0.823761</td>
      <td>-2.447504</td>
      <td>0.868651</td>
      <td>0.957636</td>
      <td>-1.752709</td>
    </tr>
    <tr>
      <th>12</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>23</td>
      <td>Alabama</td>
      <td>Choctaw County</td>
      <td>13859</td>
      <td>13858</td>
      <td>13841</td>
      <td>...</td>
      <td>-15.455274</td>
      <td>-0.737028</td>
      <td>-8.766391</td>
      <td>-1.274984</td>
      <td>-5.291205</td>
      <td>-15.528177</td>
      <td>-0.737028</td>
      <td>-8.766391</td>
      <td>-1.274984</td>
      <td>-5.291205</td>
    </tr>
    <tr>
      <th>13</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>25</td>
      <td>Alabama</td>
      <td>Clarke County</td>
      <td>25833</td>
      <td>25840</td>
      <td>25767</td>
      <td>...</td>
      <td>-6.194363</td>
      <td>-17.667705</td>
      <td>-0.318345</td>
      <td>-8.686428</td>
      <td>-5.613667</td>
      <td>-6.077488</td>
      <td>-17.509958</td>
      <td>-0.159172</td>
      <td>-8.486280</td>
      <td>-5.411736</td>
    </tr>
    <tr>
      <th>14</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>27</td>
      <td>Alabama</td>
      <td>Clay County</td>
      <td>13932</td>
      <td>13932</td>
      <td>13880</td>
      <td>...</td>
      <td>-10.744102</td>
      <td>-13.345130</td>
      <td>4.902871</td>
      <td>5.702648</td>
      <td>3.912450</td>
      <td>-10.816697</td>
      <td>-13.345130</td>
      <td>4.977157</td>
      <td>5.776708</td>
      <td>3.986270</td>
    </tr>
    <tr>
      <th>15</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>29</td>
      <td>Alabama</td>
      <td>Cleburne County</td>
      <td>14972</td>
      <td>14972</td>
      <td>14973</td>
      <td>...</td>
      <td>-3.673524</td>
      <td>-5.151880</td>
      <td>7.345821</td>
      <td>3.654485</td>
      <td>-3.123961</td>
      <td>-3.673524</td>
      <td>-5.151880</td>
      <td>7.345821</td>
      <td>3.654485</td>
      <td>-3.123961</td>
    </tr>
    <tr>
      <th>16</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>31</td>
      <td>Alabama</td>
      <td>Coffee County</td>
      <td>49948</td>
      <td>49948</td>
      <td>50177</td>
      <td>...</td>
      <td>0.377640</td>
      <td>7.675579</td>
      <td>-13.146535</td>
      <td>-3.602859</td>
      <td>2.214774</td>
      <td>2.166460</td>
      <td>11.513368</td>
      <td>-10.438741</td>
      <td>-0.767822</td>
      <td>5.350738</td>
    </tr>
    <tr>
      <th>17</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>33</td>
      <td>Alabama</td>
      <td>Colbert County</td>
      <td>54428</td>
      <td>54428</td>
      <td>54514</td>
      <td>...</td>
      <td>-0.073423</td>
      <td>1.065051</td>
      <td>1.762390</td>
      <td>1.835688</td>
      <td>-0.110260</td>
      <td>0.513964</td>
      <td>1.469035</td>
      <td>2.276420</td>
      <td>2.533249</td>
      <td>0.588052</td>
    </tr>
    <tr>
      <th>18</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>35</td>
      <td>Alabama</td>
      <td>Conecuh County</td>
      <td>13228</td>
      <td>13228</td>
      <td>13208</td>
      <td>...</td>
      <td>-4.861559</td>
      <td>-7.504690</td>
      <td>-6.107224</td>
      <td>-14.645416</td>
      <td>2.684140</td>
      <td>-4.861559</td>
      <td>-7.504690</td>
      <td>-6.107224</td>
      <td>-14.645416</td>
      <td>2.684140</td>
    </tr>
    <tr>
      <th>19</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>37</td>
      <td>Alabama</td>
      <td>Coosa County</td>
      <td>11539</td>
      <td>11758</td>
      <td>11758</td>
      <td>...</td>
      <td>-33.930581</td>
      <td>-10.291443</td>
      <td>-4.313831</td>
      <td>-22.958017</td>
      <td>-5.387581</td>
      <td>-34.017138</td>
      <td>-10.380162</td>
      <td>-4.403703</td>
      <td>-23.049483</td>
      <td>-5.387581</td>
    </tr>
    <tr>
      <th>20</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>39</td>
      <td>Alabama</td>
      <td>Covington County</td>
      <td>37765</td>
      <td>37765</td>
      <td>37796</td>
      <td>...</td>
      <td>6.696899</td>
      <td>-4.612668</td>
      <td>0.740271</td>
      <td>3.697932</td>
      <td>-0.316945</td>
      <td>6.881460</td>
      <td>-4.559952</td>
      <td>0.793147</td>
      <td>3.750759</td>
      <td>-0.264121</td>
    </tr>
    <tr>
      <th>21</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>41</td>
      <td>Alabama</td>
      <td>Crenshaw County</td>
      <td>13906</td>
      <td>13906</td>
      <td>13853</td>
      <td>...</td>
      <td>1.729792</td>
      <td>3.950156</td>
      <td>-1.864936</td>
      <td>3.084648</td>
      <td>3.439504</td>
      <td>2.666763</td>
      <td>5.099293</td>
      <td>-0.502098</td>
      <td>4.734577</td>
      <td>5.087600</td>
    </tr>
    <tr>
      <th>22</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>43</td>
      <td>Alabama</td>
      <td>Cullman County</td>
      <td>80406</td>
      <td>80410</td>
      <td>80473</td>
      <td>...</td>
      <td>-1.404233</td>
      <td>-1.019628</td>
      <td>4.071247</td>
      <td>5.087142</td>
      <td>7.915406</td>
      <td>-1.031427</td>
      <td>-0.634159</td>
      <td>4.542916</td>
      <td>5.593387</td>
      <td>8.417777</td>
    </tr>
    <tr>
      <th>23</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>45</td>
      <td>Alabama</td>
      <td>Dale County</td>
      <td>50251</td>
      <td>50251</td>
      <td>50358</td>
      <td>...</td>
      <td>-10.749798</td>
      <td>-5.277150</td>
      <td>-15.236079</td>
      <td>-11.979785</td>
      <td>-5.107706</td>
      <td>-9.575283</td>
      <td>-0.776637</td>
      <td>-12.640155</td>
      <td>-9.503292</td>
      <td>-1.998668</td>
    </tr>
    <tr>
      <th>24</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>47</td>
      <td>Alabama</td>
      <td>Dallas County</td>
      <td>43820</td>
      <td>43820</td>
      <td>43803</td>
      <td>...</td>
      <td>-15.635599</td>
      <td>-11.308243</td>
      <td>-16.745678</td>
      <td>-9.344789</td>
      <td>-14.687232</td>
      <td>-15.727573</td>
      <td>-11.378047</td>
      <td>-16.792849</td>
      <td>-9.368689</td>
      <td>-14.711389</td>
    </tr>
    <tr>
      <th>25</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>49</td>
      <td>Alabama</td>
      <td>DeKalb County</td>
      <td>71109</td>
      <td>71115</td>
      <td>71142</td>
      <td>...</td>
      <td>0.294677</td>
      <td>-9.302391</td>
      <td>-1.748807</td>
      <td>0.267830</td>
      <td>0.028141</td>
      <td>1.375159</td>
      <td>-8.656001</td>
      <td>-1.029539</td>
      <td>1.198187</td>
      <td>0.956790</td>
    </tr>
    <tr>
      <th>26</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>51</td>
      <td>Alabama</td>
      <td>Elmore County</td>
      <td>79303</td>
      <td>79296</td>
      <td>79465</td>
      <td>...</td>
      <td>3.235576</td>
      <td>0.822717</td>
      <td>1.760531</td>
      <td>-1.507057</td>
      <td>2.067820</td>
      <td>3.674511</td>
      <td>1.558176</td>
      <td>2.306047</td>
      <td>-0.951175</td>
      <td>2.757093</td>
    </tr>
    <tr>
      <th>27</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>53</td>
      <td>Alabama</td>
      <td>Escambia County</td>
      <td>38319</td>
      <td>38319</td>
      <td>38309</td>
      <td>...</td>
      <td>-3.449988</td>
      <td>-3.855889</td>
      <td>-4.822706</td>
      <td>-1.189831</td>
      <td>1.190902</td>
      <td>-3.397716</td>
      <td>-3.803428</td>
      <td>-4.769999</td>
      <td>-1.136950</td>
      <td>1.243830</td>
    </tr>
    <tr>
      <th>28</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>55</td>
      <td>Alabama</td>
      <td>Etowah County</td>
      <td>104430</td>
      <td>104427</td>
      <td>104442</td>
      <td>...</td>
      <td>-1.015919</td>
      <td>2.062637</td>
      <td>-1.931884</td>
      <td>-1.726932</td>
      <td>-2.082234</td>
      <td>-0.632554</td>
      <td>2.446383</td>
      <td>-1.518596</td>
      <td>-1.234901</td>
      <td>-1.588308</td>
    </tr>
    <tr>
      <th>29</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>57</td>
      <td>Alabama</td>
      <td>Fayette County</td>
      <td>17241</td>
      <td>17241</td>
      <td>17231</td>
      <td>...</td>
      <td>-5.015601</td>
      <td>-0.646640</td>
      <td>-3.725937</td>
      <td>0.296745</td>
      <td>-2.797536</td>
      <td>-5.132243</td>
      <td>-0.705426</td>
      <td>-3.785079</td>
      <td>0.237396</td>
      <td>-2.857058</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>3163</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>131</td>
      <td>Wisconsin</td>
      <td>Washington County</td>
      <td>131887</td>
      <td>131885</td>
      <td>131967</td>
      <td>...</td>
      <td>-0.794876</td>
      <td>0.785279</td>
      <td>-2.215465</td>
      <td>1.601149</td>
      <td>-0.434498</td>
      <td>-0.431504</td>
      <td>1.162817</td>
      <td>-1.763330</td>
      <td>2.104796</td>
      <td>0.059931</td>
    </tr>
    <tr>
      <th>3164</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>133</td>
      <td>Wisconsin</td>
      <td>Waukesha County</td>
      <td>389891</td>
      <td>389938</td>
      <td>390076</td>
      <td>...</td>
      <td>-0.765799</td>
      <td>2.128860</td>
      <td>0.038132</td>
      <td>0.760109</td>
      <td>-0.719858</td>
      <td>0.102448</td>
      <td>3.180527</td>
      <td>1.189727</td>
      <td>2.077633</td>
      <td>0.593567</td>
    </tr>
    <tr>
      <th>3165</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>135</td>
      <td>Wisconsin</td>
      <td>Waupaca County</td>
      <td>52410</td>
      <td>52410</td>
      <td>52422</td>
      <td>...</td>
      <td>3.111756</td>
      <td>-2.241873</td>
      <td>6.292687</td>
      <td>-0.441031</td>
      <td>-0.480617</td>
      <td>3.359933</td>
      <td>-2.011937</td>
      <td>6.561277</td>
      <td>-0.134227</td>
      <td>-0.173022</td>
    </tr>
    <tr>
      <th>3166</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>137</td>
      <td>Wisconsin</td>
      <td>Waushara County</td>
      <td>24496</td>
      <td>24496</td>
      <td>24506</td>
      <td>...</td>
      <td>4.930022</td>
      <td>-2.404973</td>
      <td>-4.097017</td>
      <td>-4.906711</td>
      <td>-4.397793</td>
      <td>5.174486</td>
      <td>-2.160399</td>
      <td>-3.810226</td>
      <td>-4.535615</td>
      <td>-4.024395</td>
    </tr>
    <tr>
      <th>3167</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>139</td>
      <td>Wisconsin</td>
      <td>Winnebago County</td>
      <td>166994</td>
      <td>166994</td>
      <td>167059</td>
      <td>...</td>
      <td>0.316712</td>
      <td>2.889873</td>
      <td>0.833819</td>
      <td>-2.406192</td>
      <td>-4.557985</td>
      <td>0.842573</td>
      <td>3.502335</td>
      <td>1.531624</td>
      <td>-1.545153</td>
      <td>-3.685304</td>
    </tr>
    <tr>
      <th>3168</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>141</td>
      <td>Wisconsin</td>
      <td>Wood County</td>
      <td>74749</td>
      <td>74749</td>
      <td>74807</td>
      <td>...</td>
      <td>-4.081523</td>
      <td>-5.019090</td>
      <td>-6.901200</td>
      <td>-5.596471</td>
      <td>-3.958322</td>
      <td>-3.733590</td>
      <td>-4.562809</td>
      <td>-6.442917</td>
      <td>-5.040889</td>
      <td>-3.414223</td>
    </tr>
    <tr>
      <th>3169</th>
      <td>40</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>0</td>
      <td>Wyoming</td>
      <td>Wyoming</td>
      <td>563626</td>
      <td>563767</td>
      <td>564516</td>
      <td>...</td>
      <td>-0.381530</td>
      <td>9.636214</td>
      <td>4.487115</td>
      <td>-4.788275</td>
      <td>-3.221091</td>
      <td>0.289680</td>
      <td>10.694870</td>
      <td>5.440390</td>
      <td>-3.727831</td>
      <td>-2.091573</td>
    </tr>
    <tr>
      <th>3170</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>1</td>
      <td>Wyoming</td>
      <td>Albany County</td>
      <td>36299</td>
      <td>36299</td>
      <td>36428</td>
      <td>...</td>
      <td>3.708956</td>
      <td>2.637812</td>
      <td>-3.544634</td>
      <td>-3.334877</td>
      <td>-9.911169</td>
      <td>6.736119</td>
      <td>6.433032</td>
      <td>0.719587</td>
      <td>1.429233</td>
      <td>-5.166460</td>
    </tr>
    <tr>
      <th>3171</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>3</td>
      <td>Wyoming</td>
      <td>Big Horn County</td>
      <td>11668</td>
      <td>11668</td>
      <td>11672</td>
      <td>...</td>
      <td>4.868258</td>
      <td>2.804930</td>
      <td>16.815908</td>
      <td>-8.026420</td>
      <td>5.095861</td>
      <td>4.868258</td>
      <td>3.144921</td>
      <td>17.236306</td>
      <td>-7.608378</td>
      <td>5.513554</td>
    </tr>
    <tr>
      <th>3172</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>5</td>
      <td>Wyoming</td>
      <td>Campbell County</td>
      <td>46133</td>
      <td>46133</td>
      <td>46244</td>
      <td>...</td>
      <td>-2.843479</td>
      <td>15.601020</td>
      <td>-5.895711</td>
      <td>-8.550911</td>
      <td>10.916963</td>
      <td>-2.649606</td>
      <td>15.558684</td>
      <td>-5.916543</td>
      <td>-8.509402</td>
      <td>10.978525</td>
    </tr>
    <tr>
      <th>3173</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>7</td>
      <td>Wyoming</td>
      <td>Carbon County</td>
      <td>15885</td>
      <td>15885</td>
      <td>15837</td>
      <td>...</td>
      <td>-7.581980</td>
      <td>-13.081441</td>
      <td>3.178134</td>
      <td>-2.970641</td>
      <td>-23.300971</td>
      <td>-7.392431</td>
      <td>-12.636926</td>
      <td>3.623073</td>
      <td>-2.338590</td>
      <td>-22.600668</td>
    </tr>
    <tr>
      <th>3174</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>9</td>
      <td>Wyoming</td>
      <td>Converse County</td>
      <td>13833</td>
      <td>13833</td>
      <td>13826</td>
      <td>...</td>
      <td>-12.847499</td>
      <td>15.493820</td>
      <td>19.035533</td>
      <td>-20.550587</td>
      <td>-0.070403</td>
      <td>-12.774915</td>
      <td>16.502720</td>
      <td>20.093063</td>
      <td>-19.358233</td>
      <td>1.126443</td>
    </tr>
    <tr>
      <th>3175</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>11</td>
      <td>Wyoming</td>
      <td>Crook County</td>
      <td>7083</td>
      <td>7083</td>
      <td>7114</td>
      <td>...</td>
      <td>-1.544618</td>
      <td>-4.202564</td>
      <td>1.397819</td>
      <td>6.378258</td>
      <td>18.629317</td>
      <td>-0.982939</td>
      <td>-3.642222</td>
      <td>2.096729</td>
      <td>7.071547</td>
      <td>19.309219</td>
    </tr>
    <tr>
      <th>3176</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>13</td>
      <td>Wyoming</td>
      <td>Fremont County</td>
      <td>40123</td>
      <td>40123</td>
      <td>40222</td>
      <td>...</td>
      <td>2.747083</td>
      <td>7.782673</td>
      <td>-4.990688</td>
      <td>-12.331633</td>
      <td>-13.673610</td>
      <td>3.093562</td>
      <td>8.027411</td>
      <td>-4.747240</td>
      <td>-12.013555</td>
      <td>-13.352750</td>
    </tr>
    <tr>
      <th>3177</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>15</td>
      <td>Wyoming</td>
      <td>Goshen County</td>
      <td>13249</td>
      <td>13247</td>
      <td>13408</td>
      <td>...</td>
      <td>14.293649</td>
      <td>3.961413</td>
      <td>-8.079028</td>
      <td>-7.017803</td>
      <td>-11.899450</td>
      <td>14.886132</td>
      <td>4.841727</td>
      <td>-6.903896</td>
      <td>-5.761986</td>
      <td>-10.635133</td>
    </tr>
    <tr>
      <th>3178</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>17</td>
      <td>Wyoming</td>
      <td>Hot Springs County</td>
      <td>4812</td>
      <td>4812</td>
      <td>4813</td>
      <td>...</td>
      <td>3.322604</td>
      <td>6.208609</td>
      <td>3.095336</td>
      <td>-6.017222</td>
      <td>-5.454164</td>
      <td>5.191569</td>
      <td>6.001656</td>
      <td>2.888981</td>
      <td>-6.224712</td>
      <td>-5.663940</td>
    </tr>
    <tr>
      <th>3179</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>19</td>
      <td>Wyoming</td>
      <td>Johnson County</td>
      <td>8569</td>
      <td>8569</td>
      <td>8581</td>
      <td>...</td>
      <td>4.995063</td>
      <td>-4.058912</td>
      <td>-0.812583</td>
      <td>-10.715742</td>
      <td>0.933652</td>
      <td>5.227392</td>
      <td>-4.058912</td>
      <td>-0.812583</td>
      <td>-10.715742</td>
      <td>0.933652</td>
    </tr>
    <tr>
      <th>3180</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>21</td>
      <td>Wyoming</td>
      <td>Laramie County</td>
      <td>91738</td>
      <td>91881</td>
      <td>92271</td>
      <td>...</td>
      <td>-1.200428</td>
      <td>15.547274</td>
      <td>4.787847</td>
      <td>-1.226133</td>
      <td>0.278940</td>
      <td>-0.973320</td>
      <td>17.914554</td>
      <td>6.003143</td>
      <td>-0.207819</td>
      <td>1.673640</td>
    </tr>
    <tr>
      <th>3181</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>23</td>
      <td>Wyoming</td>
      <td>Lincoln County</td>
      <td>18106</td>
      <td>18106</td>
      <td>18091</td>
      <td>...</td>
      <td>-9.802564</td>
      <td>-11.566801</td>
      <td>13.564556</td>
      <td>6.125989</td>
      <td>1.555544</td>
      <td>-9.691801</td>
      <td>-11.566801</td>
      <td>13.619696</td>
      <td>6.234414</td>
      <td>1.662823</td>
    </tr>
    <tr>
      <th>3182</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>25</td>
      <td>Wyoming</td>
      <td>Natrona County</td>
      <td>75450</td>
      <td>75450</td>
      <td>75472</td>
      <td>...</td>
      <td>7.189319</td>
      <td>23.066162</td>
      <td>24.322042</td>
      <td>-0.958472</td>
      <td>-0.061057</td>
      <td>7.689674</td>
      <td>23.749508</td>
      <td>25.085233</td>
      <td>-0.110593</td>
      <td>0.793743</td>
    </tr>
    <tr>
      <th>3183</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>27</td>
      <td>Wyoming</td>
      <td>Niobrara County</td>
      <td>2484</td>
      <td>2484</td>
      <td>2492</td>
      <td>...</td>
      <td>-0.401849</td>
      <td>0.806452</td>
      <td>29.066295</td>
      <td>-12.603387</td>
      <td>7.492114</td>
      <td>-0.401849</td>
      <td>0.806452</td>
      <td>29.066295</td>
      <td>-12.603387</td>
      <td>7.492114</td>
    </tr>
    <tr>
      <th>3184</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>29</td>
      <td>Wyoming</td>
      <td>Park County</td>
      <td>28205</td>
      <td>28205</td>
      <td>28259</td>
      <td>...</td>
      <td>4.582951</td>
      <td>8.057765</td>
      <td>7.641997</td>
      <td>-9.252437</td>
      <td>-2.878980</td>
      <td>6.486639</td>
      <td>11.127389</td>
      <td>10.877797</td>
      <td>-5.585731</td>
      <td>0.856839</td>
    </tr>
    <tr>
      <th>3185</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>31</td>
      <td>Wyoming</td>
      <td>Platte County</td>
      <td>8667</td>
      <td>8667</td>
      <td>8678</td>
      <td>...</td>
      <td>4.373094</td>
      <td>5.392073</td>
      <td>2.634593</td>
      <td>6.055759</td>
      <td>4.662270</td>
      <td>4.373094</td>
      <td>4.933173</td>
      <td>2.176403</td>
      <td>5.598720</td>
      <td>4.207414</td>
    </tr>
    <tr>
      <th>3186</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>33</td>
      <td>Wyoming</td>
      <td>Sheridan County</td>
      <td>29116</td>
      <td>29116</td>
      <td>29146</td>
      <td>...</td>
      <td>0.958559</td>
      <td>8.425487</td>
      <td>4.546373</td>
      <td>3.678069</td>
      <td>-3.298406</td>
      <td>2.122524</td>
      <td>9.342778</td>
      <td>5.523001</td>
      <td>4.781489</td>
      <td>-2.198937</td>
    </tr>
    <tr>
      <th>3187</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>35</td>
      <td>Wyoming</td>
      <td>Sublette County</td>
      <td>10247</td>
      <td>10247</td>
      <td>10244</td>
      <td>...</td>
      <td>-23.741784</td>
      <td>15.272374</td>
      <td>-40.870074</td>
      <td>-16.596273</td>
      <td>-22.870900</td>
      <td>-21.092907</td>
      <td>16.828794</td>
      <td>-39.211861</td>
      <td>-14.409938</td>
      <td>-20.664059</td>
    </tr>
    <tr>
      <th>3188</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>37</td>
      <td>Wyoming</td>
      <td>Sweetwater County</td>
      <td>43806</td>
      <td>43806</td>
      <td>43593</td>
      <td>...</td>
      <td>1.072643</td>
      <td>16.243199</td>
      <td>-5.339774</td>
      <td>-14.252889</td>
      <td>-14.248864</td>
      <td>1.255221</td>
      <td>16.243199</td>
      <td>-5.295460</td>
      <td>-14.075283</td>
      <td>-14.070195</td>
    </tr>
    <tr>
      <th>3189</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>39</td>
      <td>Wyoming</td>
      <td>Teton County</td>
      <td>21294</td>
      <td>21294</td>
      <td>21297</td>
      <td>...</td>
      <td>-1.589565</td>
      <td>0.972695</td>
      <td>19.525929</td>
      <td>14.143021</td>
      <td>-0.564849</td>
      <td>0.654527</td>
      <td>2.408578</td>
      <td>21.160658</td>
      <td>16.308671</td>
      <td>1.520747</td>
    </tr>
    <tr>
      <th>3190</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>41</td>
      <td>Wyoming</td>
      <td>Uinta County</td>
      <td>21118</td>
      <td>21118</td>
      <td>21102</td>
      <td>...</td>
      <td>-17.755986</td>
      <td>-4.916350</td>
      <td>-6.902954</td>
      <td>-14.215862</td>
      <td>-12.127022</td>
      <td>-18.136812</td>
      <td>-5.536861</td>
      <td>-7.521840</td>
      <td>-14.740608</td>
      <td>-12.606351</td>
    </tr>
    <tr>
      <th>3191</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>43</td>
      <td>Wyoming</td>
      <td>Washakie County</td>
      <td>8533</td>
      <td>8533</td>
      <td>8545</td>
      <td>...</td>
      <td>-11.637475</td>
      <td>-0.827815</td>
      <td>-2.013502</td>
      <td>-17.781491</td>
      <td>1.682288</td>
      <td>-11.990126</td>
      <td>-1.182592</td>
      <td>-2.250385</td>
      <td>-18.020168</td>
      <td>1.441961</td>
    </tr>
    <tr>
      <th>3192</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>45</td>
      <td>Wyoming</td>
      <td>Weston County</td>
      <td>7208</td>
      <td>7208</td>
      <td>7181</td>
      <td>...</td>
      <td>-11.752361</td>
      <td>-8.040059</td>
      <td>12.372583</td>
      <td>1.533635</td>
      <td>6.935294</td>
      <td>-12.032179</td>
      <td>-8.040059</td>
      <td>12.372583</td>
      <td>1.533635</td>
      <td>6.935294</td>
    </tr>
  </tbody>
</table>
<p>3193 rows × 100 columns</p>
</div>




```python
(df.where(df['SUMLEV']==50)
    .dropna()
    .set_index(['STNAME','CTYNAME'])
    .rename(columns={'ESTIMATESBASE2010': 'Estimates Base 2010'}))
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>SUMLEV</th>
      <th>REGION</th>
      <th>DIVISION</th>
      <th>STATE</th>
      <th>COUNTY</th>
      <th>CENSUS2010POP</th>
      <th>Estimates Base 2010</th>
      <th>POPESTIMATE2010</th>
      <th>POPESTIMATE2011</th>
      <th>POPESTIMATE2012</th>
      <th>...</th>
      <th>RDOMESTICMIG2011</th>
      <th>RDOMESTICMIG2012</th>
      <th>RDOMESTICMIG2013</th>
      <th>RDOMESTICMIG2014</th>
      <th>RDOMESTICMIG2015</th>
      <th>RNETMIG2011</th>
      <th>RNETMIG2012</th>
      <th>RNETMIG2013</th>
      <th>RNETMIG2014</th>
      <th>RNETMIG2015</th>
    </tr>
    <tr>
      <th>STNAME</th>
      <th>CTYNAME</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="30" valign="top">Alabama</th>
      <th>Autauga County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>54571.0</td>
      <td>54571.0</td>
      <td>54660.0</td>
      <td>55253.0</td>
      <td>55175.0</td>
      <td>...</td>
      <td>7.242091</td>
      <td>-2.915927</td>
      <td>-3.012349</td>
      <td>2.265971</td>
      <td>-2.530799</td>
      <td>7.606016</td>
      <td>-2.626146</td>
      <td>-2.722002</td>
      <td>2.592270</td>
      <td>-2.187333</td>
    </tr>
    <tr>
      <th>Baldwin County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>3.0</td>
      <td>182265.0</td>
      <td>182265.0</td>
      <td>183193.0</td>
      <td>186659.0</td>
      <td>190396.0</td>
      <td>...</td>
      <td>14.832960</td>
      <td>17.647293</td>
      <td>21.845705</td>
      <td>19.243287</td>
      <td>17.197872</td>
      <td>15.844176</td>
      <td>18.559627</td>
      <td>22.727626</td>
      <td>20.317142</td>
      <td>18.293499</td>
    </tr>
    <tr>
      <th>Barbour County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>5.0</td>
      <td>27457.0</td>
      <td>27457.0</td>
      <td>27341.0</td>
      <td>27226.0</td>
      <td>27159.0</td>
      <td>...</td>
      <td>-4.728132</td>
      <td>-2.500690</td>
      <td>-7.056824</td>
      <td>-3.904217</td>
      <td>-10.543299</td>
      <td>-4.874741</td>
      <td>-2.758113</td>
      <td>-7.167664</td>
      <td>-3.978583</td>
      <td>-10.543299</td>
    </tr>
    <tr>
      <th>Bibb County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>7.0</td>
      <td>22915.0</td>
      <td>22919.0</td>
      <td>22861.0</td>
      <td>22733.0</td>
      <td>22642.0</td>
      <td>...</td>
      <td>-5.527043</td>
      <td>-5.068871</td>
      <td>-6.201001</td>
      <td>-0.177537</td>
      <td>0.177258</td>
      <td>-5.088389</td>
      <td>-4.363636</td>
      <td>-5.403729</td>
      <td>0.754533</td>
      <td>1.107861</td>
    </tr>
    <tr>
      <th>Blount County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>9.0</td>
      <td>57322.0</td>
      <td>57322.0</td>
      <td>57373.0</td>
      <td>57711.0</td>
      <td>57776.0</td>
      <td>...</td>
      <td>1.807375</td>
      <td>-1.177622</td>
      <td>-1.748766</td>
      <td>-2.062535</td>
      <td>-1.369970</td>
      <td>1.859511</td>
      <td>-0.848580</td>
      <td>-1.402476</td>
      <td>-1.577232</td>
      <td>-0.884411</td>
    </tr>
    <tr>
      <th>Bullock County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>11.0</td>
      <td>10914.0</td>
      <td>10915.0</td>
      <td>10887.0</td>
      <td>10629.0</td>
      <td>10606.0</td>
      <td>...</td>
      <td>-30.953709</td>
      <td>-5.180127</td>
      <td>-1.130263</td>
      <td>14.354290</td>
      <td>-16.167247</td>
      <td>-29.001673</td>
      <td>-2.825524</td>
      <td>1.507017</td>
      <td>17.243790</td>
      <td>-13.193961</td>
    </tr>
    <tr>
      <th>Butler County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>13.0</td>
      <td>20947.0</td>
      <td>20946.0</td>
      <td>20944.0</td>
      <td>20673.0</td>
      <td>20408.0</td>
      <td>...</td>
      <td>-14.032727</td>
      <td>-11.684234</td>
      <td>-5.655413</td>
      <td>1.085428</td>
      <td>-6.529805</td>
      <td>-13.936612</td>
      <td>-11.586865</td>
      <td>-5.557058</td>
      <td>1.184103</td>
      <td>-6.430868</td>
    </tr>
    <tr>
      <th>Calhoun County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>15.0</td>
      <td>118572.0</td>
      <td>118586.0</td>
      <td>118437.0</td>
      <td>117768.0</td>
      <td>117286.0</td>
      <td>...</td>
      <td>-6.155670</td>
      <td>-4.611706</td>
      <td>-5.524649</td>
      <td>-4.463211</td>
      <td>-3.376322</td>
      <td>-5.791579</td>
      <td>-4.092677</td>
      <td>-5.062836</td>
      <td>-3.912834</td>
      <td>-2.806406</td>
    </tr>
    <tr>
      <th>Chambers County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>17.0</td>
      <td>34215.0</td>
      <td>34170.0</td>
      <td>34098.0</td>
      <td>33993.0</td>
      <td>34075.0</td>
      <td>...</td>
      <td>-2.731639</td>
      <td>3.849092</td>
      <td>2.872721</td>
      <td>-2.287222</td>
      <td>1.349468</td>
      <td>-1.821092</td>
      <td>4.701181</td>
      <td>3.781439</td>
      <td>-1.290228</td>
      <td>2.346901</td>
    </tr>
    <tr>
      <th>Cherokee County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>19.0</td>
      <td>25989.0</td>
      <td>25986.0</td>
      <td>25976.0</td>
      <td>26080.0</td>
      <td>26023.0</td>
      <td>...</td>
      <td>6.339327</td>
      <td>1.113180</td>
      <td>5.488706</td>
      <td>-0.076806</td>
      <td>-3.239866</td>
      <td>6.416167</td>
      <td>1.420264</td>
      <td>5.757384</td>
      <td>0.230419</td>
      <td>-2.931307</td>
    </tr>
    <tr>
      <th>Chilton County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>21.0</td>
      <td>43643.0</td>
      <td>43631.0</td>
      <td>43665.0</td>
      <td>43739.0</td>
      <td>43697.0</td>
      <td>...</td>
      <td>-1.372935</td>
      <td>-2.653369</td>
      <td>0.480044</td>
      <td>0.456017</td>
      <td>-2.253483</td>
      <td>-0.823761</td>
      <td>-2.447504</td>
      <td>0.868651</td>
      <td>0.957636</td>
      <td>-1.752709</td>
    </tr>
    <tr>
      <th>Choctaw County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>23.0</td>
      <td>13859.0</td>
      <td>13858.0</td>
      <td>13841.0</td>
      <td>13593.0</td>
      <td>13543.0</td>
      <td>...</td>
      <td>-15.455274</td>
      <td>-0.737028</td>
      <td>-8.766391</td>
      <td>-1.274984</td>
      <td>-5.291205</td>
      <td>-15.528177</td>
      <td>-0.737028</td>
      <td>-8.766391</td>
      <td>-1.274984</td>
      <td>-5.291205</td>
    </tr>
    <tr>
      <th>Clarke County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>25.0</td>
      <td>25833.0</td>
      <td>25840.0</td>
      <td>25767.0</td>
      <td>25570.0</td>
      <td>25144.0</td>
      <td>...</td>
      <td>-6.194363</td>
      <td>-17.667705</td>
      <td>-0.318345</td>
      <td>-8.686428</td>
      <td>-5.613667</td>
      <td>-6.077488</td>
      <td>-17.509958</td>
      <td>-0.159172</td>
      <td>-8.486280</td>
      <td>-5.411736</td>
    </tr>
    <tr>
      <th>Clay County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>27.0</td>
      <td>13932.0</td>
      <td>13932.0</td>
      <td>13880.0</td>
      <td>13670.0</td>
      <td>13456.0</td>
      <td>...</td>
      <td>-10.744102</td>
      <td>-13.345130</td>
      <td>4.902871</td>
      <td>5.702648</td>
      <td>3.912450</td>
      <td>-10.816697</td>
      <td>-13.345130</td>
      <td>4.977157</td>
      <td>5.776708</td>
      <td>3.986270</td>
    </tr>
    <tr>
      <th>Cleburne County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>29.0</td>
      <td>14972.0</td>
      <td>14972.0</td>
      <td>14973.0</td>
      <td>14971.0</td>
      <td>14921.0</td>
      <td>...</td>
      <td>-3.673524</td>
      <td>-5.151880</td>
      <td>7.345821</td>
      <td>3.654485</td>
      <td>-3.123961</td>
      <td>-3.673524</td>
      <td>-5.151880</td>
      <td>7.345821</td>
      <td>3.654485</td>
      <td>-3.123961</td>
    </tr>
    <tr>
      <th>Coffee County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>31.0</td>
      <td>49948.0</td>
      <td>49948.0</td>
      <td>50177.0</td>
      <td>50448.0</td>
      <td>51173.0</td>
      <td>...</td>
      <td>0.377640</td>
      <td>7.675579</td>
      <td>-13.146535</td>
      <td>-3.602859</td>
      <td>2.214774</td>
      <td>2.166460</td>
      <td>11.513368</td>
      <td>-10.438741</td>
      <td>-0.767822</td>
      <td>5.350738</td>
    </tr>
    <tr>
      <th>Colbert County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>33.0</td>
      <td>54428.0</td>
      <td>54428.0</td>
      <td>54514.0</td>
      <td>54443.0</td>
      <td>54472.0</td>
      <td>...</td>
      <td>-0.073423</td>
      <td>1.065051</td>
      <td>1.762390</td>
      <td>1.835688</td>
      <td>-0.110260</td>
      <td>0.513964</td>
      <td>1.469035</td>
      <td>2.276420</td>
      <td>2.533249</td>
      <td>0.588052</td>
    </tr>
    <tr>
      <th>Conecuh County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>35.0</td>
      <td>13228.0</td>
      <td>13228.0</td>
      <td>13208.0</td>
      <td>13121.0</td>
      <td>12996.0</td>
      <td>...</td>
      <td>-4.861559</td>
      <td>-7.504690</td>
      <td>-6.107224</td>
      <td>-14.645416</td>
      <td>2.684140</td>
      <td>-4.861559</td>
      <td>-7.504690</td>
      <td>-6.107224</td>
      <td>-14.645416</td>
      <td>2.684140</td>
    </tr>
    <tr>
      <th>Coosa County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>37.0</td>
      <td>11539.0</td>
      <td>11758.0</td>
      <td>11758.0</td>
      <td>11348.0</td>
      <td>11195.0</td>
      <td>...</td>
      <td>-33.930581</td>
      <td>-10.291443</td>
      <td>-4.313831</td>
      <td>-22.958017</td>
      <td>-5.387581</td>
      <td>-34.017138</td>
      <td>-10.380162</td>
      <td>-4.403703</td>
      <td>-23.049483</td>
      <td>-5.387581</td>
    </tr>
    <tr>
      <th>Covington County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>39.0</td>
      <td>37765.0</td>
      <td>37765.0</td>
      <td>37796.0</td>
      <td>38060.0</td>
      <td>37818.0</td>
      <td>...</td>
      <td>6.696899</td>
      <td>-4.612668</td>
      <td>0.740271</td>
      <td>3.697932</td>
      <td>-0.316945</td>
      <td>6.881460</td>
      <td>-4.559952</td>
      <td>0.793147</td>
      <td>3.750759</td>
      <td>-0.264121</td>
    </tr>
    <tr>
      <th>Crenshaw County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>41.0</td>
      <td>13906.0</td>
      <td>13906.0</td>
      <td>13853.0</td>
      <td>13896.0</td>
      <td>13951.0</td>
      <td>...</td>
      <td>1.729792</td>
      <td>3.950156</td>
      <td>-1.864936</td>
      <td>3.084648</td>
      <td>3.439504</td>
      <td>2.666763</td>
      <td>5.099293</td>
      <td>-0.502098</td>
      <td>4.734577</td>
      <td>5.087600</td>
    </tr>
    <tr>
      <th>Cullman County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>43.0</td>
      <td>80406.0</td>
      <td>80410.0</td>
      <td>80473.0</td>
      <td>80469.0</td>
      <td>80374.0</td>
      <td>...</td>
      <td>-1.404233</td>
      <td>-1.019628</td>
      <td>4.071247</td>
      <td>5.087142</td>
      <td>7.915406</td>
      <td>-1.031427</td>
      <td>-0.634159</td>
      <td>4.542916</td>
      <td>5.593387</td>
      <td>8.417777</td>
    </tr>
    <tr>
      <th>Dale County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>45.0</td>
      <td>50251.0</td>
      <td>50251.0</td>
      <td>50358.0</td>
      <td>50109.0</td>
      <td>50324.0</td>
      <td>...</td>
      <td>-10.749798</td>
      <td>-5.277150</td>
      <td>-15.236079</td>
      <td>-11.979785</td>
      <td>-5.107706</td>
      <td>-9.575283</td>
      <td>-0.776637</td>
      <td>-12.640155</td>
      <td>-9.503292</td>
      <td>-1.998668</td>
    </tr>
    <tr>
      <th>Dallas County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>47.0</td>
      <td>43820.0</td>
      <td>43820.0</td>
      <td>43803.0</td>
      <td>43178.0</td>
      <td>42777.0</td>
      <td>...</td>
      <td>-15.635599</td>
      <td>-11.308243</td>
      <td>-16.745678</td>
      <td>-9.344789</td>
      <td>-14.687232</td>
      <td>-15.727573</td>
      <td>-11.378047</td>
      <td>-16.792849</td>
      <td>-9.368689</td>
      <td>-14.711389</td>
    </tr>
    <tr>
      <th>DeKalb County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>49.0</td>
      <td>71109.0</td>
      <td>71115.0</td>
      <td>71142.0</td>
      <td>71387.0</td>
      <td>70942.0</td>
      <td>...</td>
      <td>0.294677</td>
      <td>-9.302391</td>
      <td>-1.748807</td>
      <td>0.267830</td>
      <td>0.028141</td>
      <td>1.375159</td>
      <td>-8.656001</td>
      <td>-1.029539</td>
      <td>1.198187</td>
      <td>0.956790</td>
    </tr>
    <tr>
      <th>Elmore County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>51.0</td>
      <td>79303.0</td>
      <td>79296.0</td>
      <td>79465.0</td>
      <td>80012.0</td>
      <td>80432.0</td>
      <td>...</td>
      <td>3.235576</td>
      <td>0.822717</td>
      <td>1.760531</td>
      <td>-1.507057</td>
      <td>2.067820</td>
      <td>3.674511</td>
      <td>1.558176</td>
      <td>2.306047</td>
      <td>-0.951175</td>
      <td>2.757093</td>
    </tr>
    <tr>
      <th>Escambia County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>53.0</td>
      <td>38319.0</td>
      <td>38319.0</td>
      <td>38309.0</td>
      <td>38213.0</td>
      <td>38034.0</td>
      <td>...</td>
      <td>-3.449988</td>
      <td>-3.855889</td>
      <td>-4.822706</td>
      <td>-1.189831</td>
      <td>1.190902</td>
      <td>-3.397716</td>
      <td>-3.803428</td>
      <td>-4.769999</td>
      <td>-1.136950</td>
      <td>1.243830</td>
    </tr>
    <tr>
      <th>Etowah County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>55.0</td>
      <td>104430.0</td>
      <td>104427.0</td>
      <td>104442.0</td>
      <td>104236.0</td>
      <td>104235.0</td>
      <td>...</td>
      <td>-1.015919</td>
      <td>2.062637</td>
      <td>-1.931884</td>
      <td>-1.726932</td>
      <td>-2.082234</td>
      <td>-0.632554</td>
      <td>2.446383</td>
      <td>-1.518596</td>
      <td>-1.234901</td>
      <td>-1.588308</td>
    </tr>
    <tr>
      <th>Fayette County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>57.0</td>
      <td>17241.0</td>
      <td>17241.0</td>
      <td>17231.0</td>
      <td>17062.0</td>
      <td>16960.0</td>
      <td>...</td>
      <td>-5.015601</td>
      <td>-0.646640</td>
      <td>-3.725937</td>
      <td>0.296745</td>
      <td>-2.797536</td>
      <td>-5.132243</td>
      <td>-0.705426</td>
      <td>-3.785079</td>
      <td>0.237396</td>
      <td>-2.857058</td>
    </tr>
    <tr>
      <th>Franklin County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>59.0</td>
      <td>31704.0</td>
      <td>31709.0</td>
      <td>31734.0</td>
      <td>31729.0</td>
      <td>31648.0</td>
      <td>...</td>
      <td>-1.638750</td>
      <td>-5.459394</td>
      <td>-8.043702</td>
      <td>-1.267849</td>
      <td>-2.401719</td>
      <td>0.063029</td>
      <td>-3.471291</td>
      <td>-5.700261</td>
      <td>1.553115</td>
      <td>0.442422</td>
    </tr>
    <tr>
      <th>...</th>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th rowspan="7" valign="top">Wisconsin</th>
      <th>Washburn County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>129.0</td>
      <td>15911.0</td>
      <td>15911.0</td>
      <td>15930.0</td>
      <td>15784.0</td>
      <td>15831.0</td>
      <td>...</td>
      <td>-6.873936</td>
      <td>7.338289</td>
      <td>-6.732724</td>
      <td>3.510452</td>
      <td>-5.123279</td>
      <td>-6.747809</td>
      <td>7.464811</td>
      <td>-6.605691</td>
      <td>3.638104</td>
      <td>-4.995197</td>
    </tr>
    <tr>
      <th>Washington County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>131.0</td>
      <td>131887.0</td>
      <td>131885.0</td>
      <td>131967.0</td>
      <td>132225.0</td>
      <td>132649.0</td>
      <td>...</td>
      <td>-0.794876</td>
      <td>0.785279</td>
      <td>-2.215465</td>
      <td>1.601149</td>
      <td>-0.434498</td>
      <td>-0.431504</td>
      <td>1.162817</td>
      <td>-1.763330</td>
      <td>2.104796</td>
      <td>0.059931</td>
    </tr>
    <tr>
      <th>Waukesha County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>133.0</td>
      <td>389891.0</td>
      <td>389938.0</td>
      <td>390076.0</td>
      <td>390808.0</td>
      <td>392710.0</td>
      <td>...</td>
      <td>-0.765799</td>
      <td>2.128860</td>
      <td>0.038132</td>
      <td>0.760109</td>
      <td>-0.719858</td>
      <td>0.102448</td>
      <td>3.180527</td>
      <td>1.189727</td>
      <td>2.077633</td>
      <td>0.593567</td>
    </tr>
    <tr>
      <th>Waupaca County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>135.0</td>
      <td>52410.0</td>
      <td>52410.0</td>
      <td>52422.0</td>
      <td>52342.0</td>
      <td>52035.0</td>
      <td>...</td>
      <td>3.111756</td>
      <td>-2.241873</td>
      <td>6.292687</td>
      <td>-0.441031</td>
      <td>-0.480617</td>
      <td>3.359933</td>
      <td>-2.011937</td>
      <td>6.561277</td>
      <td>-0.134227</td>
      <td>-0.173022</td>
    </tr>
    <tr>
      <th>Waushara County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>137.0</td>
      <td>24496.0</td>
      <td>24496.0</td>
      <td>24506.0</td>
      <td>24581.0</td>
      <td>24484.0</td>
      <td>...</td>
      <td>4.930022</td>
      <td>-2.404973</td>
      <td>-4.097017</td>
      <td>-4.906711</td>
      <td>-4.397793</td>
      <td>5.174486</td>
      <td>-2.160399</td>
      <td>-3.810226</td>
      <td>-4.535615</td>
      <td>-4.024395</td>
    </tr>
    <tr>
      <th>Winnebago County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>139.0</td>
      <td>166994.0</td>
      <td>166994.0</td>
      <td>167059.0</td>
      <td>167630.0</td>
      <td>168717.0</td>
      <td>...</td>
      <td>0.316712</td>
      <td>2.889873</td>
      <td>0.833819</td>
      <td>-2.406192</td>
      <td>-4.557985</td>
      <td>0.842573</td>
      <td>3.502335</td>
      <td>1.531624</td>
      <td>-1.545153</td>
      <td>-3.685304</td>
    </tr>
    <tr>
      <th>Wood County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>141.0</td>
      <td>74749.0</td>
      <td>74749.0</td>
      <td>74807.0</td>
      <td>74647.0</td>
      <td>74384.0</td>
      <td>...</td>
      <td>-4.081523</td>
      <td>-5.019090</td>
      <td>-6.901200</td>
      <td>-5.596471</td>
      <td>-3.958322</td>
      <td>-3.733590</td>
      <td>-4.562809</td>
      <td>-6.442917</td>
      <td>-5.040889</td>
      <td>-3.414223</td>
    </tr>
    <tr>
      <th rowspan="23" valign="top">Wyoming</th>
      <th>Albany County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>1.0</td>
      <td>36299.0</td>
      <td>36299.0</td>
      <td>36428.0</td>
      <td>36908.0</td>
      <td>37396.0</td>
      <td>...</td>
      <td>3.708956</td>
      <td>2.637812</td>
      <td>-3.544634</td>
      <td>-3.334877</td>
      <td>-9.911169</td>
      <td>6.736119</td>
      <td>6.433032</td>
      <td>0.719587</td>
      <td>1.429233</td>
      <td>-5.166460</td>
    </tr>
    <tr>
      <th>Big Horn County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>3.0</td>
      <td>11668.0</td>
      <td>11668.0</td>
      <td>11672.0</td>
      <td>11745.0</td>
      <td>11785.0</td>
      <td>...</td>
      <td>4.868258</td>
      <td>2.804930</td>
      <td>16.815908</td>
      <td>-8.026420</td>
      <td>5.095861</td>
      <td>4.868258</td>
      <td>3.144921</td>
      <td>17.236306</td>
      <td>-7.608378</td>
      <td>5.513554</td>
    </tr>
    <tr>
      <th>Campbell County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>5.0</td>
      <td>46133.0</td>
      <td>46133.0</td>
      <td>46244.0</td>
      <td>46600.0</td>
      <td>47881.0</td>
      <td>...</td>
      <td>-2.843479</td>
      <td>15.601020</td>
      <td>-5.895711</td>
      <td>-8.550911</td>
      <td>10.916963</td>
      <td>-2.649606</td>
      <td>15.558684</td>
      <td>-5.916543</td>
      <td>-8.509402</td>
      <td>10.978525</td>
    </tr>
    <tr>
      <th>Carbon County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>7.0</td>
      <td>15885.0</td>
      <td>15885.0</td>
      <td>15837.0</td>
      <td>15817.0</td>
      <td>15678.0</td>
      <td>...</td>
      <td>-7.581980</td>
      <td>-13.081441</td>
      <td>3.178134</td>
      <td>-2.970641</td>
      <td>-23.300971</td>
      <td>-7.392431</td>
      <td>-12.636926</td>
      <td>3.623073</td>
      <td>-2.338590</td>
      <td>-22.600668</td>
    </tr>
    <tr>
      <th>Converse County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>9.0</td>
      <td>13833.0</td>
      <td>13833.0</td>
      <td>13826.0</td>
      <td>13728.0</td>
      <td>14025.0</td>
      <td>...</td>
      <td>-12.847499</td>
      <td>15.493820</td>
      <td>19.035533</td>
      <td>-20.550587</td>
      <td>-0.070403</td>
      <td>-12.774915</td>
      <td>16.502720</td>
      <td>20.093063</td>
      <td>-19.358233</td>
      <td>1.126443</td>
    </tr>
    <tr>
      <th>Crook County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>11.0</td>
      <td>7083.0</td>
      <td>7083.0</td>
      <td>7114.0</td>
      <td>7129.0</td>
      <td>7148.0</td>
      <td>...</td>
      <td>-1.544618</td>
      <td>-4.202564</td>
      <td>1.397819</td>
      <td>6.378258</td>
      <td>18.629317</td>
      <td>-0.982939</td>
      <td>-3.642222</td>
      <td>2.096729</td>
      <td>7.071547</td>
      <td>19.309219</td>
    </tr>
    <tr>
      <th>Fremont County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>13.0</td>
      <td>40123.0</td>
      <td>40123.0</td>
      <td>40222.0</td>
      <td>40591.0</td>
      <td>41129.0</td>
      <td>...</td>
      <td>2.747083</td>
      <td>7.782673</td>
      <td>-4.990688</td>
      <td>-12.331633</td>
      <td>-13.673610</td>
      <td>3.093562</td>
      <td>8.027411</td>
      <td>-4.747240</td>
      <td>-12.013555</td>
      <td>-13.352750</td>
    </tr>
    <tr>
      <th>Goshen County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>15.0</td>
      <td>13249.0</td>
      <td>13247.0</td>
      <td>13408.0</td>
      <td>13597.0</td>
      <td>13666.0</td>
      <td>...</td>
      <td>14.293649</td>
      <td>3.961413</td>
      <td>-8.079028</td>
      <td>-7.017803</td>
      <td>-11.899450</td>
      <td>14.886132</td>
      <td>4.841727</td>
      <td>-6.903896</td>
      <td>-5.761986</td>
      <td>-10.635133</td>
    </tr>
    <tr>
      <th>Hot Springs County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>17.0</td>
      <td>4812.0</td>
      <td>4812.0</td>
      <td>4813.0</td>
      <td>4818.0</td>
      <td>4846.0</td>
      <td>...</td>
      <td>3.322604</td>
      <td>6.208609</td>
      <td>3.095336</td>
      <td>-6.017222</td>
      <td>-5.454164</td>
      <td>5.191569</td>
      <td>6.001656</td>
      <td>2.888981</td>
      <td>-6.224712</td>
      <td>-5.663940</td>
    </tr>
    <tr>
      <th>Johnson County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>19.0</td>
      <td>8569.0</td>
      <td>8569.0</td>
      <td>8581.0</td>
      <td>8636.0</td>
      <td>8610.0</td>
      <td>...</td>
      <td>4.995063</td>
      <td>-4.058912</td>
      <td>-0.812583</td>
      <td>-10.715742</td>
      <td>0.933652</td>
      <td>5.227392</td>
      <td>-4.058912</td>
      <td>-0.812583</td>
      <td>-10.715742</td>
      <td>0.933652</td>
    </tr>
    <tr>
      <th>Laramie County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>21.0</td>
      <td>91738.0</td>
      <td>91881.0</td>
      <td>92271.0</td>
      <td>92663.0</td>
      <td>94894.0</td>
      <td>...</td>
      <td>-1.200428</td>
      <td>15.547274</td>
      <td>4.787847</td>
      <td>-1.226133</td>
      <td>0.278940</td>
      <td>-0.973320</td>
      <td>17.914554</td>
      <td>6.003143</td>
      <td>-0.207819</td>
      <td>1.673640</td>
    </tr>
    <tr>
      <th>Lincoln County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>23.0</td>
      <td>18106.0</td>
      <td>18106.0</td>
      <td>18091.0</td>
      <td>18022.0</td>
      <td>17943.0</td>
      <td>...</td>
      <td>-9.802564</td>
      <td>-11.566801</td>
      <td>13.564556</td>
      <td>6.125989</td>
      <td>1.555544</td>
      <td>-9.691801</td>
      <td>-11.566801</td>
      <td>13.619696</td>
      <td>6.234414</td>
      <td>1.662823</td>
    </tr>
    <tr>
      <th>Natrona County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>25.0</td>
      <td>75450.0</td>
      <td>75450.0</td>
      <td>75472.0</td>
      <td>76420.0</td>
      <td>78699.0</td>
      <td>...</td>
      <td>7.189319</td>
      <td>23.066162</td>
      <td>24.322042</td>
      <td>-0.958472</td>
      <td>-0.061057</td>
      <td>7.689674</td>
      <td>23.749508</td>
      <td>25.085233</td>
      <td>-0.110593</td>
      <td>0.793743</td>
    </tr>
    <tr>
      <th>Niobrara County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>27.0</td>
      <td>2484.0</td>
      <td>2484.0</td>
      <td>2492.0</td>
      <td>2485.0</td>
      <td>2475.0</td>
      <td>...</td>
      <td>-0.401849</td>
      <td>0.806452</td>
      <td>29.066295</td>
      <td>-12.603387</td>
      <td>7.492114</td>
      <td>-0.401849</td>
      <td>0.806452</td>
      <td>29.066295</td>
      <td>-12.603387</td>
      <td>7.492114</td>
    </tr>
    <tr>
      <th>Park County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>29.0</td>
      <td>28205.0</td>
      <td>28205.0</td>
      <td>28259.0</td>
      <td>28473.0</td>
      <td>28863.0</td>
      <td>...</td>
      <td>4.582951</td>
      <td>8.057765</td>
      <td>7.641997</td>
      <td>-9.252437</td>
      <td>-2.878980</td>
      <td>6.486639</td>
      <td>11.127389</td>
      <td>10.877797</td>
      <td>-5.585731</td>
      <td>0.856839</td>
    </tr>
    <tr>
      <th>Platte County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>31.0</td>
      <td>8667.0</td>
      <td>8667.0</td>
      <td>8678.0</td>
      <td>8701.0</td>
      <td>8732.0</td>
      <td>...</td>
      <td>4.373094</td>
      <td>5.392073</td>
      <td>2.634593</td>
      <td>6.055759</td>
      <td>4.662270</td>
      <td>4.373094</td>
      <td>4.933173</td>
      <td>2.176403</td>
      <td>5.598720</td>
      <td>4.207414</td>
    </tr>
    <tr>
      <th>Sheridan County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>33.0</td>
      <td>29116.0</td>
      <td>29116.0</td>
      <td>29146.0</td>
      <td>29275.0</td>
      <td>29594.0</td>
      <td>...</td>
      <td>0.958559</td>
      <td>8.425487</td>
      <td>4.546373</td>
      <td>3.678069</td>
      <td>-3.298406</td>
      <td>2.122524</td>
      <td>9.342778</td>
      <td>5.523001</td>
      <td>4.781489</td>
      <td>-2.198937</td>
    </tr>
    <tr>
      <th>Sublette County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>35.0</td>
      <td>10247.0</td>
      <td>10247.0</td>
      <td>10244.0</td>
      <td>10142.0</td>
      <td>10418.0</td>
      <td>...</td>
      <td>-23.741784</td>
      <td>15.272374</td>
      <td>-40.870074</td>
      <td>-16.596273</td>
      <td>-22.870900</td>
      <td>-21.092907</td>
      <td>16.828794</td>
      <td>-39.211861</td>
      <td>-14.409938</td>
      <td>-20.664059</td>
    </tr>
    <tr>
      <th>Sweetwater County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>37.0</td>
      <td>43806.0</td>
      <td>43806.0</td>
      <td>43593.0</td>
      <td>44041.0</td>
      <td>45104.0</td>
      <td>...</td>
      <td>1.072643</td>
      <td>16.243199</td>
      <td>-5.339774</td>
      <td>-14.252889</td>
      <td>-14.248864</td>
      <td>1.255221</td>
      <td>16.243199</td>
      <td>-5.295460</td>
      <td>-14.075283</td>
      <td>-14.070195</td>
    </tr>
    <tr>
      <th>Teton County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>39.0</td>
      <td>21294.0</td>
      <td>21294.0</td>
      <td>21297.0</td>
      <td>21482.0</td>
      <td>21697.0</td>
      <td>...</td>
      <td>-1.589565</td>
      <td>0.972695</td>
      <td>19.525929</td>
      <td>14.143021</td>
      <td>-0.564849</td>
      <td>0.654527</td>
      <td>2.408578</td>
      <td>21.160658</td>
      <td>16.308671</td>
      <td>1.520747</td>
    </tr>
    <tr>
      <th>Uinta County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>41.0</td>
      <td>21118.0</td>
      <td>21118.0</td>
      <td>21102.0</td>
      <td>20912.0</td>
      <td>20989.0</td>
      <td>...</td>
      <td>-17.755986</td>
      <td>-4.916350</td>
      <td>-6.902954</td>
      <td>-14.215862</td>
      <td>-12.127022</td>
      <td>-18.136812</td>
      <td>-5.536861</td>
      <td>-7.521840</td>
      <td>-14.740608</td>
      <td>-12.606351</td>
    </tr>
    <tr>
      <th>Washakie County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>43.0</td>
      <td>8533.0</td>
      <td>8533.0</td>
      <td>8545.0</td>
      <td>8469.0</td>
      <td>8443.0</td>
      <td>...</td>
      <td>-11.637475</td>
      <td>-0.827815</td>
      <td>-2.013502</td>
      <td>-17.781491</td>
      <td>1.682288</td>
      <td>-11.990126</td>
      <td>-1.182592</td>
      <td>-2.250385</td>
      <td>-18.020168</td>
      <td>1.441961</td>
    </tr>
    <tr>
      <th>Weston County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>45.0</td>
      <td>7208.0</td>
      <td>7208.0</td>
      <td>7181.0</td>
      <td>7114.0</td>
      <td>7065.0</td>
      <td>...</td>
      <td>-11.752361</td>
      <td>-8.040059</td>
      <td>12.372583</td>
      <td>1.533635</td>
      <td>6.935294</td>
      <td>-12.032179</td>
      <td>-8.040059</td>
      <td>12.372583</td>
      <td>1.533635</td>
      <td>6.935294</td>
    </tr>
  </tbody>
</table>
<p>3142 rows × 98 columns</p>
</div>




```python
df = df[df['SUMLEV']==50]
df.set_index(['STNAME','CTYNAME'], inplace=True)
df.rename(columns={'ESTIMATESBASE2010': 'Estimates Base 2010'})
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>SUMLEV</th>
      <th>REGION</th>
      <th>DIVISION</th>
      <th>STATE</th>
      <th>COUNTY</th>
      <th>CENSUS2010POP</th>
      <th>Estimates Base 2010</th>
      <th>POPESTIMATE2010</th>
      <th>POPESTIMATE2011</th>
      <th>POPESTIMATE2012</th>
      <th>...</th>
      <th>RDOMESTICMIG2011</th>
      <th>RDOMESTICMIG2012</th>
      <th>RDOMESTICMIG2013</th>
      <th>RDOMESTICMIG2014</th>
      <th>RDOMESTICMIG2015</th>
      <th>RNETMIG2011</th>
      <th>RNETMIG2012</th>
      <th>RNETMIG2013</th>
      <th>RNETMIG2014</th>
      <th>RNETMIG2015</th>
    </tr>
    <tr>
      <th>STNAME</th>
      <th>CTYNAME</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="30" valign="top">Alabama</th>
      <th>Autauga County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>1</td>
      <td>54571</td>
      <td>54571</td>
      <td>54660</td>
      <td>55253</td>
      <td>55175</td>
      <td>...</td>
      <td>7.242091</td>
      <td>-2.915927</td>
      <td>-3.012349</td>
      <td>2.265971</td>
      <td>-2.530799</td>
      <td>7.606016</td>
      <td>-2.626146</td>
      <td>-2.722002</td>
      <td>2.592270</td>
      <td>-2.187333</td>
    </tr>
    <tr>
      <th>Baldwin County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>3</td>
      <td>182265</td>
      <td>182265</td>
      <td>183193</td>
      <td>186659</td>
      <td>190396</td>
      <td>...</td>
      <td>14.832960</td>
      <td>17.647293</td>
      <td>21.845705</td>
      <td>19.243287</td>
      <td>17.197872</td>
      <td>15.844176</td>
      <td>18.559627</td>
      <td>22.727626</td>
      <td>20.317142</td>
      <td>18.293499</td>
    </tr>
    <tr>
      <th>Barbour County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>5</td>
      <td>27457</td>
      <td>27457</td>
      <td>27341</td>
      <td>27226</td>
      <td>27159</td>
      <td>...</td>
      <td>-4.728132</td>
      <td>-2.500690</td>
      <td>-7.056824</td>
      <td>-3.904217</td>
      <td>-10.543299</td>
      <td>-4.874741</td>
      <td>-2.758113</td>
      <td>-7.167664</td>
      <td>-3.978583</td>
      <td>-10.543299</td>
    </tr>
    <tr>
      <th>Bibb County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>7</td>
      <td>22915</td>
      <td>22919</td>
      <td>22861</td>
      <td>22733</td>
      <td>22642</td>
      <td>...</td>
      <td>-5.527043</td>
      <td>-5.068871</td>
      <td>-6.201001</td>
      <td>-0.177537</td>
      <td>0.177258</td>
      <td>-5.088389</td>
      <td>-4.363636</td>
      <td>-5.403729</td>
      <td>0.754533</td>
      <td>1.107861</td>
    </tr>
    <tr>
      <th>Blount County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>9</td>
      <td>57322</td>
      <td>57322</td>
      <td>57373</td>
      <td>57711</td>
      <td>57776</td>
      <td>...</td>
      <td>1.807375</td>
      <td>-1.177622</td>
      <td>-1.748766</td>
      <td>-2.062535</td>
      <td>-1.369970</td>
      <td>1.859511</td>
      <td>-0.848580</td>
      <td>-1.402476</td>
      <td>-1.577232</td>
      <td>-0.884411</td>
    </tr>
    <tr>
      <th>Bullock County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>11</td>
      <td>10914</td>
      <td>10915</td>
      <td>10887</td>
      <td>10629</td>
      <td>10606</td>
      <td>...</td>
      <td>-30.953709</td>
      <td>-5.180127</td>
      <td>-1.130263</td>
      <td>14.354290</td>
      <td>-16.167247</td>
      <td>-29.001673</td>
      <td>-2.825524</td>
      <td>1.507017</td>
      <td>17.243790</td>
      <td>-13.193961</td>
    </tr>
    <tr>
      <th>Butler County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>13</td>
      <td>20947</td>
      <td>20946</td>
      <td>20944</td>
      <td>20673</td>
      <td>20408</td>
      <td>...</td>
      <td>-14.032727</td>
      <td>-11.684234</td>
      <td>-5.655413</td>
      <td>1.085428</td>
      <td>-6.529805</td>
      <td>-13.936612</td>
      <td>-11.586865</td>
      <td>-5.557058</td>
      <td>1.184103</td>
      <td>-6.430868</td>
    </tr>
    <tr>
      <th>Calhoun County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>15</td>
      <td>118572</td>
      <td>118586</td>
      <td>118437</td>
      <td>117768</td>
      <td>117286</td>
      <td>...</td>
      <td>-6.155670</td>
      <td>-4.611706</td>
      <td>-5.524649</td>
      <td>-4.463211</td>
      <td>-3.376322</td>
      <td>-5.791579</td>
      <td>-4.092677</td>
      <td>-5.062836</td>
      <td>-3.912834</td>
      <td>-2.806406</td>
    </tr>
    <tr>
      <th>Chambers County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>17</td>
      <td>34215</td>
      <td>34170</td>
      <td>34098</td>
      <td>33993</td>
      <td>34075</td>
      <td>...</td>
      <td>-2.731639</td>
      <td>3.849092</td>
      <td>2.872721</td>
      <td>-2.287222</td>
      <td>1.349468</td>
      <td>-1.821092</td>
      <td>4.701181</td>
      <td>3.781439</td>
      <td>-1.290228</td>
      <td>2.346901</td>
    </tr>
    <tr>
      <th>Cherokee County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>19</td>
      <td>25989</td>
      <td>25986</td>
      <td>25976</td>
      <td>26080</td>
      <td>26023</td>
      <td>...</td>
      <td>6.339327</td>
      <td>1.113180</td>
      <td>5.488706</td>
      <td>-0.076806</td>
      <td>-3.239866</td>
      <td>6.416167</td>
      <td>1.420264</td>
      <td>5.757384</td>
      <td>0.230419</td>
      <td>-2.931307</td>
    </tr>
    <tr>
      <th>Chilton County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>21</td>
      <td>43643</td>
      <td>43631</td>
      <td>43665</td>
      <td>43739</td>
      <td>43697</td>
      <td>...</td>
      <td>-1.372935</td>
      <td>-2.653369</td>
      <td>0.480044</td>
      <td>0.456017</td>
      <td>-2.253483</td>
      <td>-0.823761</td>
      <td>-2.447504</td>
      <td>0.868651</td>
      <td>0.957636</td>
      <td>-1.752709</td>
    </tr>
    <tr>
      <th>Choctaw County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>23</td>
      <td>13859</td>
      <td>13858</td>
      <td>13841</td>
      <td>13593</td>
      <td>13543</td>
      <td>...</td>
      <td>-15.455274</td>
      <td>-0.737028</td>
      <td>-8.766391</td>
      <td>-1.274984</td>
      <td>-5.291205</td>
      <td>-15.528177</td>
      <td>-0.737028</td>
      <td>-8.766391</td>
      <td>-1.274984</td>
      <td>-5.291205</td>
    </tr>
    <tr>
      <th>Clarke County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>25</td>
      <td>25833</td>
      <td>25840</td>
      <td>25767</td>
      <td>25570</td>
      <td>25144</td>
      <td>...</td>
      <td>-6.194363</td>
      <td>-17.667705</td>
      <td>-0.318345</td>
      <td>-8.686428</td>
      <td>-5.613667</td>
      <td>-6.077488</td>
      <td>-17.509958</td>
      <td>-0.159172</td>
      <td>-8.486280</td>
      <td>-5.411736</td>
    </tr>
    <tr>
      <th>Clay County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>27</td>
      <td>13932</td>
      <td>13932</td>
      <td>13880</td>
      <td>13670</td>
      <td>13456</td>
      <td>...</td>
      <td>-10.744102</td>
      <td>-13.345130</td>
      <td>4.902871</td>
      <td>5.702648</td>
      <td>3.912450</td>
      <td>-10.816697</td>
      <td>-13.345130</td>
      <td>4.977157</td>
      <td>5.776708</td>
      <td>3.986270</td>
    </tr>
    <tr>
      <th>Cleburne County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>29</td>
      <td>14972</td>
      <td>14972</td>
      <td>14973</td>
      <td>14971</td>
      <td>14921</td>
      <td>...</td>
      <td>-3.673524</td>
      <td>-5.151880</td>
      <td>7.345821</td>
      <td>3.654485</td>
      <td>-3.123961</td>
      <td>-3.673524</td>
      <td>-5.151880</td>
      <td>7.345821</td>
      <td>3.654485</td>
      <td>-3.123961</td>
    </tr>
    <tr>
      <th>Coffee County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>31</td>
      <td>49948</td>
      <td>49948</td>
      <td>50177</td>
      <td>50448</td>
      <td>51173</td>
      <td>...</td>
      <td>0.377640</td>
      <td>7.675579</td>
      <td>-13.146535</td>
      <td>-3.602859</td>
      <td>2.214774</td>
      <td>2.166460</td>
      <td>11.513368</td>
      <td>-10.438741</td>
      <td>-0.767822</td>
      <td>5.350738</td>
    </tr>
    <tr>
      <th>Colbert County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>33</td>
      <td>54428</td>
      <td>54428</td>
      <td>54514</td>
      <td>54443</td>
      <td>54472</td>
      <td>...</td>
      <td>-0.073423</td>
      <td>1.065051</td>
      <td>1.762390</td>
      <td>1.835688</td>
      <td>-0.110260</td>
      <td>0.513964</td>
      <td>1.469035</td>
      <td>2.276420</td>
      <td>2.533249</td>
      <td>0.588052</td>
    </tr>
    <tr>
      <th>Conecuh County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>35</td>
      <td>13228</td>
      <td>13228</td>
      <td>13208</td>
      <td>13121</td>
      <td>12996</td>
      <td>...</td>
      <td>-4.861559</td>
      <td>-7.504690</td>
      <td>-6.107224</td>
      <td>-14.645416</td>
      <td>2.684140</td>
      <td>-4.861559</td>
      <td>-7.504690</td>
      <td>-6.107224</td>
      <td>-14.645416</td>
      <td>2.684140</td>
    </tr>
    <tr>
      <th>Coosa County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>37</td>
      <td>11539</td>
      <td>11758</td>
      <td>11758</td>
      <td>11348</td>
      <td>11195</td>
      <td>...</td>
      <td>-33.930581</td>
      <td>-10.291443</td>
      <td>-4.313831</td>
      <td>-22.958017</td>
      <td>-5.387581</td>
      <td>-34.017138</td>
      <td>-10.380162</td>
      <td>-4.403703</td>
      <td>-23.049483</td>
      <td>-5.387581</td>
    </tr>
    <tr>
      <th>Covington County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>39</td>
      <td>37765</td>
      <td>37765</td>
      <td>37796</td>
      <td>38060</td>
      <td>37818</td>
      <td>...</td>
      <td>6.696899</td>
      <td>-4.612668</td>
      <td>0.740271</td>
      <td>3.697932</td>
      <td>-0.316945</td>
      <td>6.881460</td>
      <td>-4.559952</td>
      <td>0.793147</td>
      <td>3.750759</td>
      <td>-0.264121</td>
    </tr>
    <tr>
      <th>Crenshaw County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>41</td>
      <td>13906</td>
      <td>13906</td>
      <td>13853</td>
      <td>13896</td>
      <td>13951</td>
      <td>...</td>
      <td>1.729792</td>
      <td>3.950156</td>
      <td>-1.864936</td>
      <td>3.084648</td>
      <td>3.439504</td>
      <td>2.666763</td>
      <td>5.099293</td>
      <td>-0.502098</td>
      <td>4.734577</td>
      <td>5.087600</td>
    </tr>
    <tr>
      <th>Cullman County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>43</td>
      <td>80406</td>
      <td>80410</td>
      <td>80473</td>
      <td>80469</td>
      <td>80374</td>
      <td>...</td>
      <td>-1.404233</td>
      <td>-1.019628</td>
      <td>4.071247</td>
      <td>5.087142</td>
      <td>7.915406</td>
      <td>-1.031427</td>
      <td>-0.634159</td>
      <td>4.542916</td>
      <td>5.593387</td>
      <td>8.417777</td>
    </tr>
    <tr>
      <th>Dale County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>45</td>
      <td>50251</td>
      <td>50251</td>
      <td>50358</td>
      <td>50109</td>
      <td>50324</td>
      <td>...</td>
      <td>-10.749798</td>
      <td>-5.277150</td>
      <td>-15.236079</td>
      <td>-11.979785</td>
      <td>-5.107706</td>
      <td>-9.575283</td>
      <td>-0.776637</td>
      <td>-12.640155</td>
      <td>-9.503292</td>
      <td>-1.998668</td>
    </tr>
    <tr>
      <th>Dallas County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>47</td>
      <td>43820</td>
      <td>43820</td>
      <td>43803</td>
      <td>43178</td>
      <td>42777</td>
      <td>...</td>
      <td>-15.635599</td>
      <td>-11.308243</td>
      <td>-16.745678</td>
      <td>-9.344789</td>
      <td>-14.687232</td>
      <td>-15.727573</td>
      <td>-11.378047</td>
      <td>-16.792849</td>
      <td>-9.368689</td>
      <td>-14.711389</td>
    </tr>
    <tr>
      <th>DeKalb County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>49</td>
      <td>71109</td>
      <td>71115</td>
      <td>71142</td>
      <td>71387</td>
      <td>70942</td>
      <td>...</td>
      <td>0.294677</td>
      <td>-9.302391</td>
      <td>-1.748807</td>
      <td>0.267830</td>
      <td>0.028141</td>
      <td>1.375159</td>
      <td>-8.656001</td>
      <td>-1.029539</td>
      <td>1.198187</td>
      <td>0.956790</td>
    </tr>
    <tr>
      <th>Elmore County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>51</td>
      <td>79303</td>
      <td>79296</td>
      <td>79465</td>
      <td>80012</td>
      <td>80432</td>
      <td>...</td>
      <td>3.235576</td>
      <td>0.822717</td>
      <td>1.760531</td>
      <td>-1.507057</td>
      <td>2.067820</td>
      <td>3.674511</td>
      <td>1.558176</td>
      <td>2.306047</td>
      <td>-0.951175</td>
      <td>2.757093</td>
    </tr>
    <tr>
      <th>Escambia County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>53</td>
      <td>38319</td>
      <td>38319</td>
      <td>38309</td>
      <td>38213</td>
      <td>38034</td>
      <td>...</td>
      <td>-3.449988</td>
      <td>-3.855889</td>
      <td>-4.822706</td>
      <td>-1.189831</td>
      <td>1.190902</td>
      <td>-3.397716</td>
      <td>-3.803428</td>
      <td>-4.769999</td>
      <td>-1.136950</td>
      <td>1.243830</td>
    </tr>
    <tr>
      <th>Etowah County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>55</td>
      <td>104430</td>
      <td>104427</td>
      <td>104442</td>
      <td>104236</td>
      <td>104235</td>
      <td>...</td>
      <td>-1.015919</td>
      <td>2.062637</td>
      <td>-1.931884</td>
      <td>-1.726932</td>
      <td>-2.082234</td>
      <td>-0.632554</td>
      <td>2.446383</td>
      <td>-1.518596</td>
      <td>-1.234901</td>
      <td>-1.588308</td>
    </tr>
    <tr>
      <th>Fayette County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>57</td>
      <td>17241</td>
      <td>17241</td>
      <td>17231</td>
      <td>17062</td>
      <td>16960</td>
      <td>...</td>
      <td>-5.015601</td>
      <td>-0.646640</td>
      <td>-3.725937</td>
      <td>0.296745</td>
      <td>-2.797536</td>
      <td>-5.132243</td>
      <td>-0.705426</td>
      <td>-3.785079</td>
      <td>0.237396</td>
      <td>-2.857058</td>
    </tr>
    <tr>
      <th>Franklin County</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>59</td>
      <td>31704</td>
      <td>31709</td>
      <td>31734</td>
      <td>31729</td>
      <td>31648</td>
      <td>...</td>
      <td>-1.638750</td>
      <td>-5.459394</td>
      <td>-8.043702</td>
      <td>-1.267849</td>
      <td>-2.401719</td>
      <td>0.063029</td>
      <td>-3.471291</td>
      <td>-5.700261</td>
      <td>1.553115</td>
      <td>0.442422</td>
    </tr>
    <tr>
      <th>...</th>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th rowspan="7" valign="top">Wisconsin</th>
      <th>Washburn County</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>129</td>
      <td>15911</td>
      <td>15911</td>
      <td>15930</td>
      <td>15784</td>
      <td>15831</td>
      <td>...</td>
      <td>-6.873936</td>
      <td>7.338289</td>
      <td>-6.732724</td>
      <td>3.510452</td>
      <td>-5.123279</td>
      <td>-6.747809</td>
      <td>7.464811</td>
      <td>-6.605691</td>
      <td>3.638104</td>
      <td>-4.995197</td>
    </tr>
    <tr>
      <th>Washington County</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>131</td>
      <td>131887</td>
      <td>131885</td>
      <td>131967</td>
      <td>132225</td>
      <td>132649</td>
      <td>...</td>
      <td>-0.794876</td>
      <td>0.785279</td>
      <td>-2.215465</td>
      <td>1.601149</td>
      <td>-0.434498</td>
      <td>-0.431504</td>
      <td>1.162817</td>
      <td>-1.763330</td>
      <td>2.104796</td>
      <td>0.059931</td>
    </tr>
    <tr>
      <th>Waukesha County</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>133</td>
      <td>389891</td>
      <td>389938</td>
      <td>390076</td>
      <td>390808</td>
      <td>392710</td>
      <td>...</td>
      <td>-0.765799</td>
      <td>2.128860</td>
      <td>0.038132</td>
      <td>0.760109</td>
      <td>-0.719858</td>
      <td>0.102448</td>
      <td>3.180527</td>
      <td>1.189727</td>
      <td>2.077633</td>
      <td>0.593567</td>
    </tr>
    <tr>
      <th>Waupaca County</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>135</td>
      <td>52410</td>
      <td>52410</td>
      <td>52422</td>
      <td>52342</td>
      <td>52035</td>
      <td>...</td>
      <td>3.111756</td>
      <td>-2.241873</td>
      <td>6.292687</td>
      <td>-0.441031</td>
      <td>-0.480617</td>
      <td>3.359933</td>
      <td>-2.011937</td>
      <td>6.561277</td>
      <td>-0.134227</td>
      <td>-0.173022</td>
    </tr>
    <tr>
      <th>Waushara County</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>137</td>
      <td>24496</td>
      <td>24496</td>
      <td>24506</td>
      <td>24581</td>
      <td>24484</td>
      <td>...</td>
      <td>4.930022</td>
      <td>-2.404973</td>
      <td>-4.097017</td>
      <td>-4.906711</td>
      <td>-4.397793</td>
      <td>5.174486</td>
      <td>-2.160399</td>
      <td>-3.810226</td>
      <td>-4.535615</td>
      <td>-4.024395</td>
    </tr>
    <tr>
      <th>Winnebago County</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>139</td>
      <td>166994</td>
      <td>166994</td>
      <td>167059</td>
      <td>167630</td>
      <td>168717</td>
      <td>...</td>
      <td>0.316712</td>
      <td>2.889873</td>
      <td>0.833819</td>
      <td>-2.406192</td>
      <td>-4.557985</td>
      <td>0.842573</td>
      <td>3.502335</td>
      <td>1.531624</td>
      <td>-1.545153</td>
      <td>-3.685304</td>
    </tr>
    <tr>
      <th>Wood County</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>141</td>
      <td>74749</td>
      <td>74749</td>
      <td>74807</td>
      <td>74647</td>
      <td>74384</td>
      <td>...</td>
      <td>-4.081523</td>
      <td>-5.019090</td>
      <td>-6.901200</td>
      <td>-5.596471</td>
      <td>-3.958322</td>
      <td>-3.733590</td>
      <td>-4.562809</td>
      <td>-6.442917</td>
      <td>-5.040889</td>
      <td>-3.414223</td>
    </tr>
    <tr>
      <th rowspan="23" valign="top">Wyoming</th>
      <th>Albany County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>1</td>
      <td>36299</td>
      <td>36299</td>
      <td>36428</td>
      <td>36908</td>
      <td>37396</td>
      <td>...</td>
      <td>3.708956</td>
      <td>2.637812</td>
      <td>-3.544634</td>
      <td>-3.334877</td>
      <td>-9.911169</td>
      <td>6.736119</td>
      <td>6.433032</td>
      <td>0.719587</td>
      <td>1.429233</td>
      <td>-5.166460</td>
    </tr>
    <tr>
      <th>Big Horn County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>3</td>
      <td>11668</td>
      <td>11668</td>
      <td>11672</td>
      <td>11745</td>
      <td>11785</td>
      <td>...</td>
      <td>4.868258</td>
      <td>2.804930</td>
      <td>16.815908</td>
      <td>-8.026420</td>
      <td>5.095861</td>
      <td>4.868258</td>
      <td>3.144921</td>
      <td>17.236306</td>
      <td>-7.608378</td>
      <td>5.513554</td>
    </tr>
    <tr>
      <th>Campbell County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>5</td>
      <td>46133</td>
      <td>46133</td>
      <td>46244</td>
      <td>46600</td>
      <td>47881</td>
      <td>...</td>
      <td>-2.843479</td>
      <td>15.601020</td>
      <td>-5.895711</td>
      <td>-8.550911</td>
      <td>10.916963</td>
      <td>-2.649606</td>
      <td>15.558684</td>
      <td>-5.916543</td>
      <td>-8.509402</td>
      <td>10.978525</td>
    </tr>
    <tr>
      <th>Carbon County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>7</td>
      <td>15885</td>
      <td>15885</td>
      <td>15837</td>
      <td>15817</td>
      <td>15678</td>
      <td>...</td>
      <td>-7.581980</td>
      <td>-13.081441</td>
      <td>3.178134</td>
      <td>-2.970641</td>
      <td>-23.300971</td>
      <td>-7.392431</td>
      <td>-12.636926</td>
      <td>3.623073</td>
      <td>-2.338590</td>
      <td>-22.600668</td>
    </tr>
    <tr>
      <th>Converse County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>9</td>
      <td>13833</td>
      <td>13833</td>
      <td>13826</td>
      <td>13728</td>
      <td>14025</td>
      <td>...</td>
      <td>-12.847499</td>
      <td>15.493820</td>
      <td>19.035533</td>
      <td>-20.550587</td>
      <td>-0.070403</td>
      <td>-12.774915</td>
      <td>16.502720</td>
      <td>20.093063</td>
      <td>-19.358233</td>
      <td>1.126443</td>
    </tr>
    <tr>
      <th>Crook County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>11</td>
      <td>7083</td>
      <td>7083</td>
      <td>7114</td>
      <td>7129</td>
      <td>7148</td>
      <td>...</td>
      <td>-1.544618</td>
      <td>-4.202564</td>
      <td>1.397819</td>
      <td>6.378258</td>
      <td>18.629317</td>
      <td>-0.982939</td>
      <td>-3.642222</td>
      <td>2.096729</td>
      <td>7.071547</td>
      <td>19.309219</td>
    </tr>
    <tr>
      <th>Fremont County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>13</td>
      <td>40123</td>
      <td>40123</td>
      <td>40222</td>
      <td>40591</td>
      <td>41129</td>
      <td>...</td>
      <td>2.747083</td>
      <td>7.782673</td>
      <td>-4.990688</td>
      <td>-12.331633</td>
      <td>-13.673610</td>
      <td>3.093562</td>
      <td>8.027411</td>
      <td>-4.747240</td>
      <td>-12.013555</td>
      <td>-13.352750</td>
    </tr>
    <tr>
      <th>Goshen County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>15</td>
      <td>13249</td>
      <td>13247</td>
      <td>13408</td>
      <td>13597</td>
      <td>13666</td>
      <td>...</td>
      <td>14.293649</td>
      <td>3.961413</td>
      <td>-8.079028</td>
      <td>-7.017803</td>
      <td>-11.899450</td>
      <td>14.886132</td>
      <td>4.841727</td>
      <td>-6.903896</td>
      <td>-5.761986</td>
      <td>-10.635133</td>
    </tr>
    <tr>
      <th>Hot Springs County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>17</td>
      <td>4812</td>
      <td>4812</td>
      <td>4813</td>
      <td>4818</td>
      <td>4846</td>
      <td>...</td>
      <td>3.322604</td>
      <td>6.208609</td>
      <td>3.095336</td>
      <td>-6.017222</td>
      <td>-5.454164</td>
      <td>5.191569</td>
      <td>6.001656</td>
      <td>2.888981</td>
      <td>-6.224712</td>
      <td>-5.663940</td>
    </tr>
    <tr>
      <th>Johnson County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>19</td>
      <td>8569</td>
      <td>8569</td>
      <td>8581</td>
      <td>8636</td>
      <td>8610</td>
      <td>...</td>
      <td>4.995063</td>
      <td>-4.058912</td>
      <td>-0.812583</td>
      <td>-10.715742</td>
      <td>0.933652</td>
      <td>5.227392</td>
      <td>-4.058912</td>
      <td>-0.812583</td>
      <td>-10.715742</td>
      <td>0.933652</td>
    </tr>
    <tr>
      <th>Laramie County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>21</td>
      <td>91738</td>
      <td>91881</td>
      <td>92271</td>
      <td>92663</td>
      <td>94894</td>
      <td>...</td>
      <td>-1.200428</td>
      <td>15.547274</td>
      <td>4.787847</td>
      <td>-1.226133</td>
      <td>0.278940</td>
      <td>-0.973320</td>
      <td>17.914554</td>
      <td>6.003143</td>
      <td>-0.207819</td>
      <td>1.673640</td>
    </tr>
    <tr>
      <th>Lincoln County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>23</td>
      <td>18106</td>
      <td>18106</td>
      <td>18091</td>
      <td>18022</td>
      <td>17943</td>
      <td>...</td>
      <td>-9.802564</td>
      <td>-11.566801</td>
      <td>13.564556</td>
      <td>6.125989</td>
      <td>1.555544</td>
      <td>-9.691801</td>
      <td>-11.566801</td>
      <td>13.619696</td>
      <td>6.234414</td>
      <td>1.662823</td>
    </tr>
    <tr>
      <th>Natrona County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>25</td>
      <td>75450</td>
      <td>75450</td>
      <td>75472</td>
      <td>76420</td>
      <td>78699</td>
      <td>...</td>
      <td>7.189319</td>
      <td>23.066162</td>
      <td>24.322042</td>
      <td>-0.958472</td>
      <td>-0.061057</td>
      <td>7.689674</td>
      <td>23.749508</td>
      <td>25.085233</td>
      <td>-0.110593</td>
      <td>0.793743</td>
    </tr>
    <tr>
      <th>Niobrara County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>27</td>
      <td>2484</td>
      <td>2484</td>
      <td>2492</td>
      <td>2485</td>
      <td>2475</td>
      <td>...</td>
      <td>-0.401849</td>
      <td>0.806452</td>
      <td>29.066295</td>
      <td>-12.603387</td>
      <td>7.492114</td>
      <td>-0.401849</td>
      <td>0.806452</td>
      <td>29.066295</td>
      <td>-12.603387</td>
      <td>7.492114</td>
    </tr>
    <tr>
      <th>Park County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>29</td>
      <td>28205</td>
      <td>28205</td>
      <td>28259</td>
      <td>28473</td>
      <td>28863</td>
      <td>...</td>
      <td>4.582951</td>
      <td>8.057765</td>
      <td>7.641997</td>
      <td>-9.252437</td>
      <td>-2.878980</td>
      <td>6.486639</td>
      <td>11.127389</td>
      <td>10.877797</td>
      <td>-5.585731</td>
      <td>0.856839</td>
    </tr>
    <tr>
      <th>Platte County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>31</td>
      <td>8667</td>
      <td>8667</td>
      <td>8678</td>
      <td>8701</td>
      <td>8732</td>
      <td>...</td>
      <td>4.373094</td>
      <td>5.392073</td>
      <td>2.634593</td>
      <td>6.055759</td>
      <td>4.662270</td>
      <td>4.373094</td>
      <td>4.933173</td>
      <td>2.176403</td>
      <td>5.598720</td>
      <td>4.207414</td>
    </tr>
    <tr>
      <th>Sheridan County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>33</td>
      <td>29116</td>
      <td>29116</td>
      <td>29146</td>
      <td>29275</td>
      <td>29594</td>
      <td>...</td>
      <td>0.958559</td>
      <td>8.425487</td>
      <td>4.546373</td>
      <td>3.678069</td>
      <td>-3.298406</td>
      <td>2.122524</td>
      <td>9.342778</td>
      <td>5.523001</td>
      <td>4.781489</td>
      <td>-2.198937</td>
    </tr>
    <tr>
      <th>Sublette County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>35</td>
      <td>10247</td>
      <td>10247</td>
      <td>10244</td>
      <td>10142</td>
      <td>10418</td>
      <td>...</td>
      <td>-23.741784</td>
      <td>15.272374</td>
      <td>-40.870074</td>
      <td>-16.596273</td>
      <td>-22.870900</td>
      <td>-21.092907</td>
      <td>16.828794</td>
      <td>-39.211861</td>
      <td>-14.409938</td>
      <td>-20.664059</td>
    </tr>
    <tr>
      <th>Sweetwater County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>37</td>
      <td>43806</td>
      <td>43806</td>
      <td>43593</td>
      <td>44041</td>
      <td>45104</td>
      <td>...</td>
      <td>1.072643</td>
      <td>16.243199</td>
      <td>-5.339774</td>
      <td>-14.252889</td>
      <td>-14.248864</td>
      <td>1.255221</td>
      <td>16.243199</td>
      <td>-5.295460</td>
      <td>-14.075283</td>
      <td>-14.070195</td>
    </tr>
    <tr>
      <th>Teton County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>39</td>
      <td>21294</td>
      <td>21294</td>
      <td>21297</td>
      <td>21482</td>
      <td>21697</td>
      <td>...</td>
      <td>-1.589565</td>
      <td>0.972695</td>
      <td>19.525929</td>
      <td>14.143021</td>
      <td>-0.564849</td>
      <td>0.654527</td>
      <td>2.408578</td>
      <td>21.160658</td>
      <td>16.308671</td>
      <td>1.520747</td>
    </tr>
    <tr>
      <th>Uinta County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>41</td>
      <td>21118</td>
      <td>21118</td>
      <td>21102</td>
      <td>20912</td>
      <td>20989</td>
      <td>...</td>
      <td>-17.755986</td>
      <td>-4.916350</td>
      <td>-6.902954</td>
      <td>-14.215862</td>
      <td>-12.127022</td>
      <td>-18.136812</td>
      <td>-5.536861</td>
      <td>-7.521840</td>
      <td>-14.740608</td>
      <td>-12.606351</td>
    </tr>
    <tr>
      <th>Washakie County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>43</td>
      <td>8533</td>
      <td>8533</td>
      <td>8545</td>
      <td>8469</td>
      <td>8443</td>
      <td>...</td>
      <td>-11.637475</td>
      <td>-0.827815</td>
      <td>-2.013502</td>
      <td>-17.781491</td>
      <td>1.682288</td>
      <td>-11.990126</td>
      <td>-1.182592</td>
      <td>-2.250385</td>
      <td>-18.020168</td>
      <td>1.441961</td>
    </tr>
    <tr>
      <th>Weston County</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>45</td>
      <td>7208</td>
      <td>7208</td>
      <td>7181</td>
      <td>7114</td>
      <td>7065</td>
      <td>...</td>
      <td>-11.752361</td>
      <td>-8.040059</td>
      <td>12.372583</td>
      <td>1.533635</td>
      <td>6.935294</td>
      <td>-12.032179</td>
      <td>-8.040059</td>
      <td>12.372583</td>
      <td>1.533635</td>
      <td>6.935294</td>
    </tr>
  </tbody>
</table>
<p>3142 rows × 98 columns</p>
</div>




```python
import numpy as np
def min_max(row):
    data = row[['POPESTIMATE2010',
                'POPESTIMATE2011',
                'POPESTIMATE2012',
                'POPESTIMATE2013',
                'POPESTIMATE2014',
                'POPESTIMATE2015']]
    return pd.Series({'min': np.min(data), 'max': np.max(data)})
```


```python
df.apply(min_max, axis=1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>max</th>
      <th>min</th>
    </tr>
    <tr>
      <th>STNAME</th>
      <th>CTYNAME</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="30" valign="top">Alabama</th>
      <th>Autauga County</th>
      <td>55347.0</td>
      <td>54660.0</td>
    </tr>
    <tr>
      <th>Baldwin County</th>
      <td>203709.0</td>
      <td>183193.0</td>
    </tr>
    <tr>
      <th>Barbour County</th>
      <td>27341.0</td>
      <td>26489.0</td>
    </tr>
    <tr>
      <th>Bibb County</th>
      <td>22861.0</td>
      <td>22512.0</td>
    </tr>
    <tr>
      <th>Blount County</th>
      <td>57776.0</td>
      <td>57373.0</td>
    </tr>
    <tr>
      <th>Bullock County</th>
      <td>10887.0</td>
      <td>10606.0</td>
    </tr>
    <tr>
      <th>Butler County</th>
      <td>20944.0</td>
      <td>20154.0</td>
    </tr>
    <tr>
      <th>Calhoun County</th>
      <td>118437.0</td>
      <td>115620.0</td>
    </tr>
    <tr>
      <th>Chambers County</th>
      <td>34153.0</td>
      <td>33993.0</td>
    </tr>
    <tr>
      <th>Cherokee County</th>
      <td>26084.0</td>
      <td>25859.0</td>
    </tr>
    <tr>
      <th>Chilton County</th>
      <td>43943.0</td>
      <td>43665.0</td>
    </tr>
    <tr>
      <th>Choctaw County</th>
      <td>13841.0</td>
      <td>13170.0</td>
    </tr>
    <tr>
      <th>Clarke County</th>
      <td>25767.0</td>
      <td>24675.0</td>
    </tr>
    <tr>
      <th>Clay County</th>
      <td>13880.0</td>
      <td>13456.0</td>
    </tr>
    <tr>
      <th>Cleburne County</th>
      <td>15072.0</td>
      <td>14921.0</td>
    </tr>
    <tr>
      <th>Coffee County</th>
      <td>51211.0</td>
      <td>50177.0</td>
    </tr>
    <tr>
      <th>Colbert County</th>
      <td>54514.0</td>
      <td>54354.0</td>
    </tr>
    <tr>
      <th>Conecuh County</th>
      <td>13208.0</td>
      <td>12662.0</td>
    </tr>
    <tr>
      <th>Coosa County</th>
      <td>11758.0</td>
      <td>10724.0</td>
    </tr>
    <tr>
      <th>Covington County</th>
      <td>38060.0</td>
      <td>37796.0</td>
    </tr>
    <tr>
      <th>Crenshaw County</th>
      <td>13963.0</td>
      <td>13853.0</td>
    </tr>
    <tr>
      <th>Cullman County</th>
      <td>82005.0</td>
      <td>80374.0</td>
    </tr>
    <tr>
      <th>Dale County</th>
      <td>50358.0</td>
      <td>49501.0</td>
    </tr>
    <tr>
      <th>Dallas County</th>
      <td>43803.0</td>
      <td>41131.0</td>
    </tr>
    <tr>
      <th>DeKalb County</th>
      <td>71387.0</td>
      <td>70869.0</td>
    </tr>
    <tr>
      <th>Elmore County</th>
      <td>81468.0</td>
      <td>79465.0</td>
    </tr>
    <tr>
      <th>Escambia County</th>
      <td>38309.0</td>
      <td>37784.0</td>
    </tr>
    <tr>
      <th>Etowah County</th>
      <td>104442.0</td>
      <td>103057.0</td>
    </tr>
    <tr>
      <th>Fayette County</th>
      <td>17231.0</td>
      <td>16759.0</td>
    </tr>
    <tr>
      <th>Franklin County</th>
      <td>31734.0</td>
      <td>31507.0</td>
    </tr>
    <tr>
      <th>...</th>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th rowspan="7" valign="top">Wisconsin</th>
      <th>Washburn County</th>
      <td>15930.0</td>
      <td>15552.0</td>
    </tr>
    <tr>
      <th>Washington County</th>
      <td>133674.0</td>
      <td>131967.0</td>
    </tr>
    <tr>
      <th>Waukesha County</th>
      <td>396488.0</td>
      <td>390076.0</td>
    </tr>
    <tr>
      <th>Waupaca County</th>
      <td>52422.0</td>
      <td>51945.0</td>
    </tr>
    <tr>
      <th>Waushara County</th>
      <td>24581.0</td>
      <td>24033.0</td>
    </tr>
    <tr>
      <th>Winnebago County</th>
      <td>169639.0</td>
      <td>167059.0</td>
    </tr>
    <tr>
      <th>Wood County</th>
      <td>74807.0</td>
      <td>73435.0</td>
    </tr>
    <tr>
      <th rowspan="23" valign="top">Wyoming</th>
      <th>Albany County</th>
      <td>37956.0</td>
      <td>36428.0</td>
    </tr>
    <tr>
      <th>Big Horn County</th>
      <td>12022.0</td>
      <td>11672.0</td>
    </tr>
    <tr>
      <th>Campbell County</th>
      <td>49220.0</td>
      <td>46244.0</td>
    </tr>
    <tr>
      <th>Carbon County</th>
      <td>15856.0</td>
      <td>15559.0</td>
    </tr>
    <tr>
      <th>Converse County</th>
      <td>14343.0</td>
      <td>13728.0</td>
    </tr>
    <tr>
      <th>Crook County</th>
      <td>7444.0</td>
      <td>7114.0</td>
    </tr>
    <tr>
      <th>Fremont County</th>
      <td>41129.0</td>
      <td>40222.0</td>
    </tr>
    <tr>
      <th>Goshen County</th>
      <td>13666.0</td>
      <td>13383.0</td>
    </tr>
    <tr>
      <th>Hot Springs County</th>
      <td>4846.0</td>
      <td>4741.0</td>
    </tr>
    <tr>
      <th>Johnson County</th>
      <td>8636.0</td>
      <td>8552.0</td>
    </tr>
    <tr>
      <th>Laramie County</th>
      <td>97121.0</td>
      <td>92271.0</td>
    </tr>
    <tr>
      <th>Lincoln County</th>
      <td>18722.0</td>
      <td>17943.0</td>
    </tr>
    <tr>
      <th>Natrona County</th>
      <td>82178.0</td>
      <td>75472.0</td>
    </tr>
    <tr>
      <th>Niobrara County</th>
      <td>2548.0</td>
      <td>2475.0</td>
    </tr>
    <tr>
      <th>Park County</th>
      <td>29237.0</td>
      <td>28259.0</td>
    </tr>
    <tr>
      <th>Platte County</th>
      <td>8812.0</td>
      <td>8678.0</td>
    </tr>
    <tr>
      <th>Sheridan County</th>
      <td>30020.0</td>
      <td>29146.0</td>
    </tr>
    <tr>
      <th>Sublette County</th>
      <td>10418.0</td>
      <td>9899.0</td>
    </tr>
    <tr>
      <th>Sweetwater County</th>
      <td>45162.0</td>
      <td>43593.0</td>
    </tr>
    <tr>
      <th>Teton County</th>
      <td>23125.0</td>
      <td>21297.0</td>
    </tr>
    <tr>
      <th>Uinta County</th>
      <td>21102.0</td>
      <td>20822.0</td>
    </tr>
    <tr>
      <th>Washakie County</th>
      <td>8545.0</td>
      <td>8316.0</td>
    </tr>
    <tr>
      <th>Weston County</th>
      <td>7234.0</td>
      <td>7065.0</td>
    </tr>
  </tbody>
</table>
<p>3142 rows × 2 columns</p>
</div>




```python
import numpy as np
def min_max(row):
    data = row[['POPESTIMATE2010',
                'POPESTIMATE2011',
                'POPESTIMATE2012',
                'POPESTIMATE2013',
                'POPESTIMATE2014',
                'POPESTIMATE2015']]
    row['max'] = np.max(data)
    row['min'] = np.min(data)
    return row
df.apply(min_max, axis=1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>SUMLEV</th>
      <th>REGION</th>
      <th>DIVISION</th>
      <th>STATE</th>
      <th>COUNTY</th>
      <th>CENSUS2010POP</th>
      <th>ESTIMATESBASE2010</th>
      <th>POPESTIMATE2010</th>
      <th>POPESTIMATE2011</th>
      <th>POPESTIMATE2012</th>
      <th>...</th>
      <th>RDOMESTICMIG2013</th>
      <th>RDOMESTICMIG2014</th>
      <th>RDOMESTICMIG2015</th>
      <th>RNETMIG2011</th>
      <th>RNETMIG2012</th>
      <th>RNETMIG2013</th>
      <th>RNETMIG2014</th>
      <th>RNETMIG2015</th>
      <th>max</th>
      <th>min</th>
    </tr>
    <tr>
      <th>STNAME</th>
      <th>CTYNAME</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="30" valign="top">Alabama</th>
      <th>Autauga County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>54571.0</td>
      <td>54571.0</td>
      <td>54660.0</td>
      <td>55253.0</td>
      <td>55175.0</td>
      <td>...</td>
      <td>-3.012349</td>
      <td>2.265971</td>
      <td>-2.530799</td>
      <td>7.606016</td>
      <td>-2.626146</td>
      <td>-2.722002</td>
      <td>2.592270</td>
      <td>-2.187333</td>
      <td>55347.0</td>
      <td>54660.0</td>
    </tr>
    <tr>
      <th>Baldwin County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>3.0</td>
      <td>182265.0</td>
      <td>182265.0</td>
      <td>183193.0</td>
      <td>186659.0</td>
      <td>190396.0</td>
      <td>...</td>
      <td>21.845705</td>
      <td>19.243287</td>
      <td>17.197872</td>
      <td>15.844176</td>
      <td>18.559627</td>
      <td>22.727626</td>
      <td>20.317142</td>
      <td>18.293499</td>
      <td>203709.0</td>
      <td>183193.0</td>
    </tr>
    <tr>
      <th>Barbour County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>5.0</td>
      <td>27457.0</td>
      <td>27457.0</td>
      <td>27341.0</td>
      <td>27226.0</td>
      <td>27159.0</td>
      <td>...</td>
      <td>-7.056824</td>
      <td>-3.904217</td>
      <td>-10.543299</td>
      <td>-4.874741</td>
      <td>-2.758113</td>
      <td>-7.167664</td>
      <td>-3.978583</td>
      <td>-10.543299</td>
      <td>27341.0</td>
      <td>26489.0</td>
    </tr>
    <tr>
      <th>Bibb County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>7.0</td>
      <td>22915.0</td>
      <td>22919.0</td>
      <td>22861.0</td>
      <td>22733.0</td>
      <td>22642.0</td>
      <td>...</td>
      <td>-6.201001</td>
      <td>-0.177537</td>
      <td>0.177258</td>
      <td>-5.088389</td>
      <td>-4.363636</td>
      <td>-5.403729</td>
      <td>0.754533</td>
      <td>1.107861</td>
      <td>22861.0</td>
      <td>22512.0</td>
    </tr>
    <tr>
      <th>Blount County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>9.0</td>
      <td>57322.0</td>
      <td>57322.0</td>
      <td>57373.0</td>
      <td>57711.0</td>
      <td>57776.0</td>
      <td>...</td>
      <td>-1.748766</td>
      <td>-2.062535</td>
      <td>-1.369970</td>
      <td>1.859511</td>
      <td>-0.848580</td>
      <td>-1.402476</td>
      <td>-1.577232</td>
      <td>-0.884411</td>
      <td>57776.0</td>
      <td>57373.0</td>
    </tr>
    <tr>
      <th>Bullock County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>11.0</td>
      <td>10914.0</td>
      <td>10915.0</td>
      <td>10887.0</td>
      <td>10629.0</td>
      <td>10606.0</td>
      <td>...</td>
      <td>-1.130263</td>
      <td>14.354290</td>
      <td>-16.167247</td>
      <td>-29.001673</td>
      <td>-2.825524</td>
      <td>1.507017</td>
      <td>17.243790</td>
      <td>-13.193961</td>
      <td>10887.0</td>
      <td>10606.0</td>
    </tr>
    <tr>
      <th>Butler County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>13.0</td>
      <td>20947.0</td>
      <td>20946.0</td>
      <td>20944.0</td>
      <td>20673.0</td>
      <td>20408.0</td>
      <td>...</td>
      <td>-5.655413</td>
      <td>1.085428</td>
      <td>-6.529805</td>
      <td>-13.936612</td>
      <td>-11.586865</td>
      <td>-5.557058</td>
      <td>1.184103</td>
      <td>-6.430868</td>
      <td>20944.0</td>
      <td>20154.0</td>
    </tr>
    <tr>
      <th>Calhoun County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>15.0</td>
      <td>118572.0</td>
      <td>118586.0</td>
      <td>118437.0</td>
      <td>117768.0</td>
      <td>117286.0</td>
      <td>...</td>
      <td>-5.524649</td>
      <td>-4.463211</td>
      <td>-3.376322</td>
      <td>-5.791579</td>
      <td>-4.092677</td>
      <td>-5.062836</td>
      <td>-3.912834</td>
      <td>-2.806406</td>
      <td>118437.0</td>
      <td>115620.0</td>
    </tr>
    <tr>
      <th>Chambers County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>17.0</td>
      <td>34215.0</td>
      <td>34170.0</td>
      <td>34098.0</td>
      <td>33993.0</td>
      <td>34075.0</td>
      <td>...</td>
      <td>2.872721</td>
      <td>-2.287222</td>
      <td>1.349468</td>
      <td>-1.821092</td>
      <td>4.701181</td>
      <td>3.781439</td>
      <td>-1.290228</td>
      <td>2.346901</td>
      <td>34153.0</td>
      <td>33993.0</td>
    </tr>
    <tr>
      <th>Cherokee County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>19.0</td>
      <td>25989.0</td>
      <td>25986.0</td>
      <td>25976.0</td>
      <td>26080.0</td>
      <td>26023.0</td>
      <td>...</td>
      <td>5.488706</td>
      <td>-0.076806</td>
      <td>-3.239866</td>
      <td>6.416167</td>
      <td>1.420264</td>
      <td>5.757384</td>
      <td>0.230419</td>
      <td>-2.931307</td>
      <td>26084.0</td>
      <td>25859.0</td>
    </tr>
    <tr>
      <th>Chilton County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>21.0</td>
      <td>43643.0</td>
      <td>43631.0</td>
      <td>43665.0</td>
      <td>43739.0</td>
      <td>43697.0</td>
      <td>...</td>
      <td>0.480044</td>
      <td>0.456017</td>
      <td>-2.253483</td>
      <td>-0.823761</td>
      <td>-2.447504</td>
      <td>0.868651</td>
      <td>0.957636</td>
      <td>-1.752709</td>
      <td>43943.0</td>
      <td>43665.0</td>
    </tr>
    <tr>
      <th>Choctaw County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>23.0</td>
      <td>13859.0</td>
      <td>13858.0</td>
      <td>13841.0</td>
      <td>13593.0</td>
      <td>13543.0</td>
      <td>...</td>
      <td>-8.766391</td>
      <td>-1.274984</td>
      <td>-5.291205</td>
      <td>-15.528177</td>
      <td>-0.737028</td>
      <td>-8.766391</td>
      <td>-1.274984</td>
      <td>-5.291205</td>
      <td>13841.0</td>
      <td>13170.0</td>
    </tr>
    <tr>
      <th>Clarke County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>25.0</td>
      <td>25833.0</td>
      <td>25840.0</td>
      <td>25767.0</td>
      <td>25570.0</td>
      <td>25144.0</td>
      <td>...</td>
      <td>-0.318345</td>
      <td>-8.686428</td>
      <td>-5.613667</td>
      <td>-6.077488</td>
      <td>-17.509958</td>
      <td>-0.159172</td>
      <td>-8.486280</td>
      <td>-5.411736</td>
      <td>25767.0</td>
      <td>24675.0</td>
    </tr>
    <tr>
      <th>Clay County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>27.0</td>
      <td>13932.0</td>
      <td>13932.0</td>
      <td>13880.0</td>
      <td>13670.0</td>
      <td>13456.0</td>
      <td>...</td>
      <td>4.902871</td>
      <td>5.702648</td>
      <td>3.912450</td>
      <td>-10.816697</td>
      <td>-13.345130</td>
      <td>4.977157</td>
      <td>5.776708</td>
      <td>3.986270</td>
      <td>13880.0</td>
      <td>13456.0</td>
    </tr>
    <tr>
      <th>Cleburne County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>29.0</td>
      <td>14972.0</td>
      <td>14972.0</td>
      <td>14973.0</td>
      <td>14971.0</td>
      <td>14921.0</td>
      <td>...</td>
      <td>7.345821</td>
      <td>3.654485</td>
      <td>-3.123961</td>
      <td>-3.673524</td>
      <td>-5.151880</td>
      <td>7.345821</td>
      <td>3.654485</td>
      <td>-3.123961</td>
      <td>15072.0</td>
      <td>14921.0</td>
    </tr>
    <tr>
      <th>Coffee County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>31.0</td>
      <td>49948.0</td>
      <td>49948.0</td>
      <td>50177.0</td>
      <td>50448.0</td>
      <td>51173.0</td>
      <td>...</td>
      <td>-13.146535</td>
      <td>-3.602859</td>
      <td>2.214774</td>
      <td>2.166460</td>
      <td>11.513368</td>
      <td>-10.438741</td>
      <td>-0.767822</td>
      <td>5.350738</td>
      <td>51211.0</td>
      <td>50177.0</td>
    </tr>
    <tr>
      <th>Colbert County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>33.0</td>
      <td>54428.0</td>
      <td>54428.0</td>
      <td>54514.0</td>
      <td>54443.0</td>
      <td>54472.0</td>
      <td>...</td>
      <td>1.762390</td>
      <td>1.835688</td>
      <td>-0.110260</td>
      <td>0.513964</td>
      <td>1.469035</td>
      <td>2.276420</td>
      <td>2.533249</td>
      <td>0.588052</td>
      <td>54514.0</td>
      <td>54354.0</td>
    </tr>
    <tr>
      <th>Conecuh County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>35.0</td>
      <td>13228.0</td>
      <td>13228.0</td>
      <td>13208.0</td>
      <td>13121.0</td>
      <td>12996.0</td>
      <td>...</td>
      <td>-6.107224</td>
      <td>-14.645416</td>
      <td>2.684140</td>
      <td>-4.861559</td>
      <td>-7.504690</td>
      <td>-6.107224</td>
      <td>-14.645416</td>
      <td>2.684140</td>
      <td>13208.0</td>
      <td>12662.0</td>
    </tr>
    <tr>
      <th>Coosa County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>37.0</td>
      <td>11539.0</td>
      <td>11758.0</td>
      <td>11758.0</td>
      <td>11348.0</td>
      <td>11195.0</td>
      <td>...</td>
      <td>-4.313831</td>
      <td>-22.958017</td>
      <td>-5.387581</td>
      <td>-34.017138</td>
      <td>-10.380162</td>
      <td>-4.403703</td>
      <td>-23.049483</td>
      <td>-5.387581</td>
      <td>11758.0</td>
      <td>10724.0</td>
    </tr>
    <tr>
      <th>Covington County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>39.0</td>
      <td>37765.0</td>
      <td>37765.0</td>
      <td>37796.0</td>
      <td>38060.0</td>
      <td>37818.0</td>
      <td>...</td>
      <td>0.740271</td>
      <td>3.697932</td>
      <td>-0.316945</td>
      <td>6.881460</td>
      <td>-4.559952</td>
      <td>0.793147</td>
      <td>3.750759</td>
      <td>-0.264121</td>
      <td>38060.0</td>
      <td>37796.0</td>
    </tr>
    <tr>
      <th>Crenshaw County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>41.0</td>
      <td>13906.0</td>
      <td>13906.0</td>
      <td>13853.0</td>
      <td>13896.0</td>
      <td>13951.0</td>
      <td>...</td>
      <td>-1.864936</td>
      <td>3.084648</td>
      <td>3.439504</td>
      <td>2.666763</td>
      <td>5.099293</td>
      <td>-0.502098</td>
      <td>4.734577</td>
      <td>5.087600</td>
      <td>13963.0</td>
      <td>13853.0</td>
    </tr>
    <tr>
      <th>Cullman County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>43.0</td>
      <td>80406.0</td>
      <td>80410.0</td>
      <td>80473.0</td>
      <td>80469.0</td>
      <td>80374.0</td>
      <td>...</td>
      <td>4.071247</td>
      <td>5.087142</td>
      <td>7.915406</td>
      <td>-1.031427</td>
      <td>-0.634159</td>
      <td>4.542916</td>
      <td>5.593387</td>
      <td>8.417777</td>
      <td>82005.0</td>
      <td>80374.0</td>
    </tr>
    <tr>
      <th>Dale County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>45.0</td>
      <td>50251.0</td>
      <td>50251.0</td>
      <td>50358.0</td>
      <td>50109.0</td>
      <td>50324.0</td>
      <td>...</td>
      <td>-15.236079</td>
      <td>-11.979785</td>
      <td>-5.107706</td>
      <td>-9.575283</td>
      <td>-0.776637</td>
      <td>-12.640155</td>
      <td>-9.503292</td>
      <td>-1.998668</td>
      <td>50358.0</td>
      <td>49501.0</td>
    </tr>
    <tr>
      <th>Dallas County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>47.0</td>
      <td>43820.0</td>
      <td>43820.0</td>
      <td>43803.0</td>
      <td>43178.0</td>
      <td>42777.0</td>
      <td>...</td>
      <td>-16.745678</td>
      <td>-9.344789</td>
      <td>-14.687232</td>
      <td>-15.727573</td>
      <td>-11.378047</td>
      <td>-16.792849</td>
      <td>-9.368689</td>
      <td>-14.711389</td>
      <td>43803.0</td>
      <td>41131.0</td>
    </tr>
    <tr>
      <th>DeKalb County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>49.0</td>
      <td>71109.0</td>
      <td>71115.0</td>
      <td>71142.0</td>
      <td>71387.0</td>
      <td>70942.0</td>
      <td>...</td>
      <td>-1.748807</td>
      <td>0.267830</td>
      <td>0.028141</td>
      <td>1.375159</td>
      <td>-8.656001</td>
      <td>-1.029539</td>
      <td>1.198187</td>
      <td>0.956790</td>
      <td>71387.0</td>
      <td>70869.0</td>
    </tr>
    <tr>
      <th>Elmore County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>51.0</td>
      <td>79303.0</td>
      <td>79296.0</td>
      <td>79465.0</td>
      <td>80012.0</td>
      <td>80432.0</td>
      <td>...</td>
      <td>1.760531</td>
      <td>-1.507057</td>
      <td>2.067820</td>
      <td>3.674511</td>
      <td>1.558176</td>
      <td>2.306047</td>
      <td>-0.951175</td>
      <td>2.757093</td>
      <td>81468.0</td>
      <td>79465.0</td>
    </tr>
    <tr>
      <th>Escambia County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>53.0</td>
      <td>38319.0</td>
      <td>38319.0</td>
      <td>38309.0</td>
      <td>38213.0</td>
      <td>38034.0</td>
      <td>...</td>
      <td>-4.822706</td>
      <td>-1.189831</td>
      <td>1.190902</td>
      <td>-3.397716</td>
      <td>-3.803428</td>
      <td>-4.769999</td>
      <td>-1.136950</td>
      <td>1.243830</td>
      <td>38309.0</td>
      <td>37784.0</td>
    </tr>
    <tr>
      <th>Etowah County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>55.0</td>
      <td>104430.0</td>
      <td>104427.0</td>
      <td>104442.0</td>
      <td>104236.0</td>
      <td>104235.0</td>
      <td>...</td>
      <td>-1.931884</td>
      <td>-1.726932</td>
      <td>-2.082234</td>
      <td>-0.632554</td>
      <td>2.446383</td>
      <td>-1.518596</td>
      <td>-1.234901</td>
      <td>-1.588308</td>
      <td>104442.0</td>
      <td>103057.0</td>
    </tr>
    <tr>
      <th>Fayette County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>57.0</td>
      <td>17241.0</td>
      <td>17241.0</td>
      <td>17231.0</td>
      <td>17062.0</td>
      <td>16960.0</td>
      <td>...</td>
      <td>-3.725937</td>
      <td>0.296745</td>
      <td>-2.797536</td>
      <td>-5.132243</td>
      <td>-0.705426</td>
      <td>-3.785079</td>
      <td>0.237396</td>
      <td>-2.857058</td>
      <td>17231.0</td>
      <td>16759.0</td>
    </tr>
    <tr>
      <th>Franklin County</th>
      <td>50.0</td>
      <td>3.0</td>
      <td>6.0</td>
      <td>1.0</td>
      <td>59.0</td>
      <td>31704.0</td>
      <td>31709.0</td>
      <td>31734.0</td>
      <td>31729.0</td>
      <td>31648.0</td>
      <td>...</td>
      <td>-8.043702</td>
      <td>-1.267849</td>
      <td>-2.401719</td>
      <td>0.063029</td>
      <td>-3.471291</td>
      <td>-5.700261</td>
      <td>1.553115</td>
      <td>0.442422</td>
      <td>31734.0</td>
      <td>31507.0</td>
    </tr>
    <tr>
      <th>...</th>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th rowspan="7" valign="top">Wisconsin</th>
      <th>Washburn County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>129.0</td>
      <td>15911.0</td>
      <td>15911.0</td>
      <td>15930.0</td>
      <td>15784.0</td>
      <td>15831.0</td>
      <td>...</td>
      <td>-6.732724</td>
      <td>3.510452</td>
      <td>-5.123279</td>
      <td>-6.747809</td>
      <td>7.464811</td>
      <td>-6.605691</td>
      <td>3.638104</td>
      <td>-4.995197</td>
      <td>15930.0</td>
      <td>15552.0</td>
    </tr>
    <tr>
      <th>Washington County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>131.0</td>
      <td>131887.0</td>
      <td>131885.0</td>
      <td>131967.0</td>
      <td>132225.0</td>
      <td>132649.0</td>
      <td>...</td>
      <td>-2.215465</td>
      <td>1.601149</td>
      <td>-0.434498</td>
      <td>-0.431504</td>
      <td>1.162817</td>
      <td>-1.763330</td>
      <td>2.104796</td>
      <td>0.059931</td>
      <td>133674.0</td>
      <td>131967.0</td>
    </tr>
    <tr>
      <th>Waukesha County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>133.0</td>
      <td>389891.0</td>
      <td>389938.0</td>
      <td>390076.0</td>
      <td>390808.0</td>
      <td>392710.0</td>
      <td>...</td>
      <td>0.038132</td>
      <td>0.760109</td>
      <td>-0.719858</td>
      <td>0.102448</td>
      <td>3.180527</td>
      <td>1.189727</td>
      <td>2.077633</td>
      <td>0.593567</td>
      <td>396488.0</td>
      <td>390076.0</td>
    </tr>
    <tr>
      <th>Waupaca County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>135.0</td>
      <td>52410.0</td>
      <td>52410.0</td>
      <td>52422.0</td>
      <td>52342.0</td>
      <td>52035.0</td>
      <td>...</td>
      <td>6.292687</td>
      <td>-0.441031</td>
      <td>-0.480617</td>
      <td>3.359933</td>
      <td>-2.011937</td>
      <td>6.561277</td>
      <td>-0.134227</td>
      <td>-0.173022</td>
      <td>52422.0</td>
      <td>51945.0</td>
    </tr>
    <tr>
      <th>Waushara County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>137.0</td>
      <td>24496.0</td>
      <td>24496.0</td>
      <td>24506.0</td>
      <td>24581.0</td>
      <td>24484.0</td>
      <td>...</td>
      <td>-4.097017</td>
      <td>-4.906711</td>
      <td>-4.397793</td>
      <td>5.174486</td>
      <td>-2.160399</td>
      <td>-3.810226</td>
      <td>-4.535615</td>
      <td>-4.024395</td>
      <td>24581.0</td>
      <td>24033.0</td>
    </tr>
    <tr>
      <th>Winnebago County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>139.0</td>
      <td>166994.0</td>
      <td>166994.0</td>
      <td>167059.0</td>
      <td>167630.0</td>
      <td>168717.0</td>
      <td>...</td>
      <td>0.833819</td>
      <td>-2.406192</td>
      <td>-4.557985</td>
      <td>0.842573</td>
      <td>3.502335</td>
      <td>1.531624</td>
      <td>-1.545153</td>
      <td>-3.685304</td>
      <td>169639.0</td>
      <td>167059.0</td>
    </tr>
    <tr>
      <th>Wood County</th>
      <td>50.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>55.0</td>
      <td>141.0</td>
      <td>74749.0</td>
      <td>74749.0</td>
      <td>74807.0</td>
      <td>74647.0</td>
      <td>74384.0</td>
      <td>...</td>
      <td>-6.901200</td>
      <td>-5.596471</td>
      <td>-3.958322</td>
      <td>-3.733590</td>
      <td>-4.562809</td>
      <td>-6.442917</td>
      <td>-5.040889</td>
      <td>-3.414223</td>
      <td>74807.0</td>
      <td>73435.0</td>
    </tr>
    <tr>
      <th rowspan="23" valign="top">Wyoming</th>
      <th>Albany County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>1.0</td>
      <td>36299.0</td>
      <td>36299.0</td>
      <td>36428.0</td>
      <td>36908.0</td>
      <td>37396.0</td>
      <td>...</td>
      <td>-3.544634</td>
      <td>-3.334877</td>
      <td>-9.911169</td>
      <td>6.736119</td>
      <td>6.433032</td>
      <td>0.719587</td>
      <td>1.429233</td>
      <td>-5.166460</td>
      <td>37956.0</td>
      <td>36428.0</td>
    </tr>
    <tr>
      <th>Big Horn County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>3.0</td>
      <td>11668.0</td>
      <td>11668.0</td>
      <td>11672.0</td>
      <td>11745.0</td>
      <td>11785.0</td>
      <td>...</td>
      <td>16.815908</td>
      <td>-8.026420</td>
      <td>5.095861</td>
      <td>4.868258</td>
      <td>3.144921</td>
      <td>17.236306</td>
      <td>-7.608378</td>
      <td>5.513554</td>
      <td>12022.0</td>
      <td>11672.0</td>
    </tr>
    <tr>
      <th>Campbell County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>5.0</td>
      <td>46133.0</td>
      <td>46133.0</td>
      <td>46244.0</td>
      <td>46600.0</td>
      <td>47881.0</td>
      <td>...</td>
      <td>-5.895711</td>
      <td>-8.550911</td>
      <td>10.916963</td>
      <td>-2.649606</td>
      <td>15.558684</td>
      <td>-5.916543</td>
      <td>-8.509402</td>
      <td>10.978525</td>
      <td>49220.0</td>
      <td>46244.0</td>
    </tr>
    <tr>
      <th>Carbon County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>7.0</td>
      <td>15885.0</td>
      <td>15885.0</td>
      <td>15837.0</td>
      <td>15817.0</td>
      <td>15678.0</td>
      <td>...</td>
      <td>3.178134</td>
      <td>-2.970641</td>
      <td>-23.300971</td>
      <td>-7.392431</td>
      <td>-12.636926</td>
      <td>3.623073</td>
      <td>-2.338590</td>
      <td>-22.600668</td>
      <td>15856.0</td>
      <td>15559.0</td>
    </tr>
    <tr>
      <th>Converse County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>9.0</td>
      <td>13833.0</td>
      <td>13833.0</td>
      <td>13826.0</td>
      <td>13728.0</td>
      <td>14025.0</td>
      <td>...</td>
      <td>19.035533</td>
      <td>-20.550587</td>
      <td>-0.070403</td>
      <td>-12.774915</td>
      <td>16.502720</td>
      <td>20.093063</td>
      <td>-19.358233</td>
      <td>1.126443</td>
      <td>14343.0</td>
      <td>13728.0</td>
    </tr>
    <tr>
      <th>Crook County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>11.0</td>
      <td>7083.0</td>
      <td>7083.0</td>
      <td>7114.0</td>
      <td>7129.0</td>
      <td>7148.0</td>
      <td>...</td>
      <td>1.397819</td>
      <td>6.378258</td>
      <td>18.629317</td>
      <td>-0.982939</td>
      <td>-3.642222</td>
      <td>2.096729</td>
      <td>7.071547</td>
      <td>19.309219</td>
      <td>7444.0</td>
      <td>7114.0</td>
    </tr>
    <tr>
      <th>Fremont County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>13.0</td>
      <td>40123.0</td>
      <td>40123.0</td>
      <td>40222.0</td>
      <td>40591.0</td>
      <td>41129.0</td>
      <td>...</td>
      <td>-4.990688</td>
      <td>-12.331633</td>
      <td>-13.673610</td>
      <td>3.093562</td>
      <td>8.027411</td>
      <td>-4.747240</td>
      <td>-12.013555</td>
      <td>-13.352750</td>
      <td>41129.0</td>
      <td>40222.0</td>
    </tr>
    <tr>
      <th>Goshen County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>15.0</td>
      <td>13249.0</td>
      <td>13247.0</td>
      <td>13408.0</td>
      <td>13597.0</td>
      <td>13666.0</td>
      <td>...</td>
      <td>-8.079028</td>
      <td>-7.017803</td>
      <td>-11.899450</td>
      <td>14.886132</td>
      <td>4.841727</td>
      <td>-6.903896</td>
      <td>-5.761986</td>
      <td>-10.635133</td>
      <td>13666.0</td>
      <td>13383.0</td>
    </tr>
    <tr>
      <th>Hot Springs County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>17.0</td>
      <td>4812.0</td>
      <td>4812.0</td>
      <td>4813.0</td>
      <td>4818.0</td>
      <td>4846.0</td>
      <td>...</td>
      <td>3.095336</td>
      <td>-6.017222</td>
      <td>-5.454164</td>
      <td>5.191569</td>
      <td>6.001656</td>
      <td>2.888981</td>
      <td>-6.224712</td>
      <td>-5.663940</td>
      <td>4846.0</td>
      <td>4741.0</td>
    </tr>
    <tr>
      <th>Johnson County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>19.0</td>
      <td>8569.0</td>
      <td>8569.0</td>
      <td>8581.0</td>
      <td>8636.0</td>
      <td>8610.0</td>
      <td>...</td>
      <td>-0.812583</td>
      <td>-10.715742</td>
      <td>0.933652</td>
      <td>5.227392</td>
      <td>-4.058912</td>
      <td>-0.812583</td>
      <td>-10.715742</td>
      <td>0.933652</td>
      <td>8636.0</td>
      <td>8552.0</td>
    </tr>
    <tr>
      <th>Laramie County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>21.0</td>
      <td>91738.0</td>
      <td>91881.0</td>
      <td>92271.0</td>
      <td>92663.0</td>
      <td>94894.0</td>
      <td>...</td>
      <td>4.787847</td>
      <td>-1.226133</td>
      <td>0.278940</td>
      <td>-0.973320</td>
      <td>17.914554</td>
      <td>6.003143</td>
      <td>-0.207819</td>
      <td>1.673640</td>
      <td>97121.0</td>
      <td>92271.0</td>
    </tr>
    <tr>
      <th>Lincoln County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>23.0</td>
      <td>18106.0</td>
      <td>18106.0</td>
      <td>18091.0</td>
      <td>18022.0</td>
      <td>17943.0</td>
      <td>...</td>
      <td>13.564556</td>
      <td>6.125989</td>
      <td>1.555544</td>
      <td>-9.691801</td>
      <td>-11.566801</td>
      <td>13.619696</td>
      <td>6.234414</td>
      <td>1.662823</td>
      <td>18722.0</td>
      <td>17943.0</td>
    </tr>
    <tr>
      <th>Natrona County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>25.0</td>
      <td>75450.0</td>
      <td>75450.0</td>
      <td>75472.0</td>
      <td>76420.0</td>
      <td>78699.0</td>
      <td>...</td>
      <td>24.322042</td>
      <td>-0.958472</td>
      <td>-0.061057</td>
      <td>7.689674</td>
      <td>23.749508</td>
      <td>25.085233</td>
      <td>-0.110593</td>
      <td>0.793743</td>
      <td>82178.0</td>
      <td>75472.0</td>
    </tr>
    <tr>
      <th>Niobrara County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>27.0</td>
      <td>2484.0</td>
      <td>2484.0</td>
      <td>2492.0</td>
      <td>2485.0</td>
      <td>2475.0</td>
      <td>...</td>
      <td>29.066295</td>
      <td>-12.603387</td>
      <td>7.492114</td>
      <td>-0.401849</td>
      <td>0.806452</td>
      <td>29.066295</td>
      <td>-12.603387</td>
      <td>7.492114</td>
      <td>2548.0</td>
      <td>2475.0</td>
    </tr>
    <tr>
      <th>Park County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>29.0</td>
      <td>28205.0</td>
      <td>28205.0</td>
      <td>28259.0</td>
      <td>28473.0</td>
      <td>28863.0</td>
      <td>...</td>
      <td>7.641997</td>
      <td>-9.252437</td>
      <td>-2.878980</td>
      <td>6.486639</td>
      <td>11.127389</td>
      <td>10.877797</td>
      <td>-5.585731</td>
      <td>0.856839</td>
      <td>29237.0</td>
      <td>28259.0</td>
    </tr>
    <tr>
      <th>Platte County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>31.0</td>
      <td>8667.0</td>
      <td>8667.0</td>
      <td>8678.0</td>
      <td>8701.0</td>
      <td>8732.0</td>
      <td>...</td>
      <td>2.634593</td>
      <td>6.055759</td>
      <td>4.662270</td>
      <td>4.373094</td>
      <td>4.933173</td>
      <td>2.176403</td>
      <td>5.598720</td>
      <td>4.207414</td>
      <td>8812.0</td>
      <td>8678.0</td>
    </tr>
    <tr>
      <th>Sheridan County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>33.0</td>
      <td>29116.0</td>
      <td>29116.0</td>
      <td>29146.0</td>
      <td>29275.0</td>
      <td>29594.0</td>
      <td>...</td>
      <td>4.546373</td>
      <td>3.678069</td>
      <td>-3.298406</td>
      <td>2.122524</td>
      <td>9.342778</td>
      <td>5.523001</td>
      <td>4.781489</td>
      <td>-2.198937</td>
      <td>30020.0</td>
      <td>29146.0</td>
    </tr>
    <tr>
      <th>Sublette County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>35.0</td>
      <td>10247.0</td>
      <td>10247.0</td>
      <td>10244.0</td>
      <td>10142.0</td>
      <td>10418.0</td>
      <td>...</td>
      <td>-40.870074</td>
      <td>-16.596273</td>
      <td>-22.870900</td>
      <td>-21.092907</td>
      <td>16.828794</td>
      <td>-39.211861</td>
      <td>-14.409938</td>
      <td>-20.664059</td>
      <td>10418.0</td>
      <td>9899.0</td>
    </tr>
    <tr>
      <th>Sweetwater County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>37.0</td>
      <td>43806.0</td>
      <td>43806.0</td>
      <td>43593.0</td>
      <td>44041.0</td>
      <td>45104.0</td>
      <td>...</td>
      <td>-5.339774</td>
      <td>-14.252889</td>
      <td>-14.248864</td>
      <td>1.255221</td>
      <td>16.243199</td>
      <td>-5.295460</td>
      <td>-14.075283</td>
      <td>-14.070195</td>
      <td>45162.0</td>
      <td>43593.0</td>
    </tr>
    <tr>
      <th>Teton County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>39.0</td>
      <td>21294.0</td>
      <td>21294.0</td>
      <td>21297.0</td>
      <td>21482.0</td>
      <td>21697.0</td>
      <td>...</td>
      <td>19.525929</td>
      <td>14.143021</td>
      <td>-0.564849</td>
      <td>0.654527</td>
      <td>2.408578</td>
      <td>21.160658</td>
      <td>16.308671</td>
      <td>1.520747</td>
      <td>23125.0</td>
      <td>21297.0</td>
    </tr>
    <tr>
      <th>Uinta County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>41.0</td>
      <td>21118.0</td>
      <td>21118.0</td>
      <td>21102.0</td>
      <td>20912.0</td>
      <td>20989.0</td>
      <td>...</td>
      <td>-6.902954</td>
      <td>-14.215862</td>
      <td>-12.127022</td>
      <td>-18.136812</td>
      <td>-5.536861</td>
      <td>-7.521840</td>
      <td>-14.740608</td>
      <td>-12.606351</td>
      <td>21102.0</td>
      <td>20822.0</td>
    </tr>
    <tr>
      <th>Washakie County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>43.0</td>
      <td>8533.0</td>
      <td>8533.0</td>
      <td>8545.0</td>
      <td>8469.0</td>
      <td>8443.0</td>
      <td>...</td>
      <td>-2.013502</td>
      <td>-17.781491</td>
      <td>1.682288</td>
      <td>-11.990126</td>
      <td>-1.182592</td>
      <td>-2.250385</td>
      <td>-18.020168</td>
      <td>1.441961</td>
      <td>8545.0</td>
      <td>8316.0</td>
    </tr>
    <tr>
      <th>Weston County</th>
      <td>50.0</td>
      <td>4.0</td>
      <td>8.0</td>
      <td>56.0</td>
      <td>45.0</td>
      <td>7208.0</td>
      <td>7208.0</td>
      <td>7181.0</td>
      <td>7114.0</td>
      <td>7065.0</td>
      <td>...</td>
      <td>12.372583</td>
      <td>1.533635</td>
      <td>6.935294</td>
      <td>-12.032179</td>
      <td>-8.040059</td>
      <td>12.372583</td>
      <td>1.533635</td>
      <td>6.935294</td>
      <td>7234.0</td>
      <td>7065.0</td>
    </tr>
  </tbody>
</table>
<p>3142 rows × 100 columns</p>
</div>




```python
rows = ['POPESTIMATE2010',
        'POPESTIMATE2011',
        'POPESTIMATE2012',
        'POPESTIMATE2013',
        'POPESTIMATE2014',
        'POPESTIMATE2015']
df.apply(lambda x: np.max(x[rows]), axis=1)
```




    STNAME     CTYNAME           
    Alabama    Autauga County         55347.0
               Baldwin County        203709.0
               Barbour County         27341.0
               Bibb County            22861.0
               Blount County          57776.0
               Bullock County         10887.0
               Butler County          20944.0
               Calhoun County        118437.0
               Chambers County        34153.0
               Cherokee County        26084.0
               Chilton County         43943.0
               Choctaw County         13841.0
               Clarke County          25767.0
               Clay County            13880.0
               Cleburne County        15072.0
               Coffee County          51211.0
               Colbert County         54514.0
               Conecuh County         13208.0
               Coosa County           11758.0
               Covington County       38060.0
               Crenshaw County        13963.0
               Cullman County         82005.0
               Dale County            50358.0
               Dallas County          43803.0
               DeKalb County          71387.0
               Elmore County          81468.0
               Escambia County        38309.0
               Etowah County         104442.0
               Fayette County         17231.0
               Franklin County        31734.0
                                       ...   
    Wisconsin  Washburn County        15930.0
               Washington County     133674.0
               Waukesha County       396488.0
               Waupaca County         52422.0
               Waushara County        24581.0
               Winnebago County      169639.0
               Wood County            74807.0
    Wyoming    Albany County          37956.0
               Big Horn County        12022.0
               Campbell County        49220.0
               Carbon County          15856.0
               Converse County        14343.0
               Crook County            7444.0
               Fremont County         41129.0
               Goshen County          13666.0
               Hot Springs County      4846.0
               Johnson County          8636.0
               Laramie County         97121.0
               Lincoln County         18722.0
               Natrona County         82178.0
               Niobrara County         2548.0
               Park County            29237.0
               Platte County           8812.0
               Sheridan County        30020.0
               Sublette County        10418.0
               Sweetwater County      45162.0
               Teton County           23125.0
               Uinta County           21102.0
               Washakie County         8545.0
               Weston County           7234.0
    dtype: float64



# Group by


```python
import pandas as pd
import numpy as np
df = pd.read_csv('census.csv')
df = df[df['SUMLEV']==50]
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SUMLEV</th>
      <th>REGION</th>
      <th>DIVISION</th>
      <th>STATE</th>
      <th>COUNTY</th>
      <th>STNAME</th>
      <th>CTYNAME</th>
      <th>CENSUS2010POP</th>
      <th>ESTIMATESBASE2010</th>
      <th>POPESTIMATE2010</th>
      <th>...</th>
      <th>RDOMESTICMIG2011</th>
      <th>RDOMESTICMIG2012</th>
      <th>RDOMESTICMIG2013</th>
      <th>RDOMESTICMIG2014</th>
      <th>RDOMESTICMIG2015</th>
      <th>RNETMIG2011</th>
      <th>RNETMIG2012</th>
      <th>RNETMIG2013</th>
      <th>RNETMIG2014</th>
      <th>RNETMIG2015</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>1</td>
      <td>Alabama</td>
      <td>Autauga County</td>
      <td>54571</td>
      <td>54571</td>
      <td>54660</td>
      <td>...</td>
      <td>7.242091</td>
      <td>-2.915927</td>
      <td>-3.012349</td>
      <td>2.265971</td>
      <td>-2.530799</td>
      <td>7.606016</td>
      <td>-2.626146</td>
      <td>-2.722002</td>
      <td>2.592270</td>
      <td>-2.187333</td>
    </tr>
    <tr>
      <th>2</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>3</td>
      <td>Alabama</td>
      <td>Baldwin County</td>
      <td>182265</td>
      <td>182265</td>
      <td>183193</td>
      <td>...</td>
      <td>14.832960</td>
      <td>17.647293</td>
      <td>21.845705</td>
      <td>19.243287</td>
      <td>17.197872</td>
      <td>15.844176</td>
      <td>18.559627</td>
      <td>22.727626</td>
      <td>20.317142</td>
      <td>18.293499</td>
    </tr>
    <tr>
      <th>3</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>5</td>
      <td>Alabama</td>
      <td>Barbour County</td>
      <td>27457</td>
      <td>27457</td>
      <td>27341</td>
      <td>...</td>
      <td>-4.728132</td>
      <td>-2.500690</td>
      <td>-7.056824</td>
      <td>-3.904217</td>
      <td>-10.543299</td>
      <td>-4.874741</td>
      <td>-2.758113</td>
      <td>-7.167664</td>
      <td>-3.978583</td>
      <td>-10.543299</td>
    </tr>
    <tr>
      <th>4</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>7</td>
      <td>Alabama</td>
      <td>Bibb County</td>
      <td>22915</td>
      <td>22919</td>
      <td>22861</td>
      <td>...</td>
      <td>-5.527043</td>
      <td>-5.068871</td>
      <td>-6.201001</td>
      <td>-0.177537</td>
      <td>0.177258</td>
      <td>-5.088389</td>
      <td>-4.363636</td>
      <td>-5.403729</td>
      <td>0.754533</td>
      <td>1.107861</td>
    </tr>
    <tr>
      <th>5</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>9</td>
      <td>Alabama</td>
      <td>Blount County</td>
      <td>57322</td>
      <td>57322</td>
      <td>57373</td>
      <td>...</td>
      <td>1.807375</td>
      <td>-1.177622</td>
      <td>-1.748766</td>
      <td>-2.062535</td>
      <td>-1.369970</td>
      <td>1.859511</td>
      <td>-0.848580</td>
      <td>-1.402476</td>
      <td>-1.577232</td>
      <td>-0.884411</td>
    </tr>
    <tr>
      <th>6</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>11</td>
      <td>Alabama</td>
      <td>Bullock County</td>
      <td>10914</td>
      <td>10915</td>
      <td>10887</td>
      <td>...</td>
      <td>-30.953709</td>
      <td>-5.180127</td>
      <td>-1.130263</td>
      <td>14.354290</td>
      <td>-16.167247</td>
      <td>-29.001673</td>
      <td>-2.825524</td>
      <td>1.507017</td>
      <td>17.243790</td>
      <td>-13.193961</td>
    </tr>
    <tr>
      <th>7</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>13</td>
      <td>Alabama</td>
      <td>Butler County</td>
      <td>20947</td>
      <td>20946</td>
      <td>20944</td>
      <td>...</td>
      <td>-14.032727</td>
      <td>-11.684234</td>
      <td>-5.655413</td>
      <td>1.085428</td>
      <td>-6.529805</td>
      <td>-13.936612</td>
      <td>-11.586865</td>
      <td>-5.557058</td>
      <td>1.184103</td>
      <td>-6.430868</td>
    </tr>
    <tr>
      <th>8</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>15</td>
      <td>Alabama</td>
      <td>Calhoun County</td>
      <td>118572</td>
      <td>118586</td>
      <td>118437</td>
      <td>...</td>
      <td>-6.155670</td>
      <td>-4.611706</td>
      <td>-5.524649</td>
      <td>-4.463211</td>
      <td>-3.376322</td>
      <td>-5.791579</td>
      <td>-4.092677</td>
      <td>-5.062836</td>
      <td>-3.912834</td>
      <td>-2.806406</td>
    </tr>
    <tr>
      <th>9</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>17</td>
      <td>Alabama</td>
      <td>Chambers County</td>
      <td>34215</td>
      <td>34170</td>
      <td>34098</td>
      <td>...</td>
      <td>-2.731639</td>
      <td>3.849092</td>
      <td>2.872721</td>
      <td>-2.287222</td>
      <td>1.349468</td>
      <td>-1.821092</td>
      <td>4.701181</td>
      <td>3.781439</td>
      <td>-1.290228</td>
      <td>2.346901</td>
    </tr>
    <tr>
      <th>10</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>19</td>
      <td>Alabama</td>
      <td>Cherokee County</td>
      <td>25989</td>
      <td>25986</td>
      <td>25976</td>
      <td>...</td>
      <td>6.339327</td>
      <td>1.113180</td>
      <td>5.488706</td>
      <td>-0.076806</td>
      <td>-3.239866</td>
      <td>6.416167</td>
      <td>1.420264</td>
      <td>5.757384</td>
      <td>0.230419</td>
      <td>-2.931307</td>
    </tr>
    <tr>
      <th>11</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>21</td>
      <td>Alabama</td>
      <td>Chilton County</td>
      <td>43643</td>
      <td>43631</td>
      <td>43665</td>
      <td>...</td>
      <td>-1.372935</td>
      <td>-2.653369</td>
      <td>0.480044</td>
      <td>0.456017</td>
      <td>-2.253483</td>
      <td>-0.823761</td>
      <td>-2.447504</td>
      <td>0.868651</td>
      <td>0.957636</td>
      <td>-1.752709</td>
    </tr>
    <tr>
      <th>12</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>23</td>
      <td>Alabama</td>
      <td>Choctaw County</td>
      <td>13859</td>
      <td>13858</td>
      <td>13841</td>
      <td>...</td>
      <td>-15.455274</td>
      <td>-0.737028</td>
      <td>-8.766391</td>
      <td>-1.274984</td>
      <td>-5.291205</td>
      <td>-15.528177</td>
      <td>-0.737028</td>
      <td>-8.766391</td>
      <td>-1.274984</td>
      <td>-5.291205</td>
    </tr>
    <tr>
      <th>13</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>25</td>
      <td>Alabama</td>
      <td>Clarke County</td>
      <td>25833</td>
      <td>25840</td>
      <td>25767</td>
      <td>...</td>
      <td>-6.194363</td>
      <td>-17.667705</td>
      <td>-0.318345</td>
      <td>-8.686428</td>
      <td>-5.613667</td>
      <td>-6.077488</td>
      <td>-17.509958</td>
      <td>-0.159172</td>
      <td>-8.486280</td>
      <td>-5.411736</td>
    </tr>
    <tr>
      <th>14</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>27</td>
      <td>Alabama</td>
      <td>Clay County</td>
      <td>13932</td>
      <td>13932</td>
      <td>13880</td>
      <td>...</td>
      <td>-10.744102</td>
      <td>-13.345130</td>
      <td>4.902871</td>
      <td>5.702648</td>
      <td>3.912450</td>
      <td>-10.816697</td>
      <td>-13.345130</td>
      <td>4.977157</td>
      <td>5.776708</td>
      <td>3.986270</td>
    </tr>
    <tr>
      <th>15</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>29</td>
      <td>Alabama</td>
      <td>Cleburne County</td>
      <td>14972</td>
      <td>14972</td>
      <td>14973</td>
      <td>...</td>
      <td>-3.673524</td>
      <td>-5.151880</td>
      <td>7.345821</td>
      <td>3.654485</td>
      <td>-3.123961</td>
      <td>-3.673524</td>
      <td>-5.151880</td>
      <td>7.345821</td>
      <td>3.654485</td>
      <td>-3.123961</td>
    </tr>
    <tr>
      <th>16</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>31</td>
      <td>Alabama</td>
      <td>Coffee County</td>
      <td>49948</td>
      <td>49948</td>
      <td>50177</td>
      <td>...</td>
      <td>0.377640</td>
      <td>7.675579</td>
      <td>-13.146535</td>
      <td>-3.602859</td>
      <td>2.214774</td>
      <td>2.166460</td>
      <td>11.513368</td>
      <td>-10.438741</td>
      <td>-0.767822</td>
      <td>5.350738</td>
    </tr>
    <tr>
      <th>17</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>33</td>
      <td>Alabama</td>
      <td>Colbert County</td>
      <td>54428</td>
      <td>54428</td>
      <td>54514</td>
      <td>...</td>
      <td>-0.073423</td>
      <td>1.065051</td>
      <td>1.762390</td>
      <td>1.835688</td>
      <td>-0.110260</td>
      <td>0.513964</td>
      <td>1.469035</td>
      <td>2.276420</td>
      <td>2.533249</td>
      <td>0.588052</td>
    </tr>
    <tr>
      <th>18</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>35</td>
      <td>Alabama</td>
      <td>Conecuh County</td>
      <td>13228</td>
      <td>13228</td>
      <td>13208</td>
      <td>...</td>
      <td>-4.861559</td>
      <td>-7.504690</td>
      <td>-6.107224</td>
      <td>-14.645416</td>
      <td>2.684140</td>
      <td>-4.861559</td>
      <td>-7.504690</td>
      <td>-6.107224</td>
      <td>-14.645416</td>
      <td>2.684140</td>
    </tr>
    <tr>
      <th>19</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>37</td>
      <td>Alabama</td>
      <td>Coosa County</td>
      <td>11539</td>
      <td>11758</td>
      <td>11758</td>
      <td>...</td>
      <td>-33.930581</td>
      <td>-10.291443</td>
      <td>-4.313831</td>
      <td>-22.958017</td>
      <td>-5.387581</td>
      <td>-34.017138</td>
      <td>-10.380162</td>
      <td>-4.403703</td>
      <td>-23.049483</td>
      <td>-5.387581</td>
    </tr>
    <tr>
      <th>20</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>39</td>
      <td>Alabama</td>
      <td>Covington County</td>
      <td>37765</td>
      <td>37765</td>
      <td>37796</td>
      <td>...</td>
      <td>6.696899</td>
      <td>-4.612668</td>
      <td>0.740271</td>
      <td>3.697932</td>
      <td>-0.316945</td>
      <td>6.881460</td>
      <td>-4.559952</td>
      <td>0.793147</td>
      <td>3.750759</td>
      <td>-0.264121</td>
    </tr>
    <tr>
      <th>21</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>41</td>
      <td>Alabama</td>
      <td>Crenshaw County</td>
      <td>13906</td>
      <td>13906</td>
      <td>13853</td>
      <td>...</td>
      <td>1.729792</td>
      <td>3.950156</td>
      <td>-1.864936</td>
      <td>3.084648</td>
      <td>3.439504</td>
      <td>2.666763</td>
      <td>5.099293</td>
      <td>-0.502098</td>
      <td>4.734577</td>
      <td>5.087600</td>
    </tr>
    <tr>
      <th>22</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>43</td>
      <td>Alabama</td>
      <td>Cullman County</td>
      <td>80406</td>
      <td>80410</td>
      <td>80473</td>
      <td>...</td>
      <td>-1.404233</td>
      <td>-1.019628</td>
      <td>4.071247</td>
      <td>5.087142</td>
      <td>7.915406</td>
      <td>-1.031427</td>
      <td>-0.634159</td>
      <td>4.542916</td>
      <td>5.593387</td>
      <td>8.417777</td>
    </tr>
    <tr>
      <th>23</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>45</td>
      <td>Alabama</td>
      <td>Dale County</td>
      <td>50251</td>
      <td>50251</td>
      <td>50358</td>
      <td>...</td>
      <td>-10.749798</td>
      <td>-5.277150</td>
      <td>-15.236079</td>
      <td>-11.979785</td>
      <td>-5.107706</td>
      <td>-9.575283</td>
      <td>-0.776637</td>
      <td>-12.640155</td>
      <td>-9.503292</td>
      <td>-1.998668</td>
    </tr>
    <tr>
      <th>24</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>47</td>
      <td>Alabama</td>
      <td>Dallas County</td>
      <td>43820</td>
      <td>43820</td>
      <td>43803</td>
      <td>...</td>
      <td>-15.635599</td>
      <td>-11.308243</td>
      <td>-16.745678</td>
      <td>-9.344789</td>
      <td>-14.687232</td>
      <td>-15.727573</td>
      <td>-11.378047</td>
      <td>-16.792849</td>
      <td>-9.368689</td>
      <td>-14.711389</td>
    </tr>
    <tr>
      <th>25</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>49</td>
      <td>Alabama</td>
      <td>DeKalb County</td>
      <td>71109</td>
      <td>71115</td>
      <td>71142</td>
      <td>...</td>
      <td>0.294677</td>
      <td>-9.302391</td>
      <td>-1.748807</td>
      <td>0.267830</td>
      <td>0.028141</td>
      <td>1.375159</td>
      <td>-8.656001</td>
      <td>-1.029539</td>
      <td>1.198187</td>
      <td>0.956790</td>
    </tr>
    <tr>
      <th>26</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>51</td>
      <td>Alabama</td>
      <td>Elmore County</td>
      <td>79303</td>
      <td>79296</td>
      <td>79465</td>
      <td>...</td>
      <td>3.235576</td>
      <td>0.822717</td>
      <td>1.760531</td>
      <td>-1.507057</td>
      <td>2.067820</td>
      <td>3.674511</td>
      <td>1.558176</td>
      <td>2.306047</td>
      <td>-0.951175</td>
      <td>2.757093</td>
    </tr>
    <tr>
      <th>27</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>53</td>
      <td>Alabama</td>
      <td>Escambia County</td>
      <td>38319</td>
      <td>38319</td>
      <td>38309</td>
      <td>...</td>
      <td>-3.449988</td>
      <td>-3.855889</td>
      <td>-4.822706</td>
      <td>-1.189831</td>
      <td>1.190902</td>
      <td>-3.397716</td>
      <td>-3.803428</td>
      <td>-4.769999</td>
      <td>-1.136950</td>
      <td>1.243830</td>
    </tr>
    <tr>
      <th>28</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>55</td>
      <td>Alabama</td>
      <td>Etowah County</td>
      <td>104430</td>
      <td>104427</td>
      <td>104442</td>
      <td>...</td>
      <td>-1.015919</td>
      <td>2.062637</td>
      <td>-1.931884</td>
      <td>-1.726932</td>
      <td>-2.082234</td>
      <td>-0.632554</td>
      <td>2.446383</td>
      <td>-1.518596</td>
      <td>-1.234901</td>
      <td>-1.588308</td>
    </tr>
    <tr>
      <th>29</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>57</td>
      <td>Alabama</td>
      <td>Fayette County</td>
      <td>17241</td>
      <td>17241</td>
      <td>17231</td>
      <td>...</td>
      <td>-5.015601</td>
      <td>-0.646640</td>
      <td>-3.725937</td>
      <td>0.296745</td>
      <td>-2.797536</td>
      <td>-5.132243</td>
      <td>-0.705426</td>
      <td>-3.785079</td>
      <td>0.237396</td>
      <td>-2.857058</td>
    </tr>
    <tr>
      <th>30</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>59</td>
      <td>Alabama</td>
      <td>Franklin County</td>
      <td>31704</td>
      <td>31709</td>
      <td>31734</td>
      <td>...</td>
      <td>-1.638750</td>
      <td>-5.459394</td>
      <td>-8.043702</td>
      <td>-1.267849</td>
      <td>-2.401719</td>
      <td>0.063029</td>
      <td>-3.471291</td>
      <td>-5.700261</td>
      <td>1.553115</td>
      <td>0.442422</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>3162</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>129</td>
      <td>Wisconsin</td>
      <td>Washburn County</td>
      <td>15911</td>
      <td>15911</td>
      <td>15930</td>
      <td>...</td>
      <td>-6.873936</td>
      <td>7.338289</td>
      <td>-6.732724</td>
      <td>3.510452</td>
      <td>-5.123279</td>
      <td>-6.747809</td>
      <td>7.464811</td>
      <td>-6.605691</td>
      <td>3.638104</td>
      <td>-4.995197</td>
    </tr>
    <tr>
      <th>3163</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>131</td>
      <td>Wisconsin</td>
      <td>Washington County</td>
      <td>131887</td>
      <td>131885</td>
      <td>131967</td>
      <td>...</td>
      <td>-0.794876</td>
      <td>0.785279</td>
      <td>-2.215465</td>
      <td>1.601149</td>
      <td>-0.434498</td>
      <td>-0.431504</td>
      <td>1.162817</td>
      <td>-1.763330</td>
      <td>2.104796</td>
      <td>0.059931</td>
    </tr>
    <tr>
      <th>3164</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>133</td>
      <td>Wisconsin</td>
      <td>Waukesha County</td>
      <td>389891</td>
      <td>389938</td>
      <td>390076</td>
      <td>...</td>
      <td>-0.765799</td>
      <td>2.128860</td>
      <td>0.038132</td>
      <td>0.760109</td>
      <td>-0.719858</td>
      <td>0.102448</td>
      <td>3.180527</td>
      <td>1.189727</td>
      <td>2.077633</td>
      <td>0.593567</td>
    </tr>
    <tr>
      <th>3165</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>135</td>
      <td>Wisconsin</td>
      <td>Waupaca County</td>
      <td>52410</td>
      <td>52410</td>
      <td>52422</td>
      <td>...</td>
      <td>3.111756</td>
      <td>-2.241873</td>
      <td>6.292687</td>
      <td>-0.441031</td>
      <td>-0.480617</td>
      <td>3.359933</td>
      <td>-2.011937</td>
      <td>6.561277</td>
      <td>-0.134227</td>
      <td>-0.173022</td>
    </tr>
    <tr>
      <th>3166</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>137</td>
      <td>Wisconsin</td>
      <td>Waushara County</td>
      <td>24496</td>
      <td>24496</td>
      <td>24506</td>
      <td>...</td>
      <td>4.930022</td>
      <td>-2.404973</td>
      <td>-4.097017</td>
      <td>-4.906711</td>
      <td>-4.397793</td>
      <td>5.174486</td>
      <td>-2.160399</td>
      <td>-3.810226</td>
      <td>-4.535615</td>
      <td>-4.024395</td>
    </tr>
    <tr>
      <th>3167</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>139</td>
      <td>Wisconsin</td>
      <td>Winnebago County</td>
      <td>166994</td>
      <td>166994</td>
      <td>167059</td>
      <td>...</td>
      <td>0.316712</td>
      <td>2.889873</td>
      <td>0.833819</td>
      <td>-2.406192</td>
      <td>-4.557985</td>
      <td>0.842573</td>
      <td>3.502335</td>
      <td>1.531624</td>
      <td>-1.545153</td>
      <td>-3.685304</td>
    </tr>
    <tr>
      <th>3168</th>
      <td>50</td>
      <td>2</td>
      <td>3</td>
      <td>55</td>
      <td>141</td>
      <td>Wisconsin</td>
      <td>Wood County</td>
      <td>74749</td>
      <td>74749</td>
      <td>74807</td>
      <td>...</td>
      <td>-4.081523</td>
      <td>-5.019090</td>
      <td>-6.901200</td>
      <td>-5.596471</td>
      <td>-3.958322</td>
      <td>-3.733590</td>
      <td>-4.562809</td>
      <td>-6.442917</td>
      <td>-5.040889</td>
      <td>-3.414223</td>
    </tr>
    <tr>
      <th>3170</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>1</td>
      <td>Wyoming</td>
      <td>Albany County</td>
      <td>36299</td>
      <td>36299</td>
      <td>36428</td>
      <td>...</td>
      <td>3.708956</td>
      <td>2.637812</td>
      <td>-3.544634</td>
      <td>-3.334877</td>
      <td>-9.911169</td>
      <td>6.736119</td>
      <td>6.433032</td>
      <td>0.719587</td>
      <td>1.429233</td>
      <td>-5.166460</td>
    </tr>
    <tr>
      <th>3171</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>3</td>
      <td>Wyoming</td>
      <td>Big Horn County</td>
      <td>11668</td>
      <td>11668</td>
      <td>11672</td>
      <td>...</td>
      <td>4.868258</td>
      <td>2.804930</td>
      <td>16.815908</td>
      <td>-8.026420</td>
      <td>5.095861</td>
      <td>4.868258</td>
      <td>3.144921</td>
      <td>17.236306</td>
      <td>-7.608378</td>
      <td>5.513554</td>
    </tr>
    <tr>
      <th>3172</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>5</td>
      <td>Wyoming</td>
      <td>Campbell County</td>
      <td>46133</td>
      <td>46133</td>
      <td>46244</td>
      <td>...</td>
      <td>-2.843479</td>
      <td>15.601020</td>
      <td>-5.895711</td>
      <td>-8.550911</td>
      <td>10.916963</td>
      <td>-2.649606</td>
      <td>15.558684</td>
      <td>-5.916543</td>
      <td>-8.509402</td>
      <td>10.978525</td>
    </tr>
    <tr>
      <th>3173</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>7</td>
      <td>Wyoming</td>
      <td>Carbon County</td>
      <td>15885</td>
      <td>15885</td>
      <td>15837</td>
      <td>...</td>
      <td>-7.581980</td>
      <td>-13.081441</td>
      <td>3.178134</td>
      <td>-2.970641</td>
      <td>-23.300971</td>
      <td>-7.392431</td>
      <td>-12.636926</td>
      <td>3.623073</td>
      <td>-2.338590</td>
      <td>-22.600668</td>
    </tr>
    <tr>
      <th>3174</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>9</td>
      <td>Wyoming</td>
      <td>Converse County</td>
      <td>13833</td>
      <td>13833</td>
      <td>13826</td>
      <td>...</td>
      <td>-12.847499</td>
      <td>15.493820</td>
      <td>19.035533</td>
      <td>-20.550587</td>
      <td>-0.070403</td>
      <td>-12.774915</td>
      <td>16.502720</td>
      <td>20.093063</td>
      <td>-19.358233</td>
      <td>1.126443</td>
    </tr>
    <tr>
      <th>3175</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>11</td>
      <td>Wyoming</td>
      <td>Crook County</td>
      <td>7083</td>
      <td>7083</td>
      <td>7114</td>
      <td>...</td>
      <td>-1.544618</td>
      <td>-4.202564</td>
      <td>1.397819</td>
      <td>6.378258</td>
      <td>18.629317</td>
      <td>-0.982939</td>
      <td>-3.642222</td>
      <td>2.096729</td>
      <td>7.071547</td>
      <td>19.309219</td>
    </tr>
    <tr>
      <th>3176</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>13</td>
      <td>Wyoming</td>
      <td>Fremont County</td>
      <td>40123</td>
      <td>40123</td>
      <td>40222</td>
      <td>...</td>
      <td>2.747083</td>
      <td>7.782673</td>
      <td>-4.990688</td>
      <td>-12.331633</td>
      <td>-13.673610</td>
      <td>3.093562</td>
      <td>8.027411</td>
      <td>-4.747240</td>
      <td>-12.013555</td>
      <td>-13.352750</td>
    </tr>
    <tr>
      <th>3177</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>15</td>
      <td>Wyoming</td>
      <td>Goshen County</td>
      <td>13249</td>
      <td>13247</td>
      <td>13408</td>
      <td>...</td>
      <td>14.293649</td>
      <td>3.961413</td>
      <td>-8.079028</td>
      <td>-7.017803</td>
      <td>-11.899450</td>
      <td>14.886132</td>
      <td>4.841727</td>
      <td>-6.903896</td>
      <td>-5.761986</td>
      <td>-10.635133</td>
    </tr>
    <tr>
      <th>3178</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>17</td>
      <td>Wyoming</td>
      <td>Hot Springs County</td>
      <td>4812</td>
      <td>4812</td>
      <td>4813</td>
      <td>...</td>
      <td>3.322604</td>
      <td>6.208609</td>
      <td>3.095336</td>
      <td>-6.017222</td>
      <td>-5.454164</td>
      <td>5.191569</td>
      <td>6.001656</td>
      <td>2.888981</td>
      <td>-6.224712</td>
      <td>-5.663940</td>
    </tr>
    <tr>
      <th>3179</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>19</td>
      <td>Wyoming</td>
      <td>Johnson County</td>
      <td>8569</td>
      <td>8569</td>
      <td>8581</td>
      <td>...</td>
      <td>4.995063</td>
      <td>-4.058912</td>
      <td>-0.812583</td>
      <td>-10.715742</td>
      <td>0.933652</td>
      <td>5.227392</td>
      <td>-4.058912</td>
      <td>-0.812583</td>
      <td>-10.715742</td>
      <td>0.933652</td>
    </tr>
    <tr>
      <th>3180</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>21</td>
      <td>Wyoming</td>
      <td>Laramie County</td>
      <td>91738</td>
      <td>91881</td>
      <td>92271</td>
      <td>...</td>
      <td>-1.200428</td>
      <td>15.547274</td>
      <td>4.787847</td>
      <td>-1.226133</td>
      <td>0.278940</td>
      <td>-0.973320</td>
      <td>17.914554</td>
      <td>6.003143</td>
      <td>-0.207819</td>
      <td>1.673640</td>
    </tr>
    <tr>
      <th>3181</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>23</td>
      <td>Wyoming</td>
      <td>Lincoln County</td>
      <td>18106</td>
      <td>18106</td>
      <td>18091</td>
      <td>...</td>
      <td>-9.802564</td>
      <td>-11.566801</td>
      <td>13.564556</td>
      <td>6.125989</td>
      <td>1.555544</td>
      <td>-9.691801</td>
      <td>-11.566801</td>
      <td>13.619696</td>
      <td>6.234414</td>
      <td>1.662823</td>
    </tr>
    <tr>
      <th>3182</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>25</td>
      <td>Wyoming</td>
      <td>Natrona County</td>
      <td>75450</td>
      <td>75450</td>
      <td>75472</td>
      <td>...</td>
      <td>7.189319</td>
      <td>23.066162</td>
      <td>24.322042</td>
      <td>-0.958472</td>
      <td>-0.061057</td>
      <td>7.689674</td>
      <td>23.749508</td>
      <td>25.085233</td>
      <td>-0.110593</td>
      <td>0.793743</td>
    </tr>
    <tr>
      <th>3183</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>27</td>
      <td>Wyoming</td>
      <td>Niobrara County</td>
      <td>2484</td>
      <td>2484</td>
      <td>2492</td>
      <td>...</td>
      <td>-0.401849</td>
      <td>0.806452</td>
      <td>29.066295</td>
      <td>-12.603387</td>
      <td>7.492114</td>
      <td>-0.401849</td>
      <td>0.806452</td>
      <td>29.066295</td>
      <td>-12.603387</td>
      <td>7.492114</td>
    </tr>
    <tr>
      <th>3184</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>29</td>
      <td>Wyoming</td>
      <td>Park County</td>
      <td>28205</td>
      <td>28205</td>
      <td>28259</td>
      <td>...</td>
      <td>4.582951</td>
      <td>8.057765</td>
      <td>7.641997</td>
      <td>-9.252437</td>
      <td>-2.878980</td>
      <td>6.486639</td>
      <td>11.127389</td>
      <td>10.877797</td>
      <td>-5.585731</td>
      <td>0.856839</td>
    </tr>
    <tr>
      <th>3185</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>31</td>
      <td>Wyoming</td>
      <td>Platte County</td>
      <td>8667</td>
      <td>8667</td>
      <td>8678</td>
      <td>...</td>
      <td>4.373094</td>
      <td>5.392073</td>
      <td>2.634593</td>
      <td>6.055759</td>
      <td>4.662270</td>
      <td>4.373094</td>
      <td>4.933173</td>
      <td>2.176403</td>
      <td>5.598720</td>
      <td>4.207414</td>
    </tr>
    <tr>
      <th>3186</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>33</td>
      <td>Wyoming</td>
      <td>Sheridan County</td>
      <td>29116</td>
      <td>29116</td>
      <td>29146</td>
      <td>...</td>
      <td>0.958559</td>
      <td>8.425487</td>
      <td>4.546373</td>
      <td>3.678069</td>
      <td>-3.298406</td>
      <td>2.122524</td>
      <td>9.342778</td>
      <td>5.523001</td>
      <td>4.781489</td>
      <td>-2.198937</td>
    </tr>
    <tr>
      <th>3187</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>35</td>
      <td>Wyoming</td>
      <td>Sublette County</td>
      <td>10247</td>
      <td>10247</td>
      <td>10244</td>
      <td>...</td>
      <td>-23.741784</td>
      <td>15.272374</td>
      <td>-40.870074</td>
      <td>-16.596273</td>
      <td>-22.870900</td>
      <td>-21.092907</td>
      <td>16.828794</td>
      <td>-39.211861</td>
      <td>-14.409938</td>
      <td>-20.664059</td>
    </tr>
    <tr>
      <th>3188</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>37</td>
      <td>Wyoming</td>
      <td>Sweetwater County</td>
      <td>43806</td>
      <td>43806</td>
      <td>43593</td>
      <td>...</td>
      <td>1.072643</td>
      <td>16.243199</td>
      <td>-5.339774</td>
      <td>-14.252889</td>
      <td>-14.248864</td>
      <td>1.255221</td>
      <td>16.243199</td>
      <td>-5.295460</td>
      <td>-14.075283</td>
      <td>-14.070195</td>
    </tr>
    <tr>
      <th>3189</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>39</td>
      <td>Wyoming</td>
      <td>Teton County</td>
      <td>21294</td>
      <td>21294</td>
      <td>21297</td>
      <td>...</td>
      <td>-1.589565</td>
      <td>0.972695</td>
      <td>19.525929</td>
      <td>14.143021</td>
      <td>-0.564849</td>
      <td>0.654527</td>
      <td>2.408578</td>
      <td>21.160658</td>
      <td>16.308671</td>
      <td>1.520747</td>
    </tr>
    <tr>
      <th>3190</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>41</td>
      <td>Wyoming</td>
      <td>Uinta County</td>
      <td>21118</td>
      <td>21118</td>
      <td>21102</td>
      <td>...</td>
      <td>-17.755986</td>
      <td>-4.916350</td>
      <td>-6.902954</td>
      <td>-14.215862</td>
      <td>-12.127022</td>
      <td>-18.136812</td>
      <td>-5.536861</td>
      <td>-7.521840</td>
      <td>-14.740608</td>
      <td>-12.606351</td>
    </tr>
    <tr>
      <th>3191</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>43</td>
      <td>Wyoming</td>
      <td>Washakie County</td>
      <td>8533</td>
      <td>8533</td>
      <td>8545</td>
      <td>...</td>
      <td>-11.637475</td>
      <td>-0.827815</td>
      <td>-2.013502</td>
      <td>-17.781491</td>
      <td>1.682288</td>
      <td>-11.990126</td>
      <td>-1.182592</td>
      <td>-2.250385</td>
      <td>-18.020168</td>
      <td>1.441961</td>
    </tr>
    <tr>
      <th>3192</th>
      <td>50</td>
      <td>4</td>
      <td>8</td>
      <td>56</td>
      <td>45</td>
      <td>Wyoming</td>
      <td>Weston County</td>
      <td>7208</td>
      <td>7208</td>
      <td>7181</td>
      <td>...</td>
      <td>-11.752361</td>
      <td>-8.040059</td>
      <td>12.372583</td>
      <td>1.533635</td>
      <td>6.935294</td>
      <td>-12.032179</td>
      <td>-8.040059</td>
      <td>12.372583</td>
      <td>1.533635</td>
      <td>6.935294</td>
    </tr>
  </tbody>
</table>
<p>3142 rows × 100 columns</p>
</div>




```python
%%timeit -n 10
for state in df['STNAME'].unique():
    avg = np.average(df.where(df['STNAME']==state).dropna()['CENSUS2010POP'])
    print('Counties in state ' + state + ' have an average population of ' + str(avg))
```

    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    10 loops, best of 3: 1.31 s per loop



```python
%%timeit -n 10
for group, frame in df.groupby('STNAME'):
    avg = np.average(frame['CENSUS2010POP'])
    print('Counties in state ' + group + ' have an average population of ' + str(avg))
```

    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    Counties in state Alabama have an average population of 71339.3432836
    Counties in state Alaska have an average population of 24490.7241379
    Counties in state Arizona have an average population of 426134.466667
    Counties in state Arkansas have an average population of 38878.9066667
    Counties in state California have an average population of 642309.586207
    Counties in state Colorado have an average population of 78581.1875
    Counties in state Connecticut have an average population of 446762.125
    Counties in state Delaware have an average population of 299311.333333
    Counties in state District of Columbia have an average population of 601723.0
    Counties in state Florida have an average population of 280616.567164
    Counties in state Georgia have an average population of 60928.6352201
    Counties in state Hawaii have an average population of 272060.2
    Counties in state Idaho have an average population of 35626.8636364
    Counties in state Illinois have an average population of 125790.509804
    Counties in state Indiana have an average population of 70476.1086957
    Counties in state Iowa have an average population of 30771.2626263
    Counties in state Kansas have an average population of 27172.552381
    Counties in state Kentucky have an average population of 36161.3916667
    Counties in state Louisiana have an average population of 70833.9375
    Counties in state Maine have an average population of 83022.5625
    Counties in state Maryland have an average population of 240564.666667
    Counties in state Massachusetts have an average population of 467687.785714
    Counties in state Michigan have an average population of 119080.0
    Counties in state Minnesota have an average population of 60964.6551724
    Counties in state Mississippi have an average population of 36186.5487805
    Counties in state Missouri have an average population of 52077.626087
    Counties in state Montana have an average population of 17668.125
    Counties in state Nebraska have an average population of 19638.0752688
    Counties in state Nevada have an average population of 158855.941176
    Counties in state New Hampshire have an average population of 131647.0
    Counties in state New Jersey have an average population of 418661.619048
    Counties in state New Mexico have an average population of 62399.3636364
    Counties in state New York have an average population of 312550.032258
    Counties in state North Carolina have an average population of 95354.83
    Counties in state North Dakota have an average population of 12690.3962264
    Counties in state Ohio have an average population of 131096.636364
    Counties in state Oklahoma have an average population of 48718.8441558
    Counties in state Oregon have an average population of 106418.722222
    Counties in state Pennsylvania have an average population of 189587.746269
    Counties in state Rhode Island have an average population of 210513.4
    Counties in state South Carolina have an average population of 100551.391304
    Counties in state South Dakota have an average population of 12336.0606061
    Counties in state Tennessee have an average population of 66801.1052632
    Counties in state Texas have an average population of 98998.2716535
    Counties in state Utah have an average population of 95306.3793103
    Counties in state Vermont have an average population of 44695.7857143
    Counties in state Virginia have an average population of 60111.2932331
    Counties in state Washington have an average population of 172424.102564
    Counties in state West Virginia have an average population of 33690.8
    Counties in state Wisconsin have an average population of 78985.9166667
    Counties in state Wyoming have an average population of 24505.4782609
    10 loops, best of 3: 39.7 ms per loop



```python
df.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SUMLEV</th>
      <th>REGION</th>
      <th>DIVISION</th>
      <th>STATE</th>
      <th>COUNTY</th>
      <th>STNAME</th>
      <th>CTYNAME</th>
      <th>CENSUS2010POP</th>
      <th>ESTIMATESBASE2010</th>
      <th>POPESTIMATE2010</th>
      <th>...</th>
      <th>RDOMESTICMIG2011</th>
      <th>RDOMESTICMIG2012</th>
      <th>RDOMESTICMIG2013</th>
      <th>RDOMESTICMIG2014</th>
      <th>RDOMESTICMIG2015</th>
      <th>RNETMIG2011</th>
      <th>RNETMIG2012</th>
      <th>RNETMIG2013</th>
      <th>RNETMIG2014</th>
      <th>RNETMIG2015</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>1</td>
      <td>Alabama</td>
      <td>Autauga County</td>
      <td>54571</td>
      <td>54571</td>
      <td>54660</td>
      <td>...</td>
      <td>7.242091</td>
      <td>-2.915927</td>
      <td>-3.012349</td>
      <td>2.265971</td>
      <td>-2.530799</td>
      <td>7.606016</td>
      <td>-2.626146</td>
      <td>-2.722002</td>
      <td>2.592270</td>
      <td>-2.187333</td>
    </tr>
    <tr>
      <th>2</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>3</td>
      <td>Alabama</td>
      <td>Baldwin County</td>
      <td>182265</td>
      <td>182265</td>
      <td>183193</td>
      <td>...</td>
      <td>14.832960</td>
      <td>17.647293</td>
      <td>21.845705</td>
      <td>19.243287</td>
      <td>17.197872</td>
      <td>15.844176</td>
      <td>18.559627</td>
      <td>22.727626</td>
      <td>20.317142</td>
      <td>18.293499</td>
    </tr>
    <tr>
      <th>3</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>5</td>
      <td>Alabama</td>
      <td>Barbour County</td>
      <td>27457</td>
      <td>27457</td>
      <td>27341</td>
      <td>...</td>
      <td>-4.728132</td>
      <td>-2.500690</td>
      <td>-7.056824</td>
      <td>-3.904217</td>
      <td>-10.543299</td>
      <td>-4.874741</td>
      <td>-2.758113</td>
      <td>-7.167664</td>
      <td>-3.978583</td>
      <td>-10.543299</td>
    </tr>
    <tr>
      <th>4</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>7</td>
      <td>Alabama</td>
      <td>Bibb County</td>
      <td>22915</td>
      <td>22919</td>
      <td>22861</td>
      <td>...</td>
      <td>-5.527043</td>
      <td>-5.068871</td>
      <td>-6.201001</td>
      <td>-0.177537</td>
      <td>0.177258</td>
      <td>-5.088389</td>
      <td>-4.363636</td>
      <td>-5.403729</td>
      <td>0.754533</td>
      <td>1.107861</td>
    </tr>
    <tr>
      <th>5</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>9</td>
      <td>Alabama</td>
      <td>Blount County</td>
      <td>57322</td>
      <td>57322</td>
      <td>57373</td>
      <td>...</td>
      <td>1.807375</td>
      <td>-1.177622</td>
      <td>-1.748766</td>
      <td>-2.062535</td>
      <td>-1.369970</td>
      <td>1.859511</td>
      <td>-0.848580</td>
      <td>-1.402476</td>
      <td>-1.577232</td>
      <td>-0.884411</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 100 columns</p>
</div>




```python
df = df.set_index('STNAME')

def fun(item):
    if item[0]<'M':
        return 0
    if item[0]<'Q':
        return 1
    return 2

for group, frame in df.groupby(fun):
    print('There are ' + str(len(frame)) + ' records in group ' + str(group) + ' for processing.')

```

    There are 1177 records in group 0 for processing.
    There are 1134 records in group 1 for processing.
    There are 831 records in group 2 for processing.



```python
df = pd.read_csv('census.csv')
df = df[df['SUMLEV']==50]
```


```python
df.groupby('STNAME').agg({'CENSUS2010POP': np.average})
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CENSUS2010POP</th>
    </tr>
    <tr>
      <th>STNAME</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Alabama</th>
      <td>71339.343284</td>
    </tr>
    <tr>
      <th>Alaska</th>
      <td>24490.724138</td>
    </tr>
    <tr>
      <th>Arizona</th>
      <td>426134.466667</td>
    </tr>
    <tr>
      <th>Arkansas</th>
      <td>38878.906667</td>
    </tr>
    <tr>
      <th>California</th>
      <td>642309.586207</td>
    </tr>
    <tr>
      <th>Colorado</th>
      <td>78581.187500</td>
    </tr>
    <tr>
      <th>Connecticut</th>
      <td>446762.125000</td>
    </tr>
    <tr>
      <th>Delaware</th>
      <td>299311.333333</td>
    </tr>
    <tr>
      <th>District of Columbia</th>
      <td>601723.000000</td>
    </tr>
    <tr>
      <th>Florida</th>
      <td>280616.567164</td>
    </tr>
    <tr>
      <th>Georgia</th>
      <td>60928.635220</td>
    </tr>
    <tr>
      <th>Hawaii</th>
      <td>272060.200000</td>
    </tr>
    <tr>
      <th>Idaho</th>
      <td>35626.863636</td>
    </tr>
    <tr>
      <th>Illinois</th>
      <td>125790.509804</td>
    </tr>
    <tr>
      <th>Indiana</th>
      <td>70476.108696</td>
    </tr>
    <tr>
      <th>Iowa</th>
      <td>30771.262626</td>
    </tr>
    <tr>
      <th>Kansas</th>
      <td>27172.552381</td>
    </tr>
    <tr>
      <th>Kentucky</th>
      <td>36161.391667</td>
    </tr>
    <tr>
      <th>Louisiana</th>
      <td>70833.937500</td>
    </tr>
    <tr>
      <th>Maine</th>
      <td>83022.562500</td>
    </tr>
    <tr>
      <th>Maryland</th>
      <td>240564.666667</td>
    </tr>
    <tr>
      <th>Massachusetts</th>
      <td>467687.785714</td>
    </tr>
    <tr>
      <th>Michigan</th>
      <td>119080.000000</td>
    </tr>
    <tr>
      <th>Minnesota</th>
      <td>60964.655172</td>
    </tr>
    <tr>
      <th>Mississippi</th>
      <td>36186.548780</td>
    </tr>
    <tr>
      <th>Missouri</th>
      <td>52077.626087</td>
    </tr>
    <tr>
      <th>Montana</th>
      <td>17668.125000</td>
    </tr>
    <tr>
      <th>Nebraska</th>
      <td>19638.075269</td>
    </tr>
    <tr>
      <th>Nevada</th>
      <td>158855.941176</td>
    </tr>
    <tr>
      <th>New Hampshire</th>
      <td>131647.000000</td>
    </tr>
    <tr>
      <th>New Jersey</th>
      <td>418661.619048</td>
    </tr>
    <tr>
      <th>New Mexico</th>
      <td>62399.363636</td>
    </tr>
    <tr>
      <th>New York</th>
      <td>312550.032258</td>
    </tr>
    <tr>
      <th>North Carolina</th>
      <td>95354.830000</td>
    </tr>
    <tr>
      <th>North Dakota</th>
      <td>12690.396226</td>
    </tr>
    <tr>
      <th>Ohio</th>
      <td>131096.636364</td>
    </tr>
    <tr>
      <th>Oklahoma</th>
      <td>48718.844156</td>
    </tr>
    <tr>
      <th>Oregon</th>
      <td>106418.722222</td>
    </tr>
    <tr>
      <th>Pennsylvania</th>
      <td>189587.746269</td>
    </tr>
    <tr>
      <th>Rhode Island</th>
      <td>210513.400000</td>
    </tr>
    <tr>
      <th>South Carolina</th>
      <td>100551.391304</td>
    </tr>
    <tr>
      <th>South Dakota</th>
      <td>12336.060606</td>
    </tr>
    <tr>
      <th>Tennessee</th>
      <td>66801.105263</td>
    </tr>
    <tr>
      <th>Texas</th>
      <td>98998.271654</td>
    </tr>
    <tr>
      <th>Utah</th>
      <td>95306.379310</td>
    </tr>
    <tr>
      <th>Vermont</th>
      <td>44695.785714</td>
    </tr>
    <tr>
      <th>Virginia</th>
      <td>60111.293233</td>
    </tr>
    <tr>
      <th>Washington</th>
      <td>172424.102564</td>
    </tr>
    <tr>
      <th>West Virginia</th>
      <td>33690.800000</td>
    </tr>
    <tr>
      <th>Wisconsin</th>
      <td>78985.916667</td>
    </tr>
    <tr>
      <th>Wyoming</th>
      <td>24505.478261</td>
    </tr>
  </tbody>
</table>
</div>




```python
print(type(df.groupby(level=0)['POPESTIMATE2010','POPESTIMATE2011']))
print(type(df.groupby(level=0)['POPESTIMATE2010']))
```

    <class 'pandas.core.groupby.DataFrameGroupBy'>
    <class 'pandas.core.groupby.SeriesGroupBy'>



```python
(df.set_index('STNAME').groupby(level=0)['CENSUS2010POP']
    .agg({'avg': np.average, 'sum': np.sum}))
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>avg</th>
      <th>sum</th>
    </tr>
    <tr>
      <th>STNAME</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Alabama</th>
      <td>71339.343284</td>
      <td>4779736</td>
    </tr>
    <tr>
      <th>Alaska</th>
      <td>24490.724138</td>
      <td>710231</td>
    </tr>
    <tr>
      <th>Arizona</th>
      <td>426134.466667</td>
      <td>6392017</td>
    </tr>
    <tr>
      <th>Arkansas</th>
      <td>38878.906667</td>
      <td>2915918</td>
    </tr>
    <tr>
      <th>California</th>
      <td>642309.586207</td>
      <td>37253956</td>
    </tr>
    <tr>
      <th>Colorado</th>
      <td>78581.187500</td>
      <td>5029196</td>
    </tr>
    <tr>
      <th>Connecticut</th>
      <td>446762.125000</td>
      <td>3574097</td>
    </tr>
    <tr>
      <th>Delaware</th>
      <td>299311.333333</td>
      <td>897934</td>
    </tr>
    <tr>
      <th>District of Columbia</th>
      <td>601723.000000</td>
      <td>601723</td>
    </tr>
    <tr>
      <th>Florida</th>
      <td>280616.567164</td>
      <td>18801310</td>
    </tr>
    <tr>
      <th>Georgia</th>
      <td>60928.635220</td>
      <td>9687653</td>
    </tr>
    <tr>
      <th>Hawaii</th>
      <td>272060.200000</td>
      <td>1360301</td>
    </tr>
    <tr>
      <th>Idaho</th>
      <td>35626.863636</td>
      <td>1567582</td>
    </tr>
    <tr>
      <th>Illinois</th>
      <td>125790.509804</td>
      <td>12830632</td>
    </tr>
    <tr>
      <th>Indiana</th>
      <td>70476.108696</td>
      <td>6483802</td>
    </tr>
    <tr>
      <th>Iowa</th>
      <td>30771.262626</td>
      <td>3046355</td>
    </tr>
    <tr>
      <th>Kansas</th>
      <td>27172.552381</td>
      <td>2853118</td>
    </tr>
    <tr>
      <th>Kentucky</th>
      <td>36161.391667</td>
      <td>4339367</td>
    </tr>
    <tr>
      <th>Louisiana</th>
      <td>70833.937500</td>
      <td>4533372</td>
    </tr>
    <tr>
      <th>Maine</th>
      <td>83022.562500</td>
      <td>1328361</td>
    </tr>
    <tr>
      <th>Maryland</th>
      <td>240564.666667</td>
      <td>5773552</td>
    </tr>
    <tr>
      <th>Massachusetts</th>
      <td>467687.785714</td>
      <td>6547629</td>
    </tr>
    <tr>
      <th>Michigan</th>
      <td>119080.000000</td>
      <td>9883640</td>
    </tr>
    <tr>
      <th>Minnesota</th>
      <td>60964.655172</td>
      <td>5303925</td>
    </tr>
    <tr>
      <th>Mississippi</th>
      <td>36186.548780</td>
      <td>2967297</td>
    </tr>
    <tr>
      <th>Missouri</th>
      <td>52077.626087</td>
      <td>5988927</td>
    </tr>
    <tr>
      <th>Montana</th>
      <td>17668.125000</td>
      <td>989415</td>
    </tr>
    <tr>
      <th>Nebraska</th>
      <td>19638.075269</td>
      <td>1826341</td>
    </tr>
    <tr>
      <th>Nevada</th>
      <td>158855.941176</td>
      <td>2700551</td>
    </tr>
    <tr>
      <th>New Hampshire</th>
      <td>131647.000000</td>
      <td>1316470</td>
    </tr>
    <tr>
      <th>New Jersey</th>
      <td>418661.619048</td>
      <td>8791894</td>
    </tr>
    <tr>
      <th>New Mexico</th>
      <td>62399.363636</td>
      <td>2059179</td>
    </tr>
    <tr>
      <th>New York</th>
      <td>312550.032258</td>
      <td>19378102</td>
    </tr>
    <tr>
      <th>North Carolina</th>
      <td>95354.830000</td>
      <td>9535483</td>
    </tr>
    <tr>
      <th>North Dakota</th>
      <td>12690.396226</td>
      <td>672591</td>
    </tr>
    <tr>
      <th>Ohio</th>
      <td>131096.636364</td>
      <td>11536504</td>
    </tr>
    <tr>
      <th>Oklahoma</th>
      <td>48718.844156</td>
      <td>3751351</td>
    </tr>
    <tr>
      <th>Oregon</th>
      <td>106418.722222</td>
      <td>3831074</td>
    </tr>
    <tr>
      <th>Pennsylvania</th>
      <td>189587.746269</td>
      <td>12702379</td>
    </tr>
    <tr>
      <th>Rhode Island</th>
      <td>210513.400000</td>
      <td>1052567</td>
    </tr>
    <tr>
      <th>South Carolina</th>
      <td>100551.391304</td>
      <td>4625364</td>
    </tr>
    <tr>
      <th>South Dakota</th>
      <td>12336.060606</td>
      <td>814180</td>
    </tr>
    <tr>
      <th>Tennessee</th>
      <td>66801.105263</td>
      <td>6346105</td>
    </tr>
    <tr>
      <th>Texas</th>
      <td>98998.271654</td>
      <td>25145561</td>
    </tr>
    <tr>
      <th>Utah</th>
      <td>95306.379310</td>
      <td>2763885</td>
    </tr>
    <tr>
      <th>Vermont</th>
      <td>44695.785714</td>
      <td>625741</td>
    </tr>
    <tr>
      <th>Virginia</th>
      <td>60111.293233</td>
      <td>7994802</td>
    </tr>
    <tr>
      <th>Washington</th>
      <td>172424.102564</td>
      <td>6724540</td>
    </tr>
    <tr>
      <th>West Virginia</th>
      <td>33690.800000</td>
      <td>1852994</td>
    </tr>
    <tr>
      <th>Wisconsin</th>
      <td>78985.916667</td>
      <td>5686986</td>
    </tr>
    <tr>
      <th>Wyoming</th>
      <td>24505.478261</td>
      <td>563626</td>
    </tr>
  </tbody>
</table>
</div>




```python
(df.set_index('STNAME').groupby(level=0)['POPESTIMATE2010','POPESTIMATE2011']
    .agg({'avg': np.average, 'sum': np.sum}))
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="2" halign="left">avg</th>
      <th colspan="2" halign="left">sum</th>
    </tr>
    <tr>
      <th></th>
      <th>POPESTIMATE2010</th>
      <th>POPESTIMATE2011</th>
      <th>POPESTIMATE2010</th>
      <th>POPESTIMATE2011</th>
    </tr>
    <tr>
      <th>STNAME</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Alabama</th>
      <td>71420.313433</td>
      <td>71658.328358</td>
      <td>4785161</td>
      <td>4801108</td>
    </tr>
    <tr>
      <th>Alaska</th>
      <td>24621.413793</td>
      <td>24921.379310</td>
      <td>714021</td>
      <td>722720</td>
    </tr>
    <tr>
      <th>Arizona</th>
      <td>427213.866667</td>
      <td>431248.800000</td>
      <td>6408208</td>
      <td>6468732</td>
    </tr>
    <tr>
      <th>Arkansas</th>
      <td>38965.253333</td>
      <td>39180.506667</td>
      <td>2922394</td>
      <td>2938538</td>
    </tr>
    <tr>
      <th>California</th>
      <td>643691.017241</td>
      <td>650000.586207</td>
      <td>37334079</td>
      <td>37700034</td>
    </tr>
    <tr>
      <th>Colorado</th>
      <td>78878.968750</td>
      <td>79991.875000</td>
      <td>5048254</td>
      <td>5119480</td>
    </tr>
    <tr>
      <th>Connecticut</th>
      <td>447464.625000</td>
      <td>448719.875000</td>
      <td>3579717</td>
      <td>3589759</td>
    </tr>
    <tr>
      <th>Delaware</th>
      <td>299930.333333</td>
      <td>302638.666667</td>
      <td>899791</td>
      <td>907916</td>
    </tr>
    <tr>
      <th>District of Columbia</th>
      <td>605126.000000</td>
      <td>620472.000000</td>
      <td>605126</td>
      <td>620472</td>
    </tr>
    <tr>
      <th>Florida</th>
      <td>281341.641791</td>
      <td>285157.208955</td>
      <td>18849890</td>
      <td>19105533</td>
    </tr>
    <tr>
      <th>Georgia</th>
      <td>61090.905660</td>
      <td>61712.452830</td>
      <td>9713454</td>
      <td>9812280</td>
    </tr>
    <tr>
      <th>Hawaii</th>
      <td>272796.000000</td>
      <td>275645.400000</td>
      <td>1363980</td>
      <td>1378227</td>
    </tr>
    <tr>
      <th>Idaho</th>
      <td>35704.227273</td>
      <td>36003.045455</td>
      <td>1570986</td>
      <td>1584134</td>
    </tr>
    <tr>
      <th>Illinois</th>
      <td>125894.598039</td>
      <td>126096.882353</td>
      <td>12841249</td>
      <td>12861882</td>
    </tr>
    <tr>
      <th>Indiana</th>
      <td>70549.891304</td>
      <td>70835.271739</td>
      <td>6490590</td>
      <td>6516845</td>
    </tr>
    <tr>
      <th>Iowa</th>
      <td>30815.090909</td>
      <td>30963.525253</td>
      <td>3050694</td>
      <td>3065389</td>
    </tr>
    <tr>
      <th>Kansas</th>
      <td>27226.895238</td>
      <td>27332.542857</td>
      <td>2858824</td>
      <td>2869917</td>
    </tr>
    <tr>
      <th>Kentucky</th>
      <td>36232.808333</td>
      <td>36399.016667</td>
      <td>4347937</td>
      <td>4367882</td>
    </tr>
    <tr>
      <th>Louisiana</th>
      <td>71014.859375</td>
      <td>71490.328125</td>
      <td>4544951</td>
      <td>4575381</td>
    </tr>
    <tr>
      <th>Maine</th>
      <td>82980.937500</td>
      <td>83016.062500</td>
      <td>1327695</td>
      <td>1328257</td>
    </tr>
    <tr>
      <th>Maryland</th>
      <td>241183.708333</td>
      <td>243507.125000</td>
      <td>5788409</td>
      <td>5844171</td>
    </tr>
    <tr>
      <th>Massachusetts</th>
      <td>468931.142857</td>
      <td>472271.214286</td>
      <td>6565036</td>
      <td>6611797</td>
    </tr>
    <tr>
      <th>Michigan</th>
      <td>119004.445783</td>
      <td>118995.048193</td>
      <td>9877369</td>
      <td>9876589</td>
    </tr>
    <tr>
      <th>Minnesota</th>
      <td>61044.862069</td>
      <td>61472.632184</td>
      <td>5310903</td>
      <td>5348119</td>
    </tr>
    <tr>
      <th>Mississippi</th>
      <td>36223.365854</td>
      <td>36317.060976</td>
      <td>2970316</td>
      <td>2977999</td>
    </tr>
    <tr>
      <th>Missouri</th>
      <td>52139.582609</td>
      <td>52265.973913</td>
      <td>5996052</td>
      <td>6010587</td>
    </tr>
    <tr>
      <th>Montana</th>
      <td>17690.053571</td>
      <td>17816.892857</td>
      <td>990643</td>
      <td>997746</td>
    </tr>
    <tr>
      <th>Nebraska</th>
      <td>19677.688172</td>
      <td>19810.569892</td>
      <td>1830025</td>
      <td>1842383</td>
    </tr>
    <tr>
      <th>Nevada</th>
      <td>159025.882353</td>
      <td>159930.529412</td>
      <td>2703440</td>
      <td>2718819</td>
    </tr>
    <tr>
      <th>New Hampshire</th>
      <td>131670.800000</td>
      <td>131834.400000</td>
      <td>1316708</td>
      <td>1318344</td>
    </tr>
    <tr>
      <th>New Jersey</th>
      <td>419232.428571</td>
      <td>421092.095238</td>
      <td>8803881</td>
      <td>8842934</td>
    </tr>
    <tr>
      <th>New Mexico</th>
      <td>62567.909091</td>
      <td>62976.545455</td>
      <td>2064741</td>
      <td>2078226</td>
    </tr>
    <tr>
      <th>New York</th>
      <td>312950.322581</td>
      <td>314890.354839</td>
      <td>19402920</td>
      <td>19523202</td>
    </tr>
    <tr>
      <th>North Carolina</th>
      <td>95589.790000</td>
      <td>96510.250000</td>
      <td>9558979</td>
      <td>9651025</td>
    </tr>
    <tr>
      <th>North Dakota</th>
      <td>12726.981132</td>
      <td>12930.679245</td>
      <td>674530</td>
      <td>685326</td>
    </tr>
    <tr>
      <th>Ohio</th>
      <td>131145.068182</td>
      <td>131198.204545</td>
      <td>11540766</td>
      <td>11545442</td>
    </tr>
    <tr>
      <th>Oklahoma</th>
      <td>48825.922078</td>
      <td>49176.961039</td>
      <td>3759596</td>
      <td>3786626</td>
    </tr>
    <tr>
      <th>Oregon</th>
      <td>106610.333333</td>
      <td>107458.583333</td>
      <td>3837972</td>
      <td>3868509</td>
    </tr>
    <tr>
      <th>Pennsylvania</th>
      <td>189731.552239</td>
      <td>190226.895522</td>
      <td>12712014</td>
      <td>12745202</td>
    </tr>
    <tr>
      <th>Rhode Island</th>
      <td>210643.800000</td>
      <td>210371.200000</td>
      <td>1053219</td>
      <td>1051856</td>
    </tr>
    <tr>
      <th>South Carolina</th>
      <td>100780.304348</td>
      <td>101581.152174</td>
      <td>4635894</td>
      <td>4672733</td>
    </tr>
    <tr>
      <th>South Dakota</th>
      <td>12368.166667</td>
      <td>12489.227273</td>
      <td>816299</td>
      <td>824289</td>
    </tr>
    <tr>
      <th>Tennessee</th>
      <td>66911.421053</td>
      <td>67351.663158</td>
      <td>6356585</td>
      <td>6398408</td>
    </tr>
    <tr>
      <th>Texas</th>
      <td>99387.255906</td>
      <td>101001.826772</td>
      <td>25244363</td>
      <td>25654464</td>
    </tr>
    <tr>
      <th>Utah</th>
      <td>95704.344828</td>
      <td>97118.620690</td>
      <td>2775426</td>
      <td>2816440</td>
    </tr>
    <tr>
      <th>Vermont</th>
      <td>44713.142857</td>
      <td>44763.357143</td>
      <td>625984</td>
      <td>626687</td>
    </tr>
    <tr>
      <th>Virginia</th>
      <td>60344.263158</td>
      <td>60983.330827</td>
      <td>8025787</td>
      <td>8110783</td>
    </tr>
    <tr>
      <th>Washington</th>
      <td>172898.974359</td>
      <td>174954.589744</td>
      <td>6743060</td>
      <td>6823229</td>
    </tr>
    <tr>
      <th>West Virginia</th>
      <td>33713.181818</td>
      <td>33726.327273</td>
      <td>1854225</td>
      <td>1854948</td>
    </tr>
    <tr>
      <th>Wisconsin</th>
      <td>79030.611111</td>
      <td>79301.666667</td>
      <td>5690204</td>
      <td>5709720</td>
    </tr>
    <tr>
      <th>Wyoming</th>
      <td>24544.173913</td>
      <td>24685.565217</td>
      <td>564516</td>
      <td>567768</td>
    </tr>
  </tbody>
</table>
</div>




```python
(df.set_index('STNAME').groupby(level=0)['POPESTIMATE2010','POPESTIMATE2011']
    .agg({'POPESTIMATE2010': np.average, 'POPESTIMATE2011': np.sum}))
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>POPESTIMATE2010</th>
      <th>POPESTIMATE2011</th>
    </tr>
    <tr>
      <th>STNAME</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Alabama</th>
      <td>71420.313433</td>
      <td>4801108</td>
    </tr>
    <tr>
      <th>Alaska</th>
      <td>24621.413793</td>
      <td>722720</td>
    </tr>
    <tr>
      <th>Arizona</th>
      <td>427213.866667</td>
      <td>6468732</td>
    </tr>
    <tr>
      <th>Arkansas</th>
      <td>38965.253333</td>
      <td>2938538</td>
    </tr>
    <tr>
      <th>California</th>
      <td>643691.017241</td>
      <td>37700034</td>
    </tr>
    <tr>
      <th>Colorado</th>
      <td>78878.968750</td>
      <td>5119480</td>
    </tr>
    <tr>
      <th>Connecticut</th>
      <td>447464.625000</td>
      <td>3589759</td>
    </tr>
    <tr>
      <th>Delaware</th>
      <td>299930.333333</td>
      <td>907916</td>
    </tr>
    <tr>
      <th>District of Columbia</th>
      <td>605126.000000</td>
      <td>620472</td>
    </tr>
    <tr>
      <th>Florida</th>
      <td>281341.641791</td>
      <td>19105533</td>
    </tr>
    <tr>
      <th>Georgia</th>
      <td>61090.905660</td>
      <td>9812280</td>
    </tr>
    <tr>
      <th>Hawaii</th>
      <td>272796.000000</td>
      <td>1378227</td>
    </tr>
    <tr>
      <th>Idaho</th>
      <td>35704.227273</td>
      <td>1584134</td>
    </tr>
    <tr>
      <th>Illinois</th>
      <td>125894.598039</td>
      <td>12861882</td>
    </tr>
    <tr>
      <th>Indiana</th>
      <td>70549.891304</td>
      <td>6516845</td>
    </tr>
    <tr>
      <th>Iowa</th>
      <td>30815.090909</td>
      <td>3065389</td>
    </tr>
    <tr>
      <th>Kansas</th>
      <td>27226.895238</td>
      <td>2869917</td>
    </tr>
    <tr>
      <th>Kentucky</th>
      <td>36232.808333</td>
      <td>4367882</td>
    </tr>
    <tr>
      <th>Louisiana</th>
      <td>71014.859375</td>
      <td>4575381</td>
    </tr>
    <tr>
      <th>Maine</th>
      <td>82980.937500</td>
      <td>1328257</td>
    </tr>
    <tr>
      <th>Maryland</th>
      <td>241183.708333</td>
      <td>5844171</td>
    </tr>
    <tr>
      <th>Massachusetts</th>
      <td>468931.142857</td>
      <td>6611797</td>
    </tr>
    <tr>
      <th>Michigan</th>
      <td>119004.445783</td>
      <td>9876589</td>
    </tr>
    <tr>
      <th>Minnesota</th>
      <td>61044.862069</td>
      <td>5348119</td>
    </tr>
    <tr>
      <th>Mississippi</th>
      <td>36223.365854</td>
      <td>2977999</td>
    </tr>
    <tr>
      <th>Missouri</th>
      <td>52139.582609</td>
      <td>6010587</td>
    </tr>
    <tr>
      <th>Montana</th>
      <td>17690.053571</td>
      <td>997746</td>
    </tr>
    <tr>
      <th>Nebraska</th>
      <td>19677.688172</td>
      <td>1842383</td>
    </tr>
    <tr>
      <th>Nevada</th>
      <td>159025.882353</td>
      <td>2718819</td>
    </tr>
    <tr>
      <th>New Hampshire</th>
      <td>131670.800000</td>
      <td>1318344</td>
    </tr>
    <tr>
      <th>New Jersey</th>
      <td>419232.428571</td>
      <td>8842934</td>
    </tr>
    <tr>
      <th>New Mexico</th>
      <td>62567.909091</td>
      <td>2078226</td>
    </tr>
    <tr>
      <th>New York</th>
      <td>312950.322581</td>
      <td>19523202</td>
    </tr>
    <tr>
      <th>North Carolina</th>
      <td>95589.790000</td>
      <td>9651025</td>
    </tr>
    <tr>
      <th>North Dakota</th>
      <td>12726.981132</td>
      <td>685326</td>
    </tr>
    <tr>
      <th>Ohio</th>
      <td>131145.068182</td>
      <td>11545442</td>
    </tr>
    <tr>
      <th>Oklahoma</th>
      <td>48825.922078</td>
      <td>3786626</td>
    </tr>
    <tr>
      <th>Oregon</th>
      <td>106610.333333</td>
      <td>3868509</td>
    </tr>
    <tr>
      <th>Pennsylvania</th>
      <td>189731.552239</td>
      <td>12745202</td>
    </tr>
    <tr>
      <th>Rhode Island</th>
      <td>210643.800000</td>
      <td>1051856</td>
    </tr>
    <tr>
      <th>South Carolina</th>
      <td>100780.304348</td>
      <td>4672733</td>
    </tr>
    <tr>
      <th>South Dakota</th>
      <td>12368.166667</td>
      <td>824289</td>
    </tr>
    <tr>
      <th>Tennessee</th>
      <td>66911.421053</td>
      <td>6398408</td>
    </tr>
    <tr>
      <th>Texas</th>
      <td>99387.255906</td>
      <td>25654464</td>
    </tr>
    <tr>
      <th>Utah</th>
      <td>95704.344828</td>
      <td>2816440</td>
    </tr>
    <tr>
      <th>Vermont</th>
      <td>44713.142857</td>
      <td>626687</td>
    </tr>
    <tr>
      <th>Virginia</th>
      <td>60344.263158</td>
      <td>8110783</td>
    </tr>
    <tr>
      <th>Washington</th>
      <td>172898.974359</td>
      <td>6823229</td>
    </tr>
    <tr>
      <th>West Virginia</th>
      <td>33713.181818</td>
      <td>1854948</td>
    </tr>
    <tr>
      <th>Wisconsin</th>
      <td>79030.611111</td>
      <td>5709720</td>
    </tr>
    <tr>
      <th>Wyoming</th>
      <td>24544.173913</td>
      <td>567768</td>
    </tr>
  </tbody>
</table>
</div>



# Scales


```python
df = pd.DataFrame(['A+', 'A', 'A-', 'B+', 'B', 'B-', 'C+', 'C', 'C-', 'D+', 'D'],
                  index=['excellent', 'excellent', 'excellent', 'good', 'good', 'good', 'ok', 'ok', 'ok', 'poor', 'poor'])
df.rename(columns={0: 'Grades'}, inplace=True)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Grades</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>excellent</th>
      <td>A+</td>
    </tr>
    <tr>
      <th>excellent</th>
      <td>A</td>
    </tr>
    <tr>
      <th>excellent</th>
      <td>A-</td>
    </tr>
    <tr>
      <th>good</th>
      <td>B+</td>
    </tr>
    <tr>
      <th>good</th>
      <td>B</td>
    </tr>
    <tr>
      <th>good</th>
      <td>B-</td>
    </tr>
    <tr>
      <th>ok</th>
      <td>C+</td>
    </tr>
    <tr>
      <th>ok</th>
      <td>C</td>
    </tr>
    <tr>
      <th>ok</th>
      <td>C-</td>
    </tr>
    <tr>
      <th>poor</th>
      <td>D+</td>
    </tr>
    <tr>
      <th>poor</th>
      <td>D</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['Grades'].astype('category').head()
```




    excellent    A+
    excellent     A
    excellent    A-
    good         B+
    good          B
    Name: Grades, dtype: category
    Categories (11, object): [A, A+, A-, B, ..., C+, C-, D, D+]




```python
grades = df['Grades'].astype('category',
                             categories=['D', 'D+', 'C-', 'C', 'C+', 'B-', 'B', 'B+', 'A-', 'A', 'A+'],
                             ordered=True)
grades.head()
```




    excellent    A+
    excellent     A
    excellent    A-
    good         B+
    good          B
    Name: Grades, dtype: category
    Categories (11, object): [D < D+ < C- < C ... B+ < A- < A < A+]




```python
grades > 'C'
```




    excellent     True
    excellent     True
    excellent     True
    good          True
    good          True
    good          True
    ok            True
    ok           False
    ok           False
    poor         False
    poor         False
    Name: Grades, dtype: bool




```python
df = pd.read_csv('census.csv')
df = df[df['SUMLEV']==50]
df = df.set_index('STNAME').groupby(level=0)['CENSUS2010POP'].agg({'avg': np.average})
pd.cut(df['avg'],10)
```




    STNAME
    Alabama                  (11706.0871, 75333.413]
    Alaska                   (11706.0871, 75333.413]
    Arizona                 (390320.176, 453317.529]
    Arkansas                 (11706.0871, 75333.413]
    California              (579312.234, 642309.586]
    Colorado                 (75333.413, 138330.766]
    Connecticut             (390320.176, 453317.529]
    Delaware                (264325.471, 327322.823]
    District of Columbia    (579312.234, 642309.586]
    Florida                 (264325.471, 327322.823]
    Georgia                  (11706.0871, 75333.413]
    Hawaii                  (264325.471, 327322.823]
    Idaho                    (11706.0871, 75333.413]
    Illinois                 (75333.413, 138330.766]
    Indiana                  (11706.0871, 75333.413]
    Iowa                     (11706.0871, 75333.413]
    Kansas                   (11706.0871, 75333.413]
    Kentucky                 (11706.0871, 75333.413]
    Louisiana                (11706.0871, 75333.413]
    Maine                    (75333.413, 138330.766]
    Maryland                (201328.118, 264325.471]
    Massachusetts           (453317.529, 516314.881]
    Michigan                 (75333.413, 138330.766]
    Minnesota                (11706.0871, 75333.413]
    Mississippi              (11706.0871, 75333.413]
    Missouri                 (11706.0871, 75333.413]
    Montana                  (11706.0871, 75333.413]
    Nebraska                 (11706.0871, 75333.413]
    Nevada                  (138330.766, 201328.118]
    New Hampshire            (75333.413, 138330.766]
    New Jersey              (390320.176, 453317.529]
    New Mexico               (11706.0871, 75333.413]
    New York                (264325.471, 327322.823]
    North Carolina           (75333.413, 138330.766]
    North Dakota             (11706.0871, 75333.413]
    Ohio                     (75333.413, 138330.766]
    Oklahoma                 (11706.0871, 75333.413]
    Oregon                   (75333.413, 138330.766]
    Pennsylvania            (138330.766, 201328.118]
    Rhode Island            (201328.118, 264325.471]
    South Carolina           (75333.413, 138330.766]
    South Dakota             (11706.0871, 75333.413]
    Tennessee                (11706.0871, 75333.413]
    Texas                    (75333.413, 138330.766]
    Utah                     (75333.413, 138330.766]
    Vermont                  (11706.0871, 75333.413]
    Virginia                 (11706.0871, 75333.413]
    Washington              (138330.766, 201328.118]
    West Virginia            (11706.0871, 75333.413]
    Wisconsin                (75333.413, 138330.766]
    Wyoming                  (11706.0871, 75333.413]
    Name: avg, dtype: category
    Categories (10, object): [(11706.0871, 75333.413] < (75333.413, 138330.766] < (138330.766, 201328.118] < (201328.118, 264325.471] ... (390320.176, 453317.529] < (453317.529, 516314.881] < (516314.881, 579312.234] < (579312.234, 642309.586]]



# Pivot Tables


```python
#http://open.canada.ca/data/en/dataset/98f1a129-f628-4ce4-b24d-6f16bf24dd64
df = pd.read_csv('cars.csv')
```


```python
df.head()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>YEAR</th>
      <th>Make</th>
      <th>Model</th>
      <th>Size</th>
      <th>(kW)</th>
      <th>Unnamed: 5</th>
      <th>TYPE</th>
      <th>CITY (kWh/100 km)</th>
      <th>HWY (kWh/100 km)</th>
      <th>COMB (kWh/100 km)</th>
      <th>CITY (Le/100 km)</th>
      <th>HWY (Le/100 km)</th>
      <th>COMB (Le/100 km)</th>
      <th>(g/km)</th>
      <th>RATING</th>
      <th>(km)</th>
      <th>TIME (h)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2012</td>
      <td>MITSUBISHI</td>
      <td>i-MiEV</td>
      <td>SUBCOMPACT</td>
      <td>49</td>
      <td>A1</td>
      <td>B</td>
      <td>16.9</td>
      <td>21.4</td>
      <td>18.7</td>
      <td>1.9</td>
      <td>2.4</td>
      <td>2.1</td>
      <td>0</td>
      <td>n/a</td>
      <td>100</td>
      <td>7</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2012</td>
      <td>NISSAN</td>
      <td>LEAF</td>
      <td>MID-SIZE</td>
      <td>80</td>
      <td>A1</td>
      <td>B</td>
      <td>19.3</td>
      <td>23.0</td>
      <td>21.1</td>
      <td>2.2</td>
      <td>2.6</td>
      <td>2.4</td>
      <td>0</td>
      <td>n/a</td>
      <td>117</td>
      <td>7</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2013</td>
      <td>FORD</td>
      <td>FOCUS ELECTRIC</td>
      <td>COMPACT</td>
      <td>107</td>
      <td>A1</td>
      <td>B</td>
      <td>19.0</td>
      <td>21.1</td>
      <td>20.0</td>
      <td>2.1</td>
      <td>2.4</td>
      <td>2.2</td>
      <td>0</td>
      <td>n/a</td>
      <td>122</td>
      <td>4</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2013</td>
      <td>MITSUBISHI</td>
      <td>i-MiEV</td>
      <td>SUBCOMPACT</td>
      <td>49</td>
      <td>A1</td>
      <td>B</td>
      <td>16.9</td>
      <td>21.4</td>
      <td>18.7</td>
      <td>1.9</td>
      <td>2.4</td>
      <td>2.1</td>
      <td>0</td>
      <td>n/a</td>
      <td>100</td>
      <td>7</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2013</td>
      <td>NISSAN</td>
      <td>LEAF</td>
      <td>MID-SIZE</td>
      <td>80</td>
      <td>A1</td>
      <td>B</td>
      <td>19.3</td>
      <td>23.0</td>
      <td>21.1</td>
      <td>2.2</td>
      <td>2.6</td>
      <td>2.4</td>
      <td>0</td>
      <td>n/a</td>
      <td>117</td>
      <td>7</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.pivot_table(values='(kW)', index='YEAR', columns='Make', aggfunc=np.mean)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Make</th>
      <th>BMW</th>
      <th>CHEVROLET</th>
      <th>FORD</th>
      <th>KIA</th>
      <th>MITSUBISHI</th>
      <th>NISSAN</th>
      <th>SMART</th>
      <th>TESLA</th>
    </tr>
    <tr>
      <th>YEAR</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2012</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2013</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>107.0</td>
      <td>NaN</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>280.000000</td>
    </tr>
    <tr>
      <th>2014</th>
      <td>NaN</td>
      <td>104.0</td>
      <td>107.0</td>
      <td>NaN</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>268.333333</td>
    </tr>
    <tr>
      <th>2015</th>
      <td>125.0</td>
      <td>104.0</td>
      <td>107.0</td>
      <td>81.0</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>320.666667</td>
    </tr>
    <tr>
      <th>2016</th>
      <td>125.0</td>
      <td>104.0</td>
      <td>107.0</td>
      <td>81.0</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>409.700000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.pivot_table(values='(kW)', index='YEAR', columns='Make', aggfunc=[np.mean,np.min], margins=True)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="9" halign="left">mean</th>
      <th colspan="9" halign="left">amin</th>
    </tr>
    <tr>
      <th>Make</th>
      <th>BMW</th>
      <th>CHEVROLET</th>
      <th>FORD</th>
      <th>KIA</th>
      <th>MITSUBISHI</th>
      <th>NISSAN</th>
      <th>SMART</th>
      <th>TESLA</th>
      <th>All</th>
      <th>BMW</th>
      <th>CHEVROLET</th>
      <th>FORD</th>
      <th>KIA</th>
      <th>MITSUBISHI</th>
      <th>NISSAN</th>
      <th>SMART</th>
      <th>TESLA</th>
      <th>All</th>
    </tr>
    <tr>
      <th>YEAR</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2012</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>64.500000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>49.0</td>
    </tr>
    <tr>
      <th>2013</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>107.0</td>
      <td>NaN</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>280.000000</td>
      <td>158.444444</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>107.0</td>
      <td>NaN</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>270.0</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>2014</th>
      <td>NaN</td>
      <td>104.0</td>
      <td>107.0</td>
      <td>NaN</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>268.333333</td>
      <td>135.000000</td>
      <td>NaN</td>
      <td>104.0</td>
      <td>107.0</td>
      <td>NaN</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>225.0</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>2015</th>
      <td>125.0</td>
      <td>104.0</td>
      <td>107.0</td>
      <td>81.0</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>320.666667</td>
      <td>181.428571</td>
      <td>125.0</td>
      <td>104.0</td>
      <td>107.0</td>
      <td>81.0</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>280.0</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>2016</th>
      <td>125.0</td>
      <td>104.0</td>
      <td>107.0</td>
      <td>81.0</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>409.700000</td>
      <td>252.263158</td>
      <td>125.0</td>
      <td>104.0</td>
      <td>107.0</td>
      <td>81.0</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>283.0</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>All</th>
      <td>125.0</td>
      <td>104.0</td>
      <td>107.0</td>
      <td>81.0</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>345.478261</td>
      <td>190.622642</td>
      <td>125.0</td>
      <td>104.0</td>
      <td>107.0</td>
      <td>81.0</td>
      <td>49.0</td>
      <td>80.0</td>
      <td>35.0</td>
      <td>225.0</td>
      <td>35.0</td>
    </tr>
  </tbody>
</table>
</div>



# Date Functionality in Pandas


```python
import pandas as pd
import numpy as np
```

### Timestamp


```python
pd.Timestamp('9/1/2016 10:05AM')
```




    Timestamp('2016-09-01 10:05:00')



### Period


```python
pd.Period('1/2016')
```




    Period('2016-01', 'M')




```python
pd.Period('3/5/2016')
```




    Period('2016-03-05', 'D')



### DatetimeIndex


```python
t1 = pd.Series(list('abc'), [pd.Timestamp('2016-09-01'), pd.Timestamp('2016-09-02'), pd.Timestamp('2016-09-03')])
t1
```




    2016-09-01    a
    2016-09-02    b
    2016-09-03    c
    dtype: object




```python
type(t1.index)
```




    pandas.tseries.index.DatetimeIndex



### PeriodIndex


```python
t2 = pd.Series(list('def'), [pd.Period('2016-09'), pd.Period('2016-10'), pd.Period('2016-11')])
t2
```




    2016-09    d
    2016-10    e
    2016-11    f
    Freq: M, dtype: object




```python
type(t2.index)
```




    pandas.tseries.period.PeriodIndex



### Converting to Datetime


```python
d1 = ['2 June 2013', 'Aug 29, 2014', '2015-06-26', '7/12/16']
ts3 = pd.DataFrame(np.random.randint(10, 100, (4,2)), index=d1, columns=list('ab'))
ts3
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2 June 2013</th>
      <td>46</td>
      <td>70</td>
    </tr>
    <tr>
      <th>Aug 29, 2014</th>
      <td>75</td>
      <td>52</td>
    </tr>
    <tr>
      <th>2015-06-26</th>
      <td>79</td>
      <td>43</td>
    </tr>
    <tr>
      <th>7/12/16</th>
      <td>12</td>
      <td>47</td>
    </tr>
  </tbody>
</table>
</div>




```python
ts3.index = pd.to_datetime(ts3.index)
ts3
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2013-06-02</th>
      <td>46</td>
      <td>70</td>
    </tr>
    <tr>
      <th>2014-08-29</th>
      <td>75</td>
      <td>52</td>
    </tr>
    <tr>
      <th>2015-06-26</th>
      <td>79</td>
      <td>43</td>
    </tr>
    <tr>
      <th>2016-07-12</th>
      <td>12</td>
      <td>47</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.to_datetime('4.7.12', dayfirst=True)
```




    Timestamp('2012-07-04 00:00:00')



### Timedeltas


```python
pd.Timestamp('9/3/2016')-pd.Timestamp('9/1/2016')
```




    Timedelta('2 days 00:00:00')




```python
pd.Timestamp('9/2/2016 8:10AM') + pd.Timedelta('12D 3H')
```




    Timestamp('2016-09-14 11:10:00')



### Working with Dates in a Dataframe


```python
dates = pd.date_range('10-01-2016', periods=9, freq='2W-SUN')
dates
```




    DatetimeIndex(['2016-10-02', '2016-10-16', '2016-10-30', '2016-11-13',
                   '2016-11-27', '2016-12-11', '2016-12-25', '2017-01-08',
                   '2017-01-22'],
                  dtype='datetime64[ns]', freq='2W-SUN')




```python
df = pd.DataFrame({'Count 1': 100 + np.random.randint(-5, 10, 9).cumsum(),
                  'Count 2': 120 + np.random.randint(-5, 10, 9)}, index=dates)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Count 1</th>
      <th>Count 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-10-02</th>
      <td>100</td>
      <td>127</td>
    </tr>
    <tr>
      <th>2016-10-16</th>
      <td>106</td>
      <td>129</td>
    </tr>
    <tr>
      <th>2016-10-30</th>
      <td>107</td>
      <td>115</td>
    </tr>
    <tr>
      <th>2016-11-13</th>
      <td>116</td>
      <td>128</td>
    </tr>
    <tr>
      <th>2016-11-27</th>
      <td>111</td>
      <td>125</td>
    </tr>
    <tr>
      <th>2016-12-11</th>
      <td>108</td>
      <td>125</td>
    </tr>
    <tr>
      <th>2016-12-25</th>
      <td>108</td>
      <td>115</td>
    </tr>
    <tr>
      <th>2017-01-08</th>
      <td>114</td>
      <td>118</td>
    </tr>
    <tr>
      <th>2017-01-22</th>
      <td>115</td>
      <td>115</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.index.weekday_name
```




    array(['Sunday', 'Sunday', 'Sunday', 'Sunday', 'Sunday', 'Sunday',
           'Sunday', 'Sunday', 'Sunday'], dtype=object)




```python
df.diff()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Count 1</th>
      <th>Count 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-10-02</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-10-16</th>
      <td>6.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>2016-10-30</th>
      <td>1.0</td>
      <td>-14.0</td>
    </tr>
    <tr>
      <th>2016-11-13</th>
      <td>9.0</td>
      <td>13.0</td>
    </tr>
    <tr>
      <th>2016-11-27</th>
      <td>-5.0</td>
      <td>-3.0</td>
    </tr>
    <tr>
      <th>2016-12-11</th>
      <td>-3.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2016-12-25</th>
      <td>0.0</td>
      <td>-10.0</td>
    </tr>
    <tr>
      <th>2017-01-08</th>
      <td>6.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>2017-01-22</th>
      <td>1.0</td>
      <td>-3.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.resample('M').mean()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Count 1</th>
      <th>Count 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-10-31</th>
      <td>104.333333</td>
      <td>123.666667</td>
    </tr>
    <tr>
      <th>2016-11-30</th>
      <td>113.500000</td>
      <td>126.500000</td>
    </tr>
    <tr>
      <th>2016-12-31</th>
      <td>108.000000</td>
      <td>120.000000</td>
    </tr>
    <tr>
      <th>2017-01-31</th>
      <td>114.500000</td>
      <td>116.500000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['2017']
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Count 1</th>
      <th>Count 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017-01-08</th>
      <td>114</td>
      <td>118</td>
    </tr>
    <tr>
      <th>2017-01-22</th>
      <td>115</td>
      <td>115</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['2016-12']
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Count 1</th>
      <th>Count 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-12-11</th>
      <td>108</td>
      <td>125</td>
    </tr>
    <tr>
      <th>2016-12-25</th>
      <td>108</td>
      <td>115</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['2016-12':]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Count 1</th>
      <th>Count 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-12-11</th>
      <td>108</td>
      <td>125</td>
    </tr>
    <tr>
      <th>2016-12-25</th>
      <td>108</td>
      <td>115</td>
    </tr>
    <tr>
      <th>2017-01-08</th>
      <td>114</td>
      <td>118</td>
    </tr>
    <tr>
      <th>2017-01-22</th>
      <td>115</td>
      <td>115</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.asfreq('W', method='ffill')
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Count 1</th>
      <th>Count 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-10-02</th>
      <td>100</td>
      <td>127</td>
    </tr>
    <tr>
      <th>2016-10-09</th>
      <td>100</td>
      <td>127</td>
    </tr>
    <tr>
      <th>2016-10-16</th>
      <td>106</td>
      <td>129</td>
    </tr>
    <tr>
      <th>2016-10-23</th>
      <td>106</td>
      <td>129</td>
    </tr>
    <tr>
      <th>2016-10-30</th>
      <td>107</td>
      <td>115</td>
    </tr>
    <tr>
      <th>2016-11-06</th>
      <td>107</td>
      <td>115</td>
    </tr>
    <tr>
      <th>2016-11-13</th>
      <td>116</td>
      <td>128</td>
    </tr>
    <tr>
      <th>2016-11-20</th>
      <td>116</td>
      <td>128</td>
    </tr>
    <tr>
      <th>2016-11-27</th>
      <td>111</td>
      <td>125</td>
    </tr>
    <tr>
      <th>2016-12-04</th>
      <td>111</td>
      <td>125</td>
    </tr>
    <tr>
      <th>2016-12-11</th>
      <td>108</td>
      <td>125</td>
    </tr>
    <tr>
      <th>2016-12-18</th>
      <td>108</td>
      <td>125</td>
    </tr>
    <tr>
      <th>2016-12-25</th>
      <td>108</td>
      <td>115</td>
    </tr>
    <tr>
      <th>2017-01-01</th>
      <td>108</td>
      <td>115</td>
    </tr>
    <tr>
      <th>2017-01-08</th>
      <td>114</td>
      <td>118</td>
    </tr>
    <tr>
      <th>2017-01-15</th>
      <td>114</td>
      <td>118</td>
    </tr>
    <tr>
      <th>2017-01-22</th>
      <td>115</td>
      <td>115</td>
    </tr>
  </tbody>
</table>
</div>




```python
import matplotlib.pyplot as plt
%matplotlib inline

df.plot()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f6d4d39ff28>




![png](output_76_1.png)

