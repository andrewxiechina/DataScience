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


