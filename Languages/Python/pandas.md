# Log
```python
# Create new array of base 10 logarithm values: np_vals_log10
np_vals_log10 = np.log10(np_vals)
```

# Change Column Name
```python
# Assign the list of labels to the columns attribute: df.columns
df.columns = list_labels
```

# Build Data Frame
```python
# Construct a dictionary: data
data = {'state':state, 'city':cities}

# Construct a DataFrame from dictionary data: df
df = pd.DataFrame(data)
```

# Plot
```python
# Generate a scatter plot
df.plot(kind='scatter', x='hp', y='mpg', s=sizes)

# Add the title
plt.title('Fuel efficiency vs Horse-power')

# Add the x-axis label
plt.xlabel('Horse-power')

# Add the y-axis label
plt.ylabel('Fuel efficiency (mpg)')

# Display the plot
plt.show()


# Plot the PDF
df.fraction.plot(ax=axes[0], kind='hist', normed=True, bins=30, range=(0,.3))
plt.show()

# Plot the CDF
df.fraction.plot(ax=axes[1], kind='hist', normed=True, cumulative=True, bins=30, range=(0,.3))
```

# Quantile
```python
df.quantile([0.05,0.95])
```

# Select by Condition 
```python
titanic.loc[titanic['pclass'] == 1]
```

# Fill
```python
bronze.add(silver, fill_value=0)
```

# Concatenate
```python
# No need to reindex
pd.concat([df1, df2], ignore_index=True)

# Horizontal Join
pd.concat([df1, df2], axis=1)
```

# Merge
```python
# Merge revenue with managers on 'city': merge_by_city
merge_by_city = pd.merge(revenue, managers, on='city')
```

```python
# Merge revenue and sales: revenue_and_sales
revenue_and_sales = pd.merge(revenue, sales, on=['city','state'], how='right')
```

# Set Index
```python
merged.set_index('Edition').sort_index()
```

# Rolling Average
```python
sn.rolling(2).max()
s.expanding().mean()
s.ewm(span=20).mean()
```

# Slicing
```python
# Slice the row labels 'Potter' to 'Perry' in reverse order: p_counties_rev
p_counties_rev = election.loc['Potter':'Perry':-1]

# Slice the columns from the starting column to 'Obama': left_columns
left_columns = election.loc[:, :'Obama']
```

```python
# Create the boolean array: high_turnout
high_turnout = election['turnout'] > 70

# Filter the election DataFrame with the high_turnout array: high_turnout_df
high_turnout_df = election.loc[high_turnout]
```

# Drop Null
```python
# Drop rows in df with how='any' and print the shape
print(df.dropna(how='any').shape)

# Drop rows in df with how='all' and print the shape
print(df.dropna(how='all').shape)
```

# Apply
```python
# Write a function to convert degrees Fahrenheit to degrees Celsius: to_celsius
def to_celsius(F):
    return 5/9*(F - 32)

# Apply the function over 'Mean TemperatureF' and 'Mean Dew PointF': df_celsius
df_celsius = weather[['Mean TemperatureF', 'Mean Dew PointF']].apply(to_celsius)
```

# Map
```python
# Create the dictionary: red_vs_blue
red_vs_blue = {'Obama':'blue', 'Romney':'red'}

# Use the dictionary to map the 'winner' column to the new column: election['color']
election['color'] = election['winner'].map(red_vs_blue)
```

# Melt/Pivot
```python
# Add in the margins: signups_and_visitors_total 
signups_and_visitors_total = users.pivot_table(index='weekday', aggfunc=sum, margins=True)
```
