
# Ex2 - Getting and Knowing your Data

This time we are going to pull data directly from the internet.
Special thanks to: https://github.com/justmarkham for sharing the dataset and materials.

### Step 1. Import the necessary libraries


```
import pandas as pd
import numpy as np
```

### Step 2. Import the dataset from this [address](https://raw.githubusercontent.com/justmarkham/DAT8/master/data/chipotle.tsv). 

### Step 3. Assign it to a variable called chipo.


```
url = 'https://raw.githubusercontent.com/justmarkham/DAT8/master/data/chipotle.tsv'
    
chipo = pd.read_csv(url, sep = '\t')
```

### Step 4. See the first 10 entries


```
chipo.head(10)
# chipo['choice_description'][4]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>order_id</th>
      <th>quantity</th>
      <th>item_name</th>
      <th>choice_description</th>
      <th>item_price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1</td>
      <td>Chips and Fresh Tomato Salsa</td>
      <td>NaN</td>
      <td>$2.39</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>Izze</td>
      <td>[Clementine]</td>
      <td>$3.39</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>1</td>
      <td>Nantucket Nectar</td>
      <td>[Apple]</td>
      <td>$3.39</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1</td>
      <td>Chips and Tomatillo-Green Chili Salsa</td>
      <td>NaN</td>
      <td>$2.39</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>2</td>
      <td>Chicken Bowl</td>
      <td>[Tomatillo-Red Chili Salsa (Hot), [Black Beans...</td>
      <td>$16.98</td>
    </tr>
    <tr>
      <th>5</th>
      <td>3</td>
      <td>1</td>
      <td>Chicken Bowl</td>
      <td>[Fresh Tomato Salsa (Mild), [Rice, Cheese, Sou...</td>
      <td>$10.98</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3</td>
      <td>1</td>
      <td>Side of Chips</td>
      <td>NaN</td>
      <td>$1.69</td>
    </tr>
    <tr>
      <th>7</th>
      <td>4</td>
      <td>1</td>
      <td>Steak Burrito</td>
      <td>[Tomatillo Red Chili Salsa, [Fajita Vegetables...</td>
      <td>$11.75</td>
    </tr>
    <tr>
      <th>8</th>
      <td>4</td>
      <td>1</td>
      <td>Steak Soft Tacos</td>
      <td>[Tomatillo Green Chili Salsa, [Pinto Beans, Ch...</td>
      <td>$9.25</td>
    </tr>
    <tr>
      <th>9</th>
      <td>5</td>
      <td>1</td>
      <td>Steak Burrito</td>
      <td>[Fresh Tomato Salsa, [Rice, Black Beans, Pinto...</td>
      <td>$9.25</td>
    </tr>
  </tbody>
</table>
</div>



### Step 5. What is the number of observations in the dataset?


```
chipo.info()#

# OR

chipo.shape[0]
# 4622 observations
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 4622 entries, 0 to 4621
    Data columns (total 5 columns):
    order_id              4622 non-null int64
    quantity              4622 non-null int64
    item_name             4622 non-null object
    choice_description    3376 non-null object
    item_price            4622 non-null object
    dtypes: int64(2), object(3)
    memory usage: 180.6+ KB





    4622



### Step 6. What is the number of columns in the dataset?


```
chipo.shape[1]
```




    5



### Step 7. Print the name of all the columns.


```
chipo.columns
```




    Index([u'order_id', u'quantity', u'item_name', u'choice_description',
           u'item_price'],
          dtype='object')



### Step 8. How is the dataset indexed?


```
chipo.index
```




    RangeIndex(start=0, stop=4622, step=1)



### Step 9. Which was the most ordered item? 


```
c = chipo.groupby('item_name')
c = c.sum()
c = c.sort_values(['quantity'], ascending=False)
c.head(1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>order_id</th>
      <th>quantity</th>
    </tr>
    <tr>
      <th>item_name</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Chicken Bowl</th>
      <td>713926</td>
      <td>761</td>
    </tr>
  </tbody>
</table>
</div>



### Step 10. How many items were ordered?


```
c = chipo.groupby('item_name')
c = c.sum()
c = c.sort_values(['quantity'], ascending=False)
c.head(1)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>order_id</th>
      <th>quantity</th>
    </tr>
    <tr>
      <th>item_name</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Chicken Bowl</th>
      <td>713926</td>
      <td>761</td>
    </tr>
  </tbody>
</table>
</div>



### Step 11. What was the most ordered item in the choice_description column?


```
c = chipo.groupby('choice_description').sum()
c = c.sort_values(['quantity'], ascending=False)
c.head(1)
# Diet Coke 159
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>order_id</th>
      <th>quantity</th>
    </tr>
    <tr>
      <th>choice_description</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>[Diet Coke]</th>
      <td>123455</td>
      <td>159</td>
    </tr>
  </tbody>
</table>
</div>



### Step 12. How many items were orderd in total?


```
total_items_orders = chipo.quantity.sum()
total_items_orders
```




    4972



### Step 13. Turn the item price into a float


```
dollarizer = lambda x: float(x[1:-1])
chipo.item_price = chipo.item_price.apply(dollarizer)
```

### Step 14. How much was the revenue for the period in the dataset?


```
revenue = (chipo['quantity']* chipo['item_price']).sum()

print('Revenue was: $' + str(np.round(revenue,2)))
```

    Revenue was: $39237.02


### Step 15. How many orders were made in the period?


```
chipo.order_id.value_counts().count()
```




    1834



### Step 16. What is the average amount per order?


```
order_grouped = chipo.groupby(by=['order_id']).sum()
order_grouped.mean()['item_price']

# Or 

#chipo.groupby(by=['order_id']).sum().mean()['item_price']
```




    18.811428571428689



### Step 17. How many different items are sold?


```
chipo.item_name.value_counts().count()
```




    50


