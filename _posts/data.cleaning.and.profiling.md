[data_cleaning_and_profiling.md](https://github.com/user-attachments/files/24401698/data_cleaning_and_profiling.md)[Uploa# D599 Task 1: Data Cleaning and Profiling


```python
import pandas as pd

# File path
file_path = '/Users/meredithsmith/PycharmProjects/PythonProject/PythonProject/PythonProject19/.venv/lib/Employee Turnover Dataset.csv'
df = pd.read_csv(file_path, usecols = ['EmployeeNumber', 'Age', 'Tenure', 'Turnover', 'HourlyRate ', 'HoursWeekly', 'CompensationType', 'AnnualSalary', 'DrivingCommuterDistance', 'JobRoleArea', 'Gender', 'MaritalStatus', 'NumCompaniesPreviouslyWorked', 'AnnualProfessionalDevHrs', 'PaycheckMethod', 'TextMessageOptIn'])

```

# Part 1: Data Profiling
## A1
Identify the dataset's number of rows and columns


```python

```




    (10199, 16)



## A2
List each variable and indicate the variable's data type


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 10199 entries, 0 to 10198
    Data columns (total 16 columns):
     #   Column                        Non-Null Count  Dtype  
    ---  ------                        --------------  -----  
     0   EmployeeNumber                10199 non-null  int64  
     1   Age                           10199 non-null  int64  
     2   Tenure                        10199 non-null  int64  
     3   Turnover                      10199 non-null  object 
     4   HourlyRate                    10199 non-null  object 
     5   HoursWeekly                   10199 non-null  int64  
     6   CompensationType              10199 non-null  object 
     7   AnnualSalary                  10199 non-null  float64
     8   DrivingCommuterDistance       10199 non-null  int64  
     9   JobRoleArea                   10199 non-null  object 
     10  Gender                        10199 non-null  object 
     11  MaritalStatus                 10199 non-null  object 
     12  NumCompaniesPreviouslyWorked  9534 non-null   float64
     13  AnnualProfessionalDevHrs      8230 non-null   float64
     14  PaycheckMethod                10199 non-null  object 
     15  TextMessageOptIn              7933 non-null   object 
    dtypes: float64(3), int64(5), object(8)
    memory usage: 1.2+ MB


##### Variables							        Data Type
##### 1 Employee number					        Quantitative/Discrete
##### 2 Age							            Quantitative/Discrete
##### 3 Tenure							        Quantitative/Discrete
##### 4 Turnover							    Qualitative/Nominal
##### 5 HourlyRate						        Quantitative/Continuous
##### 6 HoursWeekly                             Quantitative/Continuous
##### 7 CompensationType						Qualitative/Nominal
##### 8 AnnualSalary						    Quantitative/Continuous
##### 9 DrivingCommuterDistance					Quantitative/Discrete
##### 10 JobRole  						        Qualitative/Nominal
##### 11 Gender							        Qualitative/Nominal
##### 12 MaritalStatus						    Qualitative/Nominal
##### 13 NumCompaniesPreviouslyWorked		    Quantitative/Discrete
##### 14 AnnualProfessionalDevHrs			    Quantitative/Discrete
##### 15 PayCheckMethod 					    Qualitative/Nominal
##### 16 TextMessageOptIn					    Qualitative/Nominal


## A3
## Identify Values for Each Variable



```python
print(df.head())
```

       EmployeeNumber  Age  Tenure Turnover HourlyRate   HoursWeekly  \
    0               1   28       6      Yes     $24.37            40   
    1               2   33       2      Yes     $24.37            40   
    2               3   22       1       No     $22.52            40   
    3               4   23       1       No     $22.52            40   
    4               5   40       6       No     $88.77            40   
    
      CompensationType  AnnualSalary  DrivingCommuterDistance  \
    0           Salary       50689.6                       89   
    1           Salary       50689.6                       89   
    2           Salary       46841.6                       35   
    3           Salary       46841.6                       35   
    4           Salary      284641.6                       12   
    
                  JobRoleArea                Gender MaritalStatus  \
    0                Research                Female       Married   
    1                Research                Female       Married   
    2  Information_Technology                Female        Single   
    3  Information_Technology                Female        Single   
    4                   Sales  Prefer Not to Answer        Single   
    
       NumCompaniesPreviouslyWorked  AnnualProfessionalDevHrs PaycheckMethod  \
    0                           3.0                       7.0     Mail Check   
    1                           6.0                       7.0     Mail Check   
    2                           1.0                       8.0   Mailed Check   
    3                           3.0                       NaN   Mailed Check   
    4                           7.0                       NaN     Mail Check   
    
      TextMessageOptIn  
    0              Yes  
    1              Yes  
    2              Yes  
    3              Yes  
    4              Yes  


# Part II: Data Cleaning and Plan


## B1 Find Duplicate Rows


```python
df2=df.copy()

# Duplicates
print("\nDuplicate rows:", df.duplicated().sum()) #99 rows x 16 columns
print("\nDuplicate rows preview:")
print(df2[df2.duplicated()].head())

df2=df2.drop_duplicates()
print(df2) #10100, 16
```

    
    Duplicate rows: 99
    
    Duplicate rows preview:
           EmployeeNumber  Age  Tenure Turnover HourlyRate   HoursWeekly  \
    10100               1   28       6      Yes     $24.37            40   
    10101               2   33       2      Yes     $24.37            40   
    10102               3   22       1       No     $22.52            40   
    10103               4   23       1       No     $22.52            40   
    10104               5   40       6       No     $88.77            40   
    
          CompensationType  AnnualSalary  DrivingCommuterDistance  \
    10100           Salary       50689.6                       89   
    10101           Salary       50689.6                       89   
    10102           Salary       46841.6                       35   
    10103           Salary       46841.6                       35   
    10104           Salary      284641.6                       12   
    
                      JobRoleArea                Gender MaritalStatus  \
    10100                Research                Female       Married   
    10101                Research                Female       Married   
    10102  Information_Technology                Female        Single   
    10103  Information_Technology                Female        Single   
    10104                   Sales  Prefer Not to Answer        Single   
    
           NumCompaniesPreviouslyWorked  AnnualProfessionalDevHrs PaycheckMethod  \
    10100                           3.0                       7.0     Mail Check   
    10101                           6.0                       7.0     Mail Check   
    10102                           1.0                       8.0   Mailed Check   
    10103                           3.0                       NaN   Mailed Check   
    10104                           7.0                       NaN     Mail Check   
    
          TextMessageOptIn  
    10100              Yes  
    10101              Yes  
    10102              Yes  
    10103              Yes  
    10104              Yes  
           EmployeeNumber  Age  Tenure Turnover HourlyRate   HoursWeekly  \
    0                   1   28       6      Yes     $24.37            40   
    1                   2   33       2      Yes     $24.37            40   
    2                   3   22       1       No     $22.52            40   
    3                   4   23       1       No     $22.52            40   
    4                   5   40       6       No     $88.77            40   
    ...               ...  ...     ...      ...         ...          ...   
    10095           10096   50      15      Yes     $61.78            40   
    10096           10097   33       9      Yes     $23.28            40   
    10097           10098   31       9      Yes     $28.25            40   
    10098           10099   50      12       No     $32.22            40   
    10099           10100   59      14       No     $44.59            40   
    
          CompensationType  AnnualSalary  DrivingCommuterDistance  \
    0               Salary       50689.6                       89   
    1               Salary       50689.6                       89   
    2               Salary       46841.6                       35   
    3               Salary       46841.6                       35   
    4               Salary      284641.6                       12   
    ...                ...           ...                      ...   
    10095           Salary      128502.4                        6   
    10096           Salary       48422.4                      -10   
    10097           Salary       37960.0                       68   
    10098           Salary       67017.6                      -13   
    10099           Salary       92747.2                       94   
    
                      JobRoleArea                Gender MaritalStatus  \
    0                    Research                Female       Married   
    1                    Research                Female       Married   
    2      Information_Technology                Female        Single   
    3      Information_Technology                Female        Single   
    4                       Sales  Prefer Not to Answer        Single   
    ...                       ...                   ...           ...   
    10095              Laboratory                  Male      Divorced   
    10096               Marketing                  Male        Single   
    10097              Laboratory                  Male       Married   
    10098                Research                Female       Married   
    10099                Research                  Male       Married   
    
           NumCompaniesPreviouslyWorked  AnnualProfessionalDevHrs  PaycheckMethod  \
    0                               3.0                       7.0      Mail Check   
    1                               6.0                       7.0      Mail Check   
    2                               1.0                       8.0    Mailed Check   
    3                               3.0                       NaN    Mailed Check   
    4                               7.0                       NaN      Mail Check   
    ...                             ...                       ...             ...   
    10095                           1.0                       8.0      Mail Check   
    10096                           1.0                      20.0  Direct_Deposit   
    10097                           2.0                      21.0   DirectDeposit   
    10098                           5.0                      20.0  Direct_Deposit   
    10099                           NaN                      10.0   DirectDeposit   
    
          TextMessageOptIn  
    0                  Yes  
    1                  Yes  
    2                  Yes  
    3                  Yes  
    4                  Yes  
    ...                ...  
    10095              Yes  
    10096              Yes  
    10097              NaN  
    10098              Yes  
    10099              NaN  
    
    [10100 rows x 16 columns]


##### B1 Inspection:

##### df.duplicated().sum() identifies duplicate rows
##### df.drop_duplicates() removes the duplicates to a new dataframe

##### B2 Quality Issue Findings:

##### •	Found and deleted 99 duplicate rows

## B1 Inconsistent Entries



```python
# Unique values per column
for col in df2.columns:
    unique_vals = df2[col].nunique()
    print(f"{col}: {unique_vals} unique values")
```

    EmployeeNumber: 10100 unique values
    Age: 41 unique values
    Tenure: 20 unique values
    Turnover: 2 unique values
    HourlyRate : 5244 unique values
    HoursWeekly: 1 unique values
    CompensationType: 1 unique values
    AnnualSalary: 5538 unique values
    DrivingCommuterDistance: 120 unique values
    JobRoleArea: 12 unique values
    Gender: 3 unique values
    MaritalStatus: 3 unique values
    NumCompaniesPreviouslyWorked: 9 unique values
    AnnualProfessionalDevHrs: 21 unique values
    PaycheckMethod: 7 unique values
    TextMessageOptIn: 2 unique values



```python
# Inconsistent categories
for col in df.select_dtypes(include='object').columns:
    print(f"\nColumn: {col}")
    print(df[col].value_counts(dropna=False).head(10))  # top 10 categories
```

    
    Column: Turnover
    Turnover
    No     5509
    Yes    4690
    Name: count, dtype: int64
    
    Column: HourlyRate 
    HourlyRate 
    $34.28     11
    $26.28     11
    $31.28     10
    $33.66     10
    $31.39     10
    $28.73     10
    $33.06      9
    $28.09      9
    $85.40      9
    $36.68      9
    Name: count, dtype: int64
    
    Column: CompensationType
    CompensationType
    Salary    10199
    Name: count, dtype: int64
    
    Column: JobRoleArea
    JobRoleArea
    Research                  2025
    Sales                     2007
    Marketing                 1105
    Manufacturing             1039
    Laboratory                1021
    Healthcare                1008
    Human Resources            909
    Information Technology     857
    InformationTechnology       80
    Information_Technology      56
    Name: count, dtype: int64
    
    Column: Gender
    Gender
    Female                  5812
    Male                    4232
    Prefer Not to Answer     155
    Name: count, dtype: int64
    
    Column: MaritalStatus
    MaritalStatus
    Married     3439
    Single      3422
    Divorced    3338
    Name: count, dtype: int64
    
    Column: PaycheckMethod
    PaycheckMethod
    Mail Check        4986
    Mailed Check      2441
    DirectDeposit      992
    Direct_Deposit     958
    Mail_Check         547
    Direct Deposit     226
    MailedCheck         49
    Name: count, dtype: int64
    
    Column: TextMessageOptIn
    TextMessageOptIn
    Yes    7390
    NaN    2266
    No      543
    Name: count, dtype: int64



```python
#Qualitative
# Normalize JobRoleArea
df3=df2.copy()
df3['JobRoleArea'] = df3['JobRoleArea'].astype(str).str.strip().str.title()

# Define mapping dictionary
mapping = {
    'Information Technology': 'Info_Tech',
    'Information_technology': 'Info_Tech',
    'Informationtechnology': 'Info_Tech',
    'Human Resources': 'Human_Resources',
    'HumanResources': 'Human_Resources'
}

# Apply mapping to a new column
df3['JobRole'] = df3['JobRoleArea'].map(mapping).fillna(df3['JobRoleArea'])
df3['JobRole'].value_counts(dropna=False)

#Quantitative
# Normalize PaycheckMethod
df3['PaycheckMethod'] = df3['PaycheckMethod'].astype(str).str.strip().str.title()

# Define mapping dictionary
mapping = {
    'Mail Check': 'Mailed_Check',
    'Mailed Check': 'Mailed_Check',
    'Mail_Check': 'Mailed_Check',
    'Mailedcheck': 'Mailed_Check',
    'Directdeposit': 'Direct_Deposit',
    'Direct Deposit': 'Direct_Deposit'
}

# Apply mapping to a new column
df3['PayMethod'] = df3['PaycheckMethod'].map(mapping).fillna(df3['PaycheckMethod'])
df3['PayMethod'].value_counts(dropna=False)

#drop old columns
df3.drop(['PaycheckMethod', 'JobRoleArea'], axis=1, inplace=True)
 #10100x16
```




    <bound method DataFrame.info of        EmployeeNumber  Age  Tenure Turnover HourlyRate   HoursWeekly  \
    0                   1   28       6      Yes     $24.37            40   
    1                   2   33       2      Yes     $24.37            40   
    2                   3   22       1       No     $22.52            40   
    3                   4   23       1       No     $22.52            40   
    4                   5   40       6       No     $88.77            40   
    ...               ...  ...     ...      ...         ...          ...   
    10095           10096   50      15      Yes     $61.78            40   
    10096           10097   33       9      Yes     $23.28            40   
    10097           10098   31       9      Yes     $28.25            40   
    10098           10099   50      12       No     $32.22            40   
    10099           10100   59      14       No     $44.59            40   
    
          CompensationType  AnnualSalary  DrivingCommuterDistance  \
    0               Salary       50689.6                       89   
    1               Salary       50689.6                       89   
    2               Salary       46841.6                       35   
    3               Salary       46841.6                       35   
    4               Salary      284641.6                       12   
    ...                ...           ...                      ...   
    10095           Salary      128502.4                        6   
    10096           Salary       48422.4                      -10   
    10097           Salary       37960.0                       68   
    10098           Salary       67017.6                      -13   
    10099           Salary       92747.2                       94   
    
                         Gender MaritalStatus  NumCompaniesPreviouslyWorked  \
    0                    Female       Married                           3.0   
    1                    Female       Married                           6.0   
    2                    Female        Single                           1.0   
    3                    Female        Single                           3.0   
    4      Prefer Not to Answer        Single                           7.0   
    ...                     ...           ...                           ...   
    10095                  Male      Divorced                           1.0   
    10096                  Male        Single                           1.0   
    10097                  Male       Married                           2.0   
    10098                Female       Married                           5.0   
    10099                  Male       Married                           NaN   
    
           AnnualProfessionalDevHrs TextMessageOptIn                 JobRole  \
    0                           7.0              Yes                Research   
    1                           7.0              Yes                Research   
    2                           8.0              Yes  Information_Technology   
    3                           NaN              Yes  Information_Technology   
    4                           NaN              Yes                   Sales   
    ...                         ...              ...                     ...   
    10095                       8.0              Yes              Laboratory   
    10096                      20.0              Yes               Marketing   
    10097                      21.0              NaN              Laboratory   
    10098                      20.0              Yes                Research   
    10099                      10.0              NaN                Research   
    
                PayMethod  
    0        Mailed_Check  
    1        Mailed_Check  
    2        Mailed_Check  
    3        Mailed_Check  
    4        Mailed_Check  
    ...               ...  
    10095    Mailed_Check  
    10096  Direct_Deposit  
    10097  Direct_Deposit  
    10098  Direct_Deposit  
    10099  Direct_Deposit  
    
    [10100 rows x 16 columns]>



##### B2 Quality Issue Findings
##### B1Inconsistent Entries
##### •	The column ‘JobRoleArea’ had multiple variations for entries ‘information technology’ and ‘human resources’
##### •	The column ‘PayCheckMethod’ had multiple variations for ‘Mailed_Check’ and ‘Direct Deposit’
#####	Do the same steps for ‘PayCheckMethod’ as ‘JobRoleArea’ to correct inconsistent entries

##### •	Create a mapping dictionary to correct spacing, white space, and capitalization inconsistencies
##### •	Rename column and drop old column

## B1 Formatting Errors


```python
df.describe()
```




<div>
<style >
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
<table  class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>EmployeeNumber</th>
      <th>Age</th>
      <th>Tenure</th>
      <th>HoursWeekly</th>
      <th>AnnualSalary</th>
      <th>DrivingCommuterDistance</th>
      <th>NumCompaniesPreviouslyWorked</th>
      <th>AnnualProfessionalDevHrs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>10199.000000</td>
      <td>10199.000000</td>
      <td>10199.000000</td>
      <td>10199.0</td>
      <td>10199.000000</td>
      <td>10199.000000</td>
      <td>9534.000000</td>
      <td>8230.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>5001.960977</td>
      <td>44.028826</td>
      <td>8.992744</td>
      <td>40.0</td>
      <td>120947.568526</td>
      <td>45.411903</td>
      <td>4.214810</td>
      <td>14.938518</td>
    </tr>
    <tr>
      <th>std</th>
      <td>2942.709195</td>
      <td>10.217864</td>
      <td>5.511985</td>
      <td>0.0</td>
      <td>77566.715759</td>
      <td>54.011750</td>
      <td>2.481994</td>
      <td>6.087415</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>21.000000</td>
      <td>1.000000</td>
      <td>40.0</td>
      <td>-33326.400000</td>
      <td>-275.000000</td>
      <td>1.000000</td>
      <td>5.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2451.500000</td>
      <td>37.000000</td>
      <td>5.000000</td>
      <td>40.0</td>
      <td>63252.800000</td>
      <td>13.000000</td>
      <td>2.000000</td>
      <td>10.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>5001.000000</td>
      <td>44.000000</td>
      <td>8.000000</td>
      <td>40.0</td>
      <td>101566.400000</td>
      <td>42.000000</td>
      <td>4.000000</td>
      <td>15.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>7550.500000</td>
      <td>53.000000</td>
      <td>13.000000</td>
      <td>40.0</td>
      <td>153878.400000</td>
      <td>71.000000</td>
      <td>6.000000</td>
      <td>20.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>10100.000000</td>
      <td>61.000000</td>
      <td>20.000000</td>
      <td>40.0</td>
      <td>339950.400000</td>
      <td>950.000000</td>
      <td>9.000000</td>
      <td>25.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Strip whitespace from column names
df3.columns = df3.columns.str.strip()

# Convert all numeric values to absolute (positive) values
df3[df3.select_dtypes(include='number').columns] = df3.select_dtypes(include='number').abs()

# Clean string columns: strip and title-case
for col in df3.select_dtypes(include='object').columns:
    df3[col] = df3[col].str.strip().str.title()

# inspect value counts across all columns
print(df3.value_counts(dropna=False))

# Clean and convert to float
df3['AnnualSalary'] = (df3['AnnualSalary'].astype(float)
)

# Format for display
df3['AnnualSalary'] = df3['AnnualSalary'].apply(lambda x: "${:,.2f}".format(x))

```

    EmployeeNumber  Age  Tenure  Turnover  HourlyRate  HoursWeekly  CompensationType  AnnualSalary  DrivingCommuterDistance  Gender  MaritalStatus  NumCompaniesPreviouslyWorked  AnnualProfessionalDevHrs  TextMessageOptIn  JobRole        PayMethod     
    1               28   6       Yes       $24.37      40           Salary            50689.6       89                       Female  Married        3.0                           7.0                       Yes               Research       Mailed_Check      1
    6738            37   7       No        $32.09      40           Salary            66747.2       52                       Male    Married        1.0                           21.0                      Yes               Info_Tech      Mailed_Check      1
    6731            28   5       No        $23.33      40           Salary            48526.4       11                       Female  Divorced       1.0                           24.0                      NaN               Info_Tech      Mailed_Check      1
    6732            52   15      Yes       $93.22      40           Salary            333897.6      53                       Female  Divorced       NaN                           NaN                       Yes               Manufacturing  Mailed_Check      1
    6733            58   7       Yes       $94.53      40           Salary            336622.4      92                       Male    Married        6.0                           18.0                      Yes               Manufacturing  Mailed_Check      1
                                                                                                                                                                                                                                                              ..
    3367            48   19      No        $92.51      40           Salary            332420.8      12                       Female  Single         7.0                           12.0                      NaN               Research       Mailed_Check      1
    3368            28   4       Yes       $23.80      40           Salary            49504.0       71                       Female  Married        3.0                           10.0                      NaN               Sales          Mailed_Check      1
    3369            55   17      Yes       $43.84      40           Salary            91287.2       44                       Male    Single         7.0                           17.0                      NaN               Marketing      Mailed_Check      1
    3370            45   15      Yes       $71.11      40           Salary            147908.8      12                       Male    Single         4.0                           18.0                      No                Manufacturing  Direct_Deposit    1
    10100           59   14      No        $44.59      40           Salary            92747.2       94                       Male    Married        NaN                           10.0                      NaN               Research       Direct_Deposit    1
    Name: count, Length: 10100, dtype: int64



```python
df.describe()
```




<div>
<style >
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
<table  >
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>EmployeeNumber</th>
      <th>Age</th>
      <th>Tenure</th>
      <th>HoursWeekly</th>
      <th>AnnualSalary</th>
      <th>DrivingCommuterDistance</th>
      <th>NumCompaniesPreviouslyWorked</th>
      <th>AnnualProfessionalDevHrs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>10199.000000</td>
      <td>10199.000000</td>
      <td>10199.000000</td>
      <td>10199.0</td>
      <td>10199.000000</td>
      <td>10199.000000</td>
      <td>9534.000000</td>
      <td>8230.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>5001.960977</td>
      <td>44.028826</td>
      <td>8.992744</td>
      <td>40.0</td>
      <td>120947.568526</td>
      <td>45.411903</td>
      <td>4.214810</td>
      <td>14.938518</td>
    </tr>
    <tr>
      <th>std</th>
      <td>2942.709195</td>
      <td>10.217864</td>
      <td>5.511985</td>
      <td>0.0</td>
      <td>77566.715759</td>
      <td>54.011750</td>
      <td>2.481994</td>
      <td>6.087415</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>21.000000</td>
      <td>1.000000</td>
      <td>40.0</td>
      <td>-33326.400000</td>
      <td>-275.000000</td>
      <td>1.000000</td>
      <td>5.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2451.500000</td>
      <td>37.000000</td>
      <td>5.000000</td>
      <td>40.0</td>
      <td>63252.800000</td>
      <td>13.000000</td>
      <td>2.000000</td>
      <td>10.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>5001.000000</td>
      <td>44.000000</td>
      <td>8.000000</td>
      <td>40.0</td>
      <td>101566.400000</td>
      <td>42.000000</td>
      <td>4.000000</td>
      <td>15.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>7550.500000</td>
      <td>53.000000</td>
      <td>13.000000</td>
      <td>40.0</td>
      <td>153878.400000</td>
      <td>71.000000</td>
      <td>6.000000</td>
      <td>20.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>10100.000000</td>
      <td>61.000000</td>
      <td>20.000000</td>
      <td>40.0</td>
      <td>339950.400000</td>
      <td>950.000000</td>
      <td>9.000000</td>
      <td>25.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Length checks
for col in df3.select_dtypes(include='object').columns:
    lengths = df3[col].str.len()
    print(f"{col} min length: {lengths.min()}, max length: {lengths.max()}")
```

    Turnover min length: 2, max length: 3
    HourlyRate min length: 6, max length: 6
    CompensationType min length: 6, max length: 6
    AnnualSalary min length: 9, max length: 11
    Gender min length: 4, max length: 20
    MaritalStatus min length: 6, max length: 8
    TextMessageOptIn min length: 2.0, max length: 3.0
    JobRole min length: 5, max length: 22
    PayMethod min length: 12, max length: 14


# B1 Missing Values



```python
import numpy as np

# Step 1: Check total missing values
print("Total missing values:", df3.isna().sum().sum())

# Step 2: Check missing values per column
print("Missing values per column:\n", df3.isna().sum())

# Step 3: Compute integer means for numeric columns
numeric_means = df3.select_dtypes(include=[np.number]).mean().round().astype(int)

# Step 4: Fill NaN in numeric columns with their integer mean
df3.fillna(value=numeric_means, inplace=True)

# Step 5: Convert all numeric columns to integer dtype
for col in df3.select_dtypes(include=[np.number]).columns:
    df3[col] = df3[col].astype(int)

# Step 6: Verify results
print("Missing values after fill:\n", df3.isna().sum())
print("Data types after conversion:\n", df3.dtypes)

# Percentage missing
missing_pct = df3.isna().mean().round(4) * 100
print("\nMissing value percentage per column:")
print(missing_pct)
```

    Total missing values: 4868
    Missing values per column:
     EmployeeNumber                     0
    Age                                0
    Tenure                             0
    Turnover                           0
    HourlyRate                         0
    HoursWeekly                        0
    CompensationType                   0
    AnnualSalary                       0
    DrivingCommuterDistance            0
    Gender                             0
    MaritalStatus                      0
    NumCompaniesPreviouslyWorked     663
    AnnualProfessionalDevHrs        1947
    TextMessageOptIn                2258
    JobRole                            0
    PayMethod                          0
    dtype: int64
    Missing values after fill:
     EmployeeNumber                     0
    Age                                0
    Tenure                             0
    Turnover                           0
    HourlyRate                         0
    HoursWeekly                        0
    CompensationType                   0
    AnnualSalary                       0
    DrivingCommuterDistance            0
    Gender                             0
    MaritalStatus                      0
    NumCompaniesPreviouslyWorked       0
    AnnualProfessionalDevHrs           0
    TextMessageOptIn                2258
    JobRole                            0
    PayMethod                          0
    dtype: int64
    Data types after conversion:
     EmployeeNumber                   int64
    Age                              int64
    Tenure                           int64
    Turnover                        object
    HourlyRate                      object
    HoursWeekly                      int64
    CompensationType                object
    AnnualSalary                    object
    DrivingCommuterDistance          int64
    Gender                          object
    MaritalStatus                   object
    NumCompaniesPreviouslyWorked     int64
    AnnualProfessionalDevHrs         int64
    TextMessageOptIn                object
    JobRole                         object
    PayMethod                       object
    dtype: object
    
    Missing value percentage per column:
    EmployeeNumber                   0.00
    Age                              0.00
    Tenure                           0.00
    Turnover                         0.00
    HourlyRate                       0.00
    HoursWeekly                      0.00
    CompensationType                 0.00
    AnnualSalary                     0.00
    DrivingCommuterDistance          0.00
    Gender                           0.00
    MaritalStatus                    0.00
    NumCompaniesPreviouslyWorked     0.00
    AnnualProfessionalDevHrs         0.00
    TextMessageOptIn                22.36
    JobRole                          0.00
    PayMethod                        0.00
    dtype: float64



```python
df3.replace("", np.nan, inplace=True)   # turn empty strings into NaN
df3.fillna('NS', inplace=True)             # then replace NaN with 0 (or another value)
```


##### B1 Inspection:

##### o	Df2.isna().sum().sum() gives missing counts per column and adds those counts together

##### o	Df2.fillna(df2.mean(numeric_only=True), inplace=True) calculates the mean of each numeric column, ensuring only numeric columns are considered column, and replaces the NaN values with the mean of that column


##### B2 Quality Issue Findings:
##### B.1.2 Missing Values
##### •	Text Message Opt In: 						    2258 missing values
##### •	Annual Professional Dev Hrs :					1947 missing values
##### •	Num Companies Previously Worked:	 			663 missing values


## B1 Outliers


```python
numeric_cols = df3.select_dtypes(include='number').columns
q1 = df3[numeric_cols].quantile(0.25)
q3 = df3[numeric_cols].quantile(0.75)
iqr = q3 - q1
lower_limit = q1 - 1.5 * iqr
upper_limit = q3 + 1.5 * iqr

# Flag outliers
low_outliers = (df3[numeric_cols] < lower_limit).any(axis=1)
high_outliers = (df3[numeric_cols] > upper_limit).any(axis=1)
outliers = df3[low_outliers | high_outliers]

# Totals
total_rows = df3.shape[0]
num_outliers = outliers.shape[0]
percent_outliers = (num_outliers / total_rows) * 100

# Column-level counts
outlier_counts = ((df3[numeric_cols] < lower_limit) | (df3[numeric_cols] > upper_limit)).sum()

# Build one summary table
summary_df = pd.DataFrame({
    "Q1": q1.abs(),
    "Q3": q3.abs(),
    "IQR": iqr.abs(),
    "Lower Limit": lower_limit.abs(),
    "Upper Limit": upper_limit.abs(),
    "Outlier Count": outlier_counts.abs()
})

# Print condensed summary
print(f"\n--- Outlier Summary ---")
print(f"Total rows: {total_rows} | Outlier rows: {num_outliers} ({percent_outliers:.2f}%)\n")
print(summary_df.sort_values("Outlier Count", ascending=False))
```

    
    --- Outlier Summary ---
    Total rows: 10100 | Outlier rows: 222 (2.20%)
    
                                       Q1       Q3     IQR  Lower Limit  \
    DrivingCommuterDistance         15.00    71.00    56.0         69.0   
    EmployeeNumber                2525.75  7575.25  5049.5       5048.5   
    Age                             37.00    53.00    16.0         13.0   
    Tenure                           5.00    13.00     8.0          7.0   
    HoursWeekly                     40.00    40.00     0.0         40.0   
    NumCompaniesPreviouslyWorked     2.00     6.00     4.0          4.0   
    AnnualProfessionalDevHrs        11.00    19.00     8.0          1.0   
    
                                  Upper Limit  Outlier Count  
    DrivingCommuterDistance             155.0            222  
    EmployeeNumber                    15149.5              0  
    Age                                  77.0              0  
    Tenure                               25.0              0  
    HoursWeekly                          40.0              0  
    NumCompaniesPreviouslyWorked         12.0              0  
    AnnualProfessionalDevHrs             31.0              0  



```python
print(df3.dtypes)
```

    EmployeeNumber                   int64
    Age                              int64
    Tenure                           int64
    Turnover                        object
    HourlyRate                      object
    HoursWeekly                      int64
    CompensationType                object
    AnnualSalary                    object
    DrivingCommuterDistance          int64
    Gender                          object
    MaritalStatus                   object
    NumCompaniesPreviouslyWorked     int64
    AnnualProfessionalDevHrs         int64
    TextMessageOptIn                object
    JobRole                         object
    PayMethod                       object
    dtype: object



```python
import seaborn as sns
import matplotlib.pyplot as plt
commuter = df3

column_name = df3['DrivingCommuterDistance']
df_commuter=pd.DataFrame(commuter,columns=column_name)

sns.boxplot(data=df3, x= column_name)
plt.show()
```


    
![png](D599_Task_1_files/D599_Task_1_30_0.png)
    



```python
import numpy as np
import matplotlib.pyplot as plt

outlier_indices = np.where((df3['DrivingCommuterDistance'] >= 155) & (df3['DrivingCommuterDistance'] <= 69))

no_outliers = df3.drop(outlier_indices[0])

fig, ax_no_outliers = plt.subplots(figsize=(6, 4))
ax_no_outliers.scatter(no_outliers['DrivingCommuterDistance'], no_outliers['DrivingCommuterDistance'])
ax_no_outliers.set_xlabel('(Lower_Distance)')
ax_no_outliers.set_ylabel('(Higher_Distance) )')
plt.show()
```


    
![png](D599_Task_1_files/D599_Task_1_31_0.png)
    


##### B2 Quality Issue Findings B.1.5 Outliers

###### Q1 - First Quartile: 25% of employees are < 37 years, earn < $63,440, & commute < 15 miles.

###### Q3 - Third Quartile: 75% of employees are < 53 years, earn < $153,717, & commute < 71 miles.

###### IQR - Interquartile Range: The central salary range spans $90,277.20

###### Lower Limit: Salaries below $71,975.80 are potential outliers

###### Upper Limit: Salaries above $289,133.00 are potential outliers


## Save new cleaned csv file


```python
df3.to_csv('Employee_Turnover_Cleaned10.csv', index=False)
import os
print(os.getcwd())
```

    /Users/meredithsmith/PycharmProjects/PythonProject/PythonProject/PythonProject44



```python
print(df3.head)

```

    <bound method NDFrame.head of        EmployeeNumber  Age  Tenure Turnover HourlyRate  HoursWeekly  \
    0                   1   28       6      Yes     $24.37           40   
    1                   2   33       2      Yes     $24.37           40   
    2                   3   22       1       No     $22.52           40   
    3                   4   23       1       No     $22.52           40   
    4                   5   40       6       No     $88.77           40   
    ...               ...  ...     ...      ...        ...          ...   
    10095           10096   50      15      Yes     $61.78           40   
    10096           10097   33       9      Yes     $23.28           40   
    10097           10098   31       9      Yes     $28.25           40   
    10098           10099   50      12       No     $32.22           40   
    10099           10100   59      14       No     $44.59           40   
    
          CompensationType AnnualSalary  DrivingCommuterDistance  \
    0               Salary   $50,689.60                       89   
    1               Salary   $50,689.60                       89   
    2               Salary   $46,841.60                       35   
    3               Salary   $46,841.60                       35   
    4               Salary  $284,641.60                       12   
    ...                ...          ...                      ...   
    10095           Salary  $128,502.40                        6   
    10096           Salary   $48,422.40                       10   
    10097           Salary   $37,960.00                       68   
    10098           Salary   $67,017.60                       13   
    10099           Salary   $92,747.20                       94   
    
                         Gender MaritalStatus  NumCompaniesPreviouslyWorked  \
    0                    Female       Married                             3   
    1                    Female       Married                             6   
    2                    Female        Single                             1   
    3                    Female        Single                             3   
    4      Prefer Not To Answer        Single                             7   
    ...                     ...           ...                           ...   
    10095                  Male      Divorced                             1   
    10096                  Male        Single                             1   
    10097                  Male       Married                             2   
    10098                Female       Married                             5   
    10099                  Male       Married                             4   
    
           AnnualProfessionalDevHrs TextMessageOptIn                 JobRole  \
    0                             7              Yes                Research   
    1                             7              Yes                Research   
    2                             8              Yes  Information_Technology   
    3                            15              Yes  Information_Technology   
    4                            15              Yes                   Sales   
    ...                         ...              ...                     ...   
    10095                         8              Yes              Laboratory   
    10096                        20              Yes               Marketing   
    10097                        21               NS              Laboratory   
    10098                        20              Yes                Research   
    10099                        10               NS                Research   
    
                PayMethod  
    0        Mailed_Check  
    1        Mailed_Check  
    2        Mailed_Check  
    3        Mailed_Check  
    4        Mailed_Check  
    ...               ...  
    10095    Mailed_Check  
    10096  Direct_Deposit  
    10097  Direct_Deposit  
    10098  Direct_Deposit  
    10099  Direct_Deposit  
    
    [10100 rows x 16 columns]>

ding data_cleaning_and_profiling.md…]()
