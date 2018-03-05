# Python Read

```python
file = open('moby_dick.txt', mode='r')
print(file.read())
file.close()
```

```python
with open('moby_dick.txt') as file:
    print(file.readline())
```

# Numpy
```python
import numpy as np
file = 'digits.csv'
data = np.loadtxt(file, delimiter='\t', dtype=float, skiprows=1, usecols=[0, 2], comment='#')
```

# Pandas
```python
# Read the first 5 rows of the file into a DataFrame: data
data = pd.read_csv(file, nrows=5, header=None, na_values=['Nothing'])
```

# Pickle
```python
with open('data.pkl', 'rb') as file:
  d = pickle.load(file)
```

```python
with open('data.pkl', 'wb') as file:
  pickle.dump(d, file)
```

# Excel
```python
xl = pd.ExcelFile(file)
# Load a sheet into a DataFrame by name: df1
df1 = xl.parse('2004')
# Parse the first sheet and rename the columns: df1
df1 = xl.parse(0, skiprows=[0], names=['Country', 'AAM due to War (2002)'])
# Parse the first column of the second sheet and rename the column: df2
df2 = xl.parse(1, parse_cols=[0], skiprows=[0], names=['Country'])
```

# SAS
```python
# Import sas7bdat package
from sas7bdat import SAS7BDAT

# Save file to a DataFrame: df_sas
with SAS7BDAT('sales.sas7bdat') as file:
    df_sas = file.to_data_frame()
```

# STATA
```python
# Import pandas
import pandas as pd

# Load Stata file into a pandas DataFrame: df
df = pd.read_stata('disarea.dta')

# Print the head of the DataFrame df
print(df.head())

# Plot histogram of one column of the DataFrame
df = pd.read_stata('disarea.dta')
```

# HDF5
Create
```python
import numpy as np
import h5py

d1 = np.random.random(size = (1000,20))
d2 = np.random.random(size = (1000,200))

hf = h5py.File('data.h5', 'w')

hf.create_dataset('dataset_1', data=d1)
hf.create_dataset('dataset_2', data=d2)

hf.close()
```

Reading
```python
hf = h5py.File('data.h5', 'r')
n1 = hf.get('dataset_1')
n1 = np.array(n1)
hf.close()
```

Groups
```python
d1 = np.random.random(size = (100,33))
d2 = np.random.random(size = (100,333))
d3 = np.random.random(size = (100,3333))

hf = h5py.File('data.h5', 'w')

g1 = hf.create_group('group1')
g1.create_dataset('data1',data=d1)
g1.create_dataset('data2',data=d1)

g2 = hf.create_group('group2/subfolder')
g2.create_dataset('data3',data=d3)

hf.close()

```

Set compression level, defaults at 4:
```python
hf.create_dataset('dataset_1', data=d1, compression="gzip", compression_opts=9)

```

# MATLAB
```python
import scipy.io
mat = scipy.io.loadmat('albeck_gene_expression.mat')
data = mat['CYratioCyt'][25, 5:]
```
