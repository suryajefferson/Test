<details>
  <summary><h3>Click to expand</h3></summary>

  ## Heading 1
  This is some hidden content that you can reveal by clicking the summary above.
  [[!Video](https://i.ytimg.com/vi_webp/4xOX3FnPtsg/maxresdefault.webp)(https://www.youtube.com/watch?v=4xOX3FnPtsg)]

  ### Heading 2
  More hidden content under a subheading.

</details>




### Importing Libraries

  - `pandas` as `pd` for data manipulation and analysis.
  - `numpy` as `np` for numerical operations.
  - `matplotlib.pyplot` as `plt` for creating visualizations.
  - `ast` for safely evaluating strings into python objects.
  - `seaborn` as `sns` for statistical data visualization and enhanced plotting.



```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import ast  
import seaborn as sns
```

### Loading Data

- **Reading CSV File:** reading a csv file into a dataframe named `df`, which is used for data analysis and manipulation.



```python
df = pd.read_csv(r'D:\Python\Python course\data_jobs.csv')
df.sample(2)
```



<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>job_title_short</th>
      <th>job_title</th>
      <th>job_location</th>
      <th>job_via</th>
      <th>job_schedule_type</th>
      <th>job_work_from_home</th>
      <th>search_location</th>
      <th>job_posted_date</th>
      <th>job_no_degree_mention</th>
      <th>job_health_insurance</th>
      <th>job_country</th>
      <th>salary_rate</th>
      <th>salary_year_avg</th>
      <th>salary_hour_avg</th>
      <th>company_name</th>
      <th>job_skills</th>
      <th>job_type_skills</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>353199</th>
      <td>Data Analyst</td>
      <td>Master Data Finance Analyst</td>
      <td>Sligo, Ireland</td>
      <td>via BeBee Ireland</td>
      <td>Full-time</td>
      <td>False</td>
      <td>Ireland</td>
      <td>2023-10-15 23:17:27</td>
      <td>False</td>
      <td>False</td>
      <td>Ireland</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Amcor</td>
      <td>['sap', 'excel']</td>
      <td>{'analyst_tools': ['sap', 'excel']}</td>
    </tr>
    <tr>
      <th>371135</th>
      <td>Machine Learning Engineer</td>
      <td>Senior Machine Learning Engineer</td>
      <td>Cairo, Egypt</td>
      <td>via Bayt.com</td>
      <td>Full-time</td>
      <td>False</td>
      <td>Egypt</td>
      <td>2023-03-30 00:01:15</td>
      <td>False</td>
      <td>False</td>
      <td>Egypt</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>EgyGamer LLC.</td>
      <td>['python', 'mysql', 'elasticsearch', 'pytorch'...</td>
      <td>{'databases': ['mysql', 'elasticsearch'], 'lib...</td>
    </tr>
  </tbody>
</table>




### Data Cleanup

- **Renaming Columns:** assigning new column names to the dataframe.

- **Converting Dates:** using `pd.to_datetime()` to change the 'posted_dt' column from string to datetime format.

- **Converting Skills:**
  - using `.apply() `function to convert 'skills' from string to list format by applying a custom function to  every row of a dataFrame.
  - using `ast.literal_eval()` to evaluate and convert strings to python objects.
  - ensuring conversion only happens if the value is not missing using `pd.notna(gg)`.

- **Handling Missing Values:** optionally dropping rows with missing values in the 'salyr' column using `df.dropna()` (commented out).


```python
new_columns = ['job', 'full_name', 'location', 'via', 'schedule', 'work_from_home','search_location','posted_dt','no_degree','health_ins','country','salrate','salyr','salhr','company','skills','skilltype']
df.columns = new_columns

# data clean up
df['posted_dt'] = pd.to_datetime(df['posted_dt'])
df['skills'] = df['skills'].apply(lambda gg: ast.literal_eval(gg) if pd.notna(gg) else gg) 
#df.dropna(subset=['salyr'],inplace=True)
```

### Sample

- Random sample of 2 rows from the modified dataFrame `df`


```python
df.sample(2)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>job</th>
      <th>full_name</th>
      <th>location</th>
      <th>via</th>
      <th>schedule</th>
      <th>work_from_home</th>
      <th>search_location</th>
      <th>posted_dt</th>
      <th>no_degree</th>
      <th>health_ins</th>
      <th>country</th>
      <th>salrate</th>
      <th>salyr</th>
      <th>salhr</th>
      <th>company</th>
      <th>skills</th>
      <th>skilltype</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>168992</th>
      <td>Machine Learning Engineer</td>
      <td>Senior Machine Learning Engineer</td>
      <td>Dublin, Ireland</td>
      <td>via LinkedIn</td>
      <td>Full-time</td>
      <td>False</td>
      <td>Ireland</td>
      <td>2023-10-04 15:35:30</td>
      <td>False</td>
      <td>False</td>
      <td>Ireland</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Harvey Nash</td>
      <td>[python]</td>
      <td>{'programming': ['python']}</td>
    </tr>
    <tr>
      <th>452987</th>
      <td>Data Analyst</td>
      <td>Data Analyst</td>
      <td>Lucca, Province of Lucca, Italy</td>
      <td>via Indeed</td>
      <td>Full-time</td>
      <td>False</td>
      <td>Italy</td>
      <td>2023-04-24 14:19:32</td>
      <td>False</td>
      <td>False</td>
      <td>Italy</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>ITALIA GAS E LUCE</td>
      <td>[sql, vba, power bi, excel, ssrs]</td>
      <td>{'analyst_tools': ['power bi', 'excel', 'ssrs'...</td>
    </tr>
  </tbody>
</table>
</div>



# For Data Analysts in India

## Filtering and Exploding  

- **Filtering DataFrame:** filtering the original dataframe to include only rows where the `job` column is `'data analyst'` and the `country` column is `'india'`, creating a new dataframe `df_da_ind`. making a copy of the filtered dataframe.

- **Adding Column:** adding a new column `posted_month_no` to `df_da_ind` by extracting the month from the `posted_dt` column.

- **Exploding Skills:** exploding the `skills` column in `df_da_ind` to create a new dataframe `df_da_ind_exp`, where each skill in the list is transformed into its own row. this allows for easier analysis of individual skills.



```python
df_da_ind = df[(df['job']== 'Data Analyst') & (df['country']== 'India')].copy()
df_da_ind['posted_month_no'] = df_da_ind['posted_dt'].dt.month

df_da_ind_exp = df_da_ind.explode('skills')
df_da_ind_exp.sample(2)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>job</th>
      <th>full_name</th>
      <th>location</th>
      <th>via</th>
      <th>schedule</th>
      <th>work_from_home</th>
      <th>search_location</th>
      <th>posted_dt</th>
      <th>no_degree</th>
      <th>health_ins</th>
      <th>country</th>
      <th>salrate</th>
      <th>salyr</th>
      <th>salhr</th>
      <th>company</th>
      <th>skills</th>
      <th>skilltype</th>
      <th>posted_month_no</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>394982</th>
      <td>Data Analyst</td>
      <td>Data Analytics</td>
      <td>India</td>
      <td>via BeBee India</td>
      <td>Full-time</td>
      <td>False</td>
      <td>India</td>
      <td>2023-05-30 18:10:39</td>
      <td>False</td>
      <td>False</td>
      <td>India</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>JP Morgan Chase</td>
      <td>sql</td>
      <td>{'analyst_tools': ['qlik', 'tableau', 'alteryx...</td>
      <td>5</td>
    </tr>
    <tr>
      <th>672979</th>
      <td>Data Analyst</td>
      <td>Data Analyst Level 3</td>
      <td>Secunderabad, Telangana, India</td>
      <td>via LinkedIn</td>
      <td>Full-time</td>
      <td>False</td>
      <td>India</td>
      <td>2023-09-14 10:10:47</td>
      <td>False</td>
      <td>False</td>
      <td>India</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Certara</td>
      <td>r</td>
      <td>{'analyst_tools': ['excel'], 'programming': ['...</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



Creating and Sorting a Pivot Table

- **Creating a Pivot Table:** creating a pivot table from the `df_da_ind_exp` dataframe, using `posted_month_no` as the index and `skills` as the columns. the table is aggregating the count of each skill per month using the 'size' function and filling missing values with 0.

- **Adding Total Row:** adding a new row labeled 'total' to the pivot table, which contains the sum of each skill across all months.

- **Reordering Columns:** reordering the columns in the pivot table based on the total counts of each skill, sorting them in descending order.

- **Dropping Total Row:** dropping the 'total' row from the pivot table, leaving only the monthly counts for each skill.



```python
df_da_ind_table = df_da_ind_exp.pivot_table(index='posted_month_no', columns='skills',aggfunc= 'size', fill_value= 0)
df_da_ind_table.loc['total'] = df_da_ind_table.sum()
df_da_ind_table = df_da_ind_table[df_da_ind_table.loc['total'].sort_values(ascending=False).index]
df_da_ind_table = df_da_ind_table.drop('total')
df_da_ind_table
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>skills</th>
      <th>sql</th>
      <th>python</th>
      <th>excel</th>
      <th>tableau</th>
      <th>power bi</th>
      <th>r</th>
      <th>sas</th>
      <th>azure</th>
      <th>aws</th>
      <th>powerpoint</th>
      <th>...</th>
      <th>hugging face</th>
      <th>fastapi</th>
      <th>kotlin</th>
      <th>powerbi</th>
      <th>mariadb</th>
      <th>sqlite</th>
      <th>clickup</th>
      <th>suse</th>
      <th>twilio</th>
      <th>centos</th>
    </tr>
    <tr>
      <th>posted_month_no</th>
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
      <th>1</th>
      <td>305</td>
      <td>216</td>
      <td>218</td>
      <td>159</td>
      <td>98</td>
      <td>89</td>
      <td>128</td>
      <td>46</td>
      <td>32</td>
      <td>43</td>
      <td>...</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>209</td>
      <td>148</td>
      <td>156</td>
      <td>116</td>
      <td>75</td>
      <td>67</td>
      <td>82</td>
      <td>26</td>
      <td>33</td>
      <td>25</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>229</td>
      <td>151</td>
      <td>138</td>
      <td>125</td>
      <td>76</td>
      <td>58</td>
      <td>62</td>
      <td>45</td>
      <td>38</td>
      <td>29</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>204</td>
      <td>143</td>
      <td>138</td>
      <td>98</td>
      <td>83</td>
      <td>56</td>
      <td>52</td>
      <td>40</td>
      <td>31</td>
      <td>28</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>155</td>
      <td>101</td>
      <td>106</td>
      <td>71</td>
      <td>61</td>
      <td>42</td>
      <td>30</td>
      <td>33</td>
      <td>22</td>
      <td>19</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>6</th>
      <td>193</td>
      <td>150</td>
      <td>115</td>
      <td>114</td>
      <td>77</td>
      <td>76</td>
      <td>74</td>
      <td>37</td>
      <td>32</td>
      <td>24</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>245</td>
      <td>161</td>
      <td>174</td>
      <td>124</td>
      <td>93</td>
      <td>67</td>
      <td>78</td>
      <td>39</td>
      <td>31</td>
      <td>31</td>
      <td>...</td>
      <td>1</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>317</td>
      <td>216</td>
      <td>192</td>
      <td>152</td>
      <td>127</td>
      <td>112</td>
      <td>98</td>
      <td>52</td>
      <td>63</td>
      <td>40</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>341</td>
      <td>229</td>
      <td>228</td>
      <td>195</td>
      <td>168</td>
      <td>100</td>
      <td>92</td>
      <td>35</td>
      <td>41</td>
      <td>29</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>269</td>
      <td>185</td>
      <td>193</td>
      <td>153</td>
      <td>110</td>
      <td>95</td>
      <td>86</td>
      <td>47</td>
      <td>48</td>
      <td>29</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>359</td>
      <td>264</td>
      <td>242</td>
      <td>182</td>
      <td>156</td>
      <td>115</td>
      <td>70</td>
      <td>57</td>
      <td>51</td>
      <td>47</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>333</td>
      <td>239</td>
      <td>217</td>
      <td>178</td>
      <td>162</td>
      <td>114</td>
      <td>100</td>
      <td>55</td>
      <td>30</td>
      <td>28</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>12 rows × 181 columns</p>
</div>



Counting Monthly Job Postings

- **Grouping Data:** grouping the `df_da_ind` dataframe by the `posted_month_no` column and calculating the size of each group.

- **Calculating Counts:** the result is a series named `df_da_ind_monthly_jobs` where the index is `posted_month_no` and the values are representing the count of data analyst jobs posted each month.


```python
df_da_ind_monthly_jobs = df_da_ind.groupby('posted_month_no').size()
df_da_ind_monthly_jobs
```




    posted_month_no
    1     628
    2     433
    3     422
    4     418
    5     278
    6     367
    7     457
    8     618
    9     630
    10    500
    11    722
    12    648
    dtype: int64



Calculating Skill Percentages 

- **Converting to Percentages:** dividing each value in the `df_da_ind_table` dataframe by the corresponding monthly job count from `df_da_ind_monthly_jobs`, then multiplying by 100. the result is a dataframe named `df_da_ind_table_percent` where each value represents the percentage of job postings for each skill in relation to the total number of data analyst jobs posted each month.


```python
df_da_ind_table_percent = df_da_ind_table.div(df_da_ind_monthly_jobs/100,axis=0)
df_da_ind_table_percent
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>skills</th>
      <th>sql</th>
      <th>python</th>
      <th>excel</th>
      <th>tableau</th>
      <th>power bi</th>
      <th>r</th>
      <th>sas</th>
      <th>azure</th>
      <th>aws</th>
      <th>powerpoint</th>
      <th>...</th>
      <th>hugging face</th>
      <th>fastapi</th>
      <th>kotlin</th>
      <th>powerbi</th>
      <th>mariadb</th>
      <th>sqlite</th>
      <th>clickup</th>
      <th>suse</th>
      <th>twilio</th>
      <th>centos</th>
    </tr>
    <tr>
      <th>posted_month_no</th>
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
      <th>1</th>
      <td>48.566879</td>
      <td>34.394904</td>
      <td>34.713376</td>
      <td>25.318471</td>
      <td>15.605096</td>
      <td>14.171975</td>
      <td>20.382166</td>
      <td>7.324841</td>
      <td>5.095541</td>
      <td>6.847134</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.159236</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.159236</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2</th>
      <td>48.267898</td>
      <td>34.180139</td>
      <td>36.027714</td>
      <td>26.789838</td>
      <td>17.321016</td>
      <td>15.473441</td>
      <td>18.937644</td>
      <td>6.004619</td>
      <td>7.621247</td>
      <td>5.773672</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>54.265403</td>
      <td>35.781991</td>
      <td>32.701422</td>
      <td>29.620853</td>
      <td>18.009479</td>
      <td>13.744076</td>
      <td>14.691943</td>
      <td>10.663507</td>
      <td>9.004739</td>
      <td>6.872038</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.236967</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.236967</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>48.803828</td>
      <td>34.210526</td>
      <td>33.014354</td>
      <td>23.444976</td>
      <td>19.856459</td>
      <td>13.397129</td>
      <td>12.440191</td>
      <td>9.569378</td>
      <td>7.416268</td>
      <td>6.698565</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>5</th>
      <td>55.755396</td>
      <td>36.330935</td>
      <td>38.129496</td>
      <td>25.539568</td>
      <td>21.942446</td>
      <td>15.107914</td>
      <td>10.791367</td>
      <td>11.870504</td>
      <td>7.913669</td>
      <td>6.834532</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.359712</td>
    </tr>
    <tr>
      <th>6</th>
      <td>52.588556</td>
      <td>40.871935</td>
      <td>31.335150</td>
      <td>31.062670</td>
      <td>20.980926</td>
      <td>20.708447</td>
      <td>20.163488</td>
      <td>10.081744</td>
      <td>8.719346</td>
      <td>6.539510</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>7</th>
      <td>53.610503</td>
      <td>35.229759</td>
      <td>38.074398</td>
      <td>27.133479</td>
      <td>20.350109</td>
      <td>14.660832</td>
      <td>17.067834</td>
      <td>8.533917</td>
      <td>6.783370</td>
      <td>6.783370</td>
      <td>...</td>
      <td>0.218818</td>
      <td>0.000000</td>
      <td>0.218818</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>8</th>
      <td>51.294498</td>
      <td>34.951456</td>
      <td>31.067961</td>
      <td>24.595469</td>
      <td>20.550162</td>
      <td>18.122977</td>
      <td>15.857605</td>
      <td>8.414239</td>
      <td>10.194175</td>
      <td>6.472492</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>9</th>
      <td>54.126984</td>
      <td>36.349206</td>
      <td>36.190476</td>
      <td>30.952381</td>
      <td>26.666667</td>
      <td>15.873016</td>
      <td>14.603175</td>
      <td>5.555556</td>
      <td>6.507937</td>
      <td>4.603175</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>10</th>
      <td>53.800000</td>
      <td>37.000000</td>
      <td>38.600000</td>
      <td>30.600000</td>
      <td>22.000000</td>
      <td>19.000000</td>
      <td>17.200000</td>
      <td>9.400000</td>
      <td>9.600000</td>
      <td>5.800000</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.2</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>11</th>
      <td>49.722992</td>
      <td>36.565097</td>
      <td>33.518006</td>
      <td>25.207756</td>
      <td>21.606648</td>
      <td>15.927978</td>
      <td>9.695291</td>
      <td>7.894737</td>
      <td>7.063712</td>
      <td>6.509695</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.138504</td>
      <td>0.138504</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>12</th>
      <td>51.388889</td>
      <td>36.882716</td>
      <td>33.487654</td>
      <td>27.469136</td>
      <td>25.000000</td>
      <td>17.592593</td>
      <td>15.432099</td>
      <td>8.487654</td>
      <td>4.629630</td>
      <td>4.320988</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
  </tbody>
</table>
<p>12 rows × 181 columns</p>
</div>



Formatting and Indexing

- **Resetting the Index:** resetting the index of the `df_da_ind_table_percent` dataframe, converting the existing index into a column.

- **Adding a New Column:** adding a new column `posted_month` by converting `posted_month_no` to a month name using `pd.to_datetime` and `strftime`.

- **Setting the New Index:** setting the new `posted_month` column as the index of the dataframe.

- **Dropping a Column:** dropping the `posted_month_no` column from the dataframe, keeping only the `posted_month` index and the percentage data.



```python
df_da_ind_table_percent.reset_index(inplace=True)
df_da_ind_table_percent['posted_month'] = df_da_ind_table_percent['posted_month_no'].apply(lambda g: pd.to_datetime(g,format= '%m').strftime('%b'))
df_da_ind_table_percent.set_index('posted_month',inplace=True)
df_da_ind_table_percent.drop(columns='posted_month_no',inplace=True)
df_da_ind_table_percent
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>skills</th>
      <th>sql</th>
      <th>python</th>
      <th>excel</th>
      <th>tableau</th>
      <th>power bi</th>
      <th>r</th>
      <th>sas</th>
      <th>azure</th>
      <th>aws</th>
      <th>powerpoint</th>
      <th>...</th>
      <th>hugging face</th>
      <th>fastapi</th>
      <th>kotlin</th>
      <th>powerbi</th>
      <th>mariadb</th>
      <th>sqlite</th>
      <th>clickup</th>
      <th>suse</th>
      <th>twilio</th>
      <th>centos</th>
    </tr>
    <tr>
      <th>posted_month</th>
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
      <th>Jan</th>
      <td>48.566879</td>
      <td>34.394904</td>
      <td>34.713376</td>
      <td>25.318471</td>
      <td>15.605096</td>
      <td>14.171975</td>
      <td>20.382166</td>
      <td>7.324841</td>
      <td>5.095541</td>
      <td>6.847134</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.159236</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.159236</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>Feb</th>
      <td>48.267898</td>
      <td>34.180139</td>
      <td>36.027714</td>
      <td>26.789838</td>
      <td>17.321016</td>
      <td>15.473441</td>
      <td>18.937644</td>
      <td>6.004619</td>
      <td>7.621247</td>
      <td>5.773672</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>Mar</th>
      <td>54.265403</td>
      <td>35.781991</td>
      <td>32.701422</td>
      <td>29.620853</td>
      <td>18.009479</td>
      <td>13.744076</td>
      <td>14.691943</td>
      <td>10.663507</td>
      <td>9.004739</td>
      <td>6.872038</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.236967</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.236967</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>Apr</th>
      <td>48.803828</td>
      <td>34.210526</td>
      <td>33.014354</td>
      <td>23.444976</td>
      <td>19.856459</td>
      <td>13.397129</td>
      <td>12.440191</td>
      <td>9.569378</td>
      <td>7.416268</td>
      <td>6.698565</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>May</th>
      <td>55.755396</td>
      <td>36.330935</td>
      <td>38.129496</td>
      <td>25.539568</td>
      <td>21.942446</td>
      <td>15.107914</td>
      <td>10.791367</td>
      <td>11.870504</td>
      <td>7.913669</td>
      <td>6.834532</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.359712</td>
    </tr>
    <tr>
      <th>Jun</th>
      <td>52.588556</td>
      <td>40.871935</td>
      <td>31.335150</td>
      <td>31.062670</td>
      <td>20.980926</td>
      <td>20.708447</td>
      <td>20.163488</td>
      <td>10.081744</td>
      <td>8.719346</td>
      <td>6.539510</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>Jul</th>
      <td>53.610503</td>
      <td>35.229759</td>
      <td>38.074398</td>
      <td>27.133479</td>
      <td>20.350109</td>
      <td>14.660832</td>
      <td>17.067834</td>
      <td>8.533917</td>
      <td>6.783370</td>
      <td>6.783370</td>
      <td>...</td>
      <td>0.218818</td>
      <td>0.000000</td>
      <td>0.218818</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>Aug</th>
      <td>51.294498</td>
      <td>34.951456</td>
      <td>31.067961</td>
      <td>24.595469</td>
      <td>20.550162</td>
      <td>18.122977</td>
      <td>15.857605</td>
      <td>8.414239</td>
      <td>10.194175</td>
      <td>6.472492</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>Sep</th>
      <td>54.126984</td>
      <td>36.349206</td>
      <td>36.190476</td>
      <td>30.952381</td>
      <td>26.666667</td>
      <td>15.873016</td>
      <td>14.603175</td>
      <td>5.555556</td>
      <td>6.507937</td>
      <td>4.603175</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>Oct</th>
      <td>53.800000</td>
      <td>37.000000</td>
      <td>38.600000</td>
      <td>30.600000</td>
      <td>22.000000</td>
      <td>19.000000</td>
      <td>17.200000</td>
      <td>9.400000</td>
      <td>9.600000</td>
      <td>5.800000</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.2</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>Nov</th>
      <td>49.722992</td>
      <td>36.565097</td>
      <td>33.518006</td>
      <td>25.207756</td>
      <td>21.606648</td>
      <td>15.927978</td>
      <td>9.695291</td>
      <td>7.894737</td>
      <td>7.063712</td>
      <td>6.509695</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.138504</td>
      <td>0.138504</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>Dec</th>
      <td>51.388889</td>
      <td>36.882716</td>
      <td>33.487654</td>
      <td>27.469136</td>
      <td>25.000000</td>
      <td>17.592593</td>
      <td>15.432099</td>
      <td>8.487654</td>
      <td>4.629630</td>
      <td>4.320988</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
  </tbody>
</table>
<p>12 rows × 181 columns</p>
</div>



Selecting Top 5 Skills for Plotting

- **Selecting Columns:** selecting the first five columns of the `df_da_ind_table_percent` dataframe to create a new dataframe named `df_da_ind_plot`, which includes only these selected columns for further plotting or analysis.


```python
df_da_ind_plot = df_da_ind_table_percent.iloc[:,:5]
df_da_ind_plot
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>skills</th>
      <th>sql</th>
      <th>python</th>
      <th>excel</th>
      <th>tableau</th>
      <th>power bi</th>
    </tr>
    <tr>
      <th>posted_month</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Jan</th>
      <td>48.566879</td>
      <td>34.394904</td>
      <td>34.713376</td>
      <td>25.318471</td>
      <td>15.605096</td>
    </tr>
    <tr>
      <th>Feb</th>
      <td>48.267898</td>
      <td>34.180139</td>
      <td>36.027714</td>
      <td>26.789838</td>
      <td>17.321016</td>
    </tr>
    <tr>
      <th>Mar</th>
      <td>54.265403</td>
      <td>35.781991</td>
      <td>32.701422</td>
      <td>29.620853</td>
      <td>18.009479</td>
    </tr>
    <tr>
      <th>Apr</th>
      <td>48.803828</td>
      <td>34.210526</td>
      <td>33.014354</td>
      <td>23.444976</td>
      <td>19.856459</td>
    </tr>
    <tr>
      <th>May</th>
      <td>55.755396</td>
      <td>36.330935</td>
      <td>38.129496</td>
      <td>25.539568</td>
      <td>21.942446</td>
    </tr>
    <tr>
      <th>Jun</th>
      <td>52.588556</td>
      <td>40.871935</td>
      <td>31.335150</td>
      <td>31.062670</td>
      <td>20.980926</td>
    </tr>
    <tr>
      <th>Jul</th>
      <td>53.610503</td>
      <td>35.229759</td>
      <td>38.074398</td>
      <td>27.133479</td>
      <td>20.350109</td>
    </tr>
    <tr>
      <th>Aug</th>
      <td>51.294498</td>
      <td>34.951456</td>
      <td>31.067961</td>
      <td>24.595469</td>
      <td>20.550162</td>
    </tr>
    <tr>
      <th>Sep</th>
      <td>54.126984</td>
      <td>36.349206</td>
      <td>36.190476</td>
      <td>30.952381</td>
      <td>26.666667</td>
    </tr>
    <tr>
      <th>Oct</th>
      <td>53.800000</td>
      <td>37.000000</td>
      <td>38.600000</td>
      <td>30.600000</td>
      <td>22.000000</td>
    </tr>
    <tr>
      <th>Nov</th>
      <td>49.722992</td>
      <td>36.565097</td>
      <td>33.518006</td>
      <td>25.207756</td>
      <td>21.606648</td>
    </tr>
    <tr>
      <th>Dec</th>
      <td>51.388889</td>
      <td>36.882716</td>
      <td>33.487654</td>
      <td>27.469136</td>
      <td>25.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python

```


```python
# Setting Up for Plot
sns.set_theme(style='ticks')

# Creating Plot
sns.lineplot(data=df_da_ind_plot, dashes= False, palette= 'tab10')

# Modifying Axes and Lables
from matplotlib.ticker import PercentFormatter
ax = plt.gca() # to get the current axes of the current figure
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))

for column in df_da_ind_plot.columns:
    plt.text(11.2, df_da_ind_plot[column].iloc[-1], column) # to add lables at the end of lines

plt.title('Skill Trends for Data Analysts India')
plt.ylabel('Likelihood in Job Posting')
plt.xlabel('2023')
plt.legend().remove()

# Display the plot
sns.despine() # to remove borders
plt.show()

```


    
![png](output_33_0.png)
    


# For Top 3 Data Jobs in India

Identifying Top 3 Job Titles

- **Finding Top Job Titles:** finding the top three most common job titles in the `job` column of the dataframe by counting occurrences and selecting the most frequent ones.

- **Converting to List:** converting these job titles to a list and assigning it to `job_list`.


```python
job_list = df['job'].value_counts().head(3).index.to_list()
job_list
```




    ['Data Analyst', 'Data Engineer', 'Data Scientist']



Processing and Analyzing Top 3 Job Titles

- **Initializing Dictionary:** initializing an empty dictionary named `top3_jobs`.

- **Looping Through Job Titles:** looping through each job title in `job_list`:

  - filtering the dataframe to include only rows where the job title matches the current job and the country is `'India'`, creating a new dataframe `df_ind`. adding a new column `posted_month_no` by extracting the month from `posted_dt`.
  
  - exploding the `skills` column to create a new dataframe `df_ind_exp`, where each skill in the list becomes its own row.
  
  - creating a pivot table from `df_ind_exp` with `posted_month_no` as the index and `skills` as the columns, aggregating by count. adding a 'total' row to the pivot table with the sum of each skill across all months and reordering the columns based on these totals. dropping the 'total' row.
  
  - calculating the monthly job counts and creating a percentage table `df_ind_table_percent` by dividing each value in the pivot table by the corresponding monthly job count, then resetting the index.
  
  - converting `posted_month_no` to month names and setting this as the new index. dropping the `posted_month_no` column.
  
  - selecting the first five columns of `df_ind_table_percent` to create `df_ind_plot`.

- **Storing Results:** storing `df_ind_plot` in the `top3_jobs` dictionary with the job title as the key.



```python

top3_jobs = {}

for i in job_list:

    df_ind = df[(df['job']== i) & (df['country']== 'India')].copy()
    df_ind['posted_month_no'] = df_ind['posted_dt'].dt.month
    df_ind_exp = df_ind.explode('skills')
    df_ind_table = df_ind_exp.pivot_table(index='posted_month_no', columns='skills',aggfunc= 'size', fill_value= 0)
    df_ind_table.loc['total'] = df_ind_table.sum()
    df_ind_table = df_ind_table[df_ind_table.loc['total'].sort_values(ascending=False).index]
    df_ind_table = df_ind_table.drop('total')
    df_ind_monthly_jobs = df_ind.groupby('posted_month_no').size()
    df_ind_table_percent = df_ind_table.div(df_ind_monthly_jobs/100,axis=0)
    df_ind_table_percent.reset_index(inplace=True)
    df_ind_table_percent['posted_month'] = df_ind_table_percent['posted_month_no'].apply(lambda g: pd.to_datetime(g,format= '%m').strftime('%b'))
    df_ind_table_percent.set_index('posted_month',inplace=True)
    df_ind_table_percent.drop(columns='posted_month_no',inplace=True)
    df_ind_plot = df_ind_table_percent.iloc[:,:5]

    top3_jobs[i] = df_ind_plot
                         
```

Accessing Skill Percentage Data for Data Engineer Jobs in India


```python
top3_jobs['Data Engineer']
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>skills</th>
      <th>sql</th>
      <th>python</th>
      <th>spark</th>
      <th>aws</th>
      <th>azure</th>
    </tr>
    <tr>
      <th>posted_month</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Jan</th>
      <td>68.433396</td>
      <td>61.913696</td>
      <td>39.118199</td>
      <td>35.600375</td>
      <td>35.881801</td>
    </tr>
    <tr>
      <th>Feb</th>
      <td>69.466585</td>
      <td>60.944206</td>
      <td>40.159411</td>
      <td>35.683630</td>
      <td>33.905579</td>
    </tr>
    <tr>
      <th>Mar</th>
      <td>67.441860</td>
      <td>61.596480</td>
      <td>38.654934</td>
      <td>37.209302</td>
      <td>33.123821</td>
    </tr>
    <tr>
      <th>Apr</th>
      <td>68.454662</td>
      <td>59.131545</td>
      <td>39.208174</td>
      <td>36.206897</td>
      <td>33.333333</td>
    </tr>
    <tr>
      <th>May</th>
      <td>66.112717</td>
      <td>59.898844</td>
      <td>39.595376</td>
      <td>37.138728</td>
      <td>33.815029</td>
    </tr>
    <tr>
      <th>Jun</th>
      <td>68.382353</td>
      <td>59.681373</td>
      <td>39.460784</td>
      <td>36.887255</td>
      <td>36.519608</td>
    </tr>
    <tr>
      <th>Jul</th>
      <td>68.848168</td>
      <td>58.965969</td>
      <td>34.489529</td>
      <td>37.238220</td>
      <td>38.808901</td>
    </tr>
    <tr>
      <th>Aug</th>
      <td>66.453447</td>
      <td>56.716418</td>
      <td>36.247335</td>
      <td>37.953092</td>
      <td>34.470505</td>
    </tr>
    <tr>
      <th>Sep</th>
      <td>66.047745</td>
      <td>58.753316</td>
      <td>33.753316</td>
      <td>35.079576</td>
      <td>35.344828</td>
    </tr>
    <tr>
      <th>Oct</th>
      <td>68.495935</td>
      <td>61.314363</td>
      <td>38.075881</td>
      <td>37.466125</td>
      <td>37.262873</td>
    </tr>
    <tr>
      <th>Nov</th>
      <td>69.535284</td>
      <td>64.371773</td>
      <td>36.947791</td>
      <td>37.062536</td>
      <td>38.324727</td>
    </tr>
    <tr>
      <th>Dec</th>
      <td>69.603825</td>
      <td>63.729508</td>
      <td>33.811475</td>
      <td>37.295082</td>
      <td>38.183060</td>
    </tr>
  </tbody>
</table>
</div>




```python
from adjustText import adjust_text
from matplotlib.ticker import PercentFormatter

# Setting Up for Plot
sns.set_theme(style='ticks')
fig, ax = plt.subplots(len(top3_jobs),1,figsize = (8,7))

# Creating Plot
for i,(key,value) in enumerate(top3_jobs.items()):
    sns.lineplot(data=value, dashes= False, palette= 'tab10', ax=ax[i], legend=False)

    # Modifying Axes and Labels
    ax[i].yaxis.set_major_formatter(PercentFormatter(decimals=0))

    # Preperaing texts for adjustText
    texts = []
    for column in value.columns:
        texts.append(ax[i].text(11.2, value[column].iloc[-1], column, fontsize=11)) 
    
    # Adjusting text to avoid overlap
    adjust_text(texts,ax=ax[i],arrowprops=dict(arrowstyle='->', color='gray'))

    ax[i].set_title(key)
    ax[i].set_xlabel('')
    ax[i].set_ylabel('Likelihood in Job Posting', fontsize = 10)
    ax[i].set_ylim(0,75)

ax[2].set_xlabel('2023')

# Modifying the entire figure
plt.suptitle('Skill Trends Over the Year in India')

# Displaying the plot
sns.despine() # to remove borders
plt.tight_layout()
plt.show()

```


    
![png](output_43_0.png)
    


<span style="color:#d7ba7d; font-size:50px;"> End </span>

---
