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

# Time
```python
df3 = pd.read_csv(filename, index_col='Date', parse_dates=True)
```

Casting
```python
# Prepare a format string: time_format
time_format='%Y-%m-%d %H:%M'

# Convert date_list into a datetime object: my_datetimes
my_datetimes = pd.to_datetime(date_list, format=time_format)  
```

Selection
```python
# Extract data from '2010-12-15' to '2010-12-31': ts3
ts3 = ts0.loc['2010-12-15':'2010-12-31']
```

Reindex
```python
ts3 = ts2.reindex(ts1.index)
# ts4 = ts2.reindex(ts1.index, method='ffill')
```

Resample
```python
# Downsample to 6 hour data and aggregate by mean: df1
df1 = df['Temperature'].resample('6h').mean()

# Downsample to daily data and count the number of data points: df2
df2 = df['Temperature'].resample('D').count()
```


Rolling
```python
# Apply a rolling mean with a 24 hour window: smoothed
smoothed = unsmoothed.rolling(window=24).mean()
```

Interpolate (Guess)
```python
ts2_interp = ts2.reindex(ts1.index).interpolate(how='linear')
```

# Time Zone
```python
# Combine two columns of data to create a datetime series: times_tz_none 
times_tz_none = pd.to_datetime( la['Date (MM/DD/YYYY)'] + ' ' + la['Wheels-off Time'] )

# Localize the time to US/Central: times_tz_central
times_tz_central = times_tz_none.dt.tz_localize('US/Central')
```

# Set Index
```python
# Convert the 'Date' column into a collection of datetime objects: df.Date
df.Date = pd.to_datetime(df.Date)

# Set the index to be the converted 'Date' column
df.set_index('Date', inplace=True)
```

# Plot
```python
df.Temperature['2010-Jun':'2010-Aug'].plot()
```
