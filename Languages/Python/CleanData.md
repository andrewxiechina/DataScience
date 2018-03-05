# Descriptive Analysis
```python
df.head()
df.columns
df.info()
print(df['Borough'].value_counts(dropna=False))
```

# Pandas Visualization
```python
df.plot(kind='scatter', x='initial_cost', y='total_est_fee', rot=70)
```

# Pandas Melt / Pivoting
```python
# Melt airquality: airquality_melt
airquality_melt = pd.melt(airquality, id_vars=['Month', 'Day'], var_name='measurement', value_name='reading')

# Pivot airquality_melt: airquality_pivot
airquality_pivot = airquality_melt.pivot_table(index=['Month', 'Day'], columns='measurement', values='reading')
airquality_pivot = airquality_pivot.reset_index()

# With duplication
airquality_pivot = airquality_dup.pivot_table(index=['Month', 'Day'], columns='measurement', values='reading', aggfunc=np.mean)
airquality_pivot = airquality_pivot.reset_index()
```

# Combine
```python
row_concat = pd.concat([uber1, uber2, uber3])

# Concatenate ebola_melt and status_country column-wise: ebola_tidy
ebola_tidy = pd.concat([ebola_melt, status_country], axis=1)
```

# Find all csv files
```python
# Import necessary modules
import glob
import pandas as pd

# Write the pattern: pattern
pattern = '*.csv'

# Save all file matches: csv_files
csv_files = glob.glob(pattern)
```

# Merge
```python
o2o = pd.merge(left=site, right=visited, left_on='name', right_on='site')
```

# Categorical Data
```python
# Convert the sex column to type 'category'
tips.sex = tips.sex.astype('category')

# Convert the smoker column to type 'category'
tips.smoker = tips.smoker.astype('category')

# Print the info of tips
print(tips.info())
```

# Object to int/float
```python
tips['total_bill'] = pd.to_numeric(tips['total_bill'], errors='coerce')
```

# Regex
```python
# Import the regular expression module
import re

# Compile the pattern: prog
prog = re.compile('\d{3}-\d{3}-\d{4}')

# See if the pattern matches
result = prog.match('123-456-7890')

# Import the regular expression module
import re

# Find the numeric values: matches
matches = re.findall('\d+', 'the recipe calls for 10 strawberries and 1 banana')
```

# Apply
```python
# Define recode_sex()
def recode_sex(sex_value):

    # Return 1 if sex_value is 'Male'
    if sex_value == 'Male':
        return 1
    
    # Return 0 if sex_value is 'Female'
    elif sex_value == 'Female':
        return 0
        
    # Return np.nan    
    else:
        return np.nan

# Apply the function to the sex column
tips['sex_recode'] = tips.sex.apply(recode_sex)
```

```python
tips['total_dollar_replace'] = tips.total_dollar.apply(lambda x: x.replace('$', ''))
```

# Drop Duplication
```python
tracks_no_duplicates = tracks.drop_duplicates()
```

# Fill Missing Data
```python
# Calculate the mean of the Ozone column: oz_mean
oz_mean = airquality.Ozone.mean()

# Replace all the missing values in the Ozone column with the mean
airquality['Ozone'] = airquality.Ozone.fillna(oz_mean)
```

# Check Missing Data
```python
# Check all columns and combine to one boolean value
 pd.notnull(ebola).all().all()
 ```
 
# Data Type
```python
 assert gapminder.country.dtypes == np.object
```
