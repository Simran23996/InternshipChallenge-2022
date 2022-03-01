```python
#import library
import pandas as pd
from datetime import timedelta
import seaborn as sns
pip install xlrd==1.2.0
```


```python
# Import the dataset
df = pd.read_excel('2022 Winter Data Science Intern Challenge Data Set.xlsx')
df.head()
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
      <th>order_id</th>
      <th>shop_id</th>
      <th>user_id</th>
      <th>order_amount</th>
      <th>total_items</th>
      <th>payment_method</th>
      <th>created_at</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>53</td>
      <td>746</td>
      <td>224</td>
      <td>2</td>
      <td>cash</td>
      <td>2017-03-13 12:36:56.190</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>92</td>
      <td>925</td>
      <td>90</td>
      <td>1</td>
      <td>cash</td>
      <td>2017-03-03 17:38:51.999</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>44</td>
      <td>861</td>
      <td>144</td>
      <td>1</td>
      <td>cash</td>
      <td>2017-03-14 04:23:55.595</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>18</td>
      <td>935</td>
      <td>156</td>
      <td>1</td>
      <td>credit_card</td>
      <td>2017-03-26 12:43:36.649</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>18</td>
      <td>883</td>
      <td>156</td>
      <td>1</td>
      <td>credit_card</td>
      <td>2017-03-01 04:35:10.773</td>
    </tr>
  </tbody>
</table>
</div>



## Calculating Summary Statistics


```python
#Calculating Average Order Value
df['order_amount'].mean()
```




    3145.128




```python
df.describe()
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
      <th>order_id</th>
      <th>shop_id</th>
      <th>user_id</th>
      <th>order_amount</th>
      <th>total_items</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>5000.000000</td>
      <td>5000.000000</td>
      <td>5000.000000</td>
      <td>5000.000000</td>
      <td>5000.00000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2500.500000</td>
      <td>50.078800</td>
      <td>849.092400</td>
      <td>3145.128000</td>
      <td>8.78720</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1443.520003</td>
      <td>29.006118</td>
      <td>87.798982</td>
      <td>41282.539349</td>
      <td>116.32032</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>607.000000</td>
      <td>90.000000</td>
      <td>1.00000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1250.750000</td>
      <td>24.000000</td>
      <td>775.000000</td>
      <td>163.000000</td>
      <td>1.00000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2500.500000</td>
      <td>50.000000</td>
      <td>849.000000</td>
      <td>284.000000</td>
      <td>2.00000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>3750.250000</td>
      <td>75.000000</td>
      <td>925.000000</td>
      <td>390.000000</td>
      <td>3.00000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>5000.000000</td>
      <td>100.000000</td>
      <td>999.000000</td>
      <td>704000.000000</td>
      <td>2000.00000</td>
    </tr>
  </tbody>
</table>
</div>



## Checking for Missing and Duplicate Values


```python
#Check for missing values 
df[df.order_amount<=0]
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
      <th>order_id</th>
      <th>shop_id</th>
      <th>user_id</th>
      <th>order_amount</th>
      <th>total_items</th>
      <th>payment_method</th>
      <th>created_at</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>




```python
#Check for duplicate values 
df[df.duplicated('order_id')]
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
      <th>order_id</th>
      <th>shop_id</th>
      <th>user_id</th>
      <th>order_amount</th>
      <th>total_items</th>
      <th>payment_method</th>
      <th>created_at</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>




```python
#Check for duplicate values 
df.order_id.value_counts()
```




    2047    1
    2608    1
    4647    1
    2600    1
    553     1
           ..
    3263    1
    1218    1
    3267    1
    1222    1
    2049    1
    Name: order_id, Length: 5000, dtype: int64



### Hence no missing or duplicate values in the dataset. 


```python
start_date_for_AOV = df["created_at"].min()+ timedelta(days=29)
```


```python
df = df.set_index('created_at')
df = df.sort_index()
df.head()
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
      <th>order_id</th>
      <th>shop_id</th>
      <th>user_id</th>
      <th>order_amount</th>
      <th>total_items</th>
      <th>payment_method</th>
    </tr>
    <tr>
      <th>created_at</th>
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
      <th>2017-03-01 00:08:09.179</th>
      <td>1863</td>
      <td>39</td>
      <td>738</td>
      <td>536</td>
      <td>4</td>
      <td>cash</td>
    </tr>
    <tr>
      <th>2017-03-01 00:10:19.043</th>
      <td>1742</td>
      <td>39</td>
      <td>910</td>
      <td>268</td>
      <td>2</td>
      <td>cash</td>
    </tr>
    <tr>
      <th>2017-03-01 00:14:12.250</th>
      <td>3229</td>
      <td>97</td>
      <td>912</td>
      <td>324</td>
      <td>2</td>
      <td>cash</td>
    </tr>
    <tr>
      <th>2017-03-01 00:19:31.258</th>
      <td>1268</td>
      <td>80</td>
      <td>798</td>
      <td>290</td>
      <td>2</td>
      <td>credit_card</td>
    </tr>
    <tr>
      <th>2017-03-01 00:22:24.790</th>
      <td>2690</td>
      <td>49</td>
      <td>799</td>
      <td>258</td>
      <td>2</td>
      <td>credit_card</td>
    </tr>
  </tbody>
</table>
</div>




```python
aov_df = df.rolling('30D').order_amount.mean().reset_index()
```


```python
aov_df[aov_df.created_at>start_date_for_AOV]
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
      <th>created_at</th>
      <th>order_amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4833</th>
      <td>2017-03-30 00:22:19.920</td>
      <td>3237.896359</td>
    </tr>
    <tr>
      <th>4834</th>
      <td>2017-03-30 00:36:01.921</td>
      <td>3237.321613</td>
    </tr>
    <tr>
      <th>4835</th>
      <td>2017-03-30 00:42:12.094</td>
      <td>3236.705955</td>
    </tr>
    <tr>
      <th>4836</th>
      <td>2017-03-30 00:54:43.962</td>
      <td>3236.095514</td>
    </tr>
    <tr>
      <th>4837</th>
      <td>2017-03-30 00:57:20.356</td>
      <td>3235.458247</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4995</th>
      <td>2017-03-30 23:12:13.085</td>
      <td>3147.476781</td>
    </tr>
    <tr>
      <th>4996</th>
      <td>2017-03-30 23:16:09.573</td>
      <td>3146.895737</td>
    </tr>
    <tr>
      <th>4997</th>
      <td>2017-03-30 23:26:54.436</td>
      <td>3146.294518</td>
    </tr>
    <tr>
      <th>4998</th>
      <td>2017-03-30 23:41:34.347</td>
      <td>3145.723545</td>
    </tr>
    <tr>
      <th>4999</th>
      <td>2017-03-30 23:55:35.408</td>
      <td>3145.128000</td>
    </tr>
  </tbody>
</table>
<p>167 rows × 2 columns</p>
</div>



## Visualising the Data
Plotting histogram and a boxplot to check for outliers


```python
df.order_amount.hist(bins=50,range=[0, 20000], facecolor='gray', align='mid')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x121c03bb0>




    
![png](output_15_1.png)
    



```python
sns.boxplot(x=df['order_amount'])
```




    <matplotlib.axes._subplots.AxesSubplot at 0x121c922e0>




    
![png](output_16_1.png)
    


## Checking For Outliers 
We check for all the order amounts which have an "Order amount < 2500" and otherwise. 


```python
#Checking for values with order amount less than 2500
df[df['order_amount']<2500].shape, df[df['order_amount']<250].order_amount.mean()
```




    ((4937, 7), 158.48031496062993)




```python
#Checking for values with order amount greater than 2500
df[df['order_amount']>2500].shape, df[df['order_amount']>250].order_amount.mean()
```




    ((63, 7), 5189.894878706199)



Thus we see, 4937 orders with Average Order Value of 302.5 and 63 orders with a high AOV of 225901.5. 


```python
aov_df = df[df['order_amount']<2500].rolling('30D').order_amount.mean().reset_index()
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-45-35ef80c42050> in <module>
    ----> 1 aov_df = df[df['order_amount']<2500].rolling('30D').order_amount.mean().reset_index()
    

    /Library/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages/pandas/core/generic.py in rolling(self, window, min_periods, center, win_type, on, axis, closed)
      10374                 )
      10375 
    > 10376             return Rolling(
      10377                 self,
      10378                 window=window,


    /Library/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages/pandas/core/window/rolling.py in __init__(self, obj, window, min_periods, center, win_type, axis, on, closed, **kwargs)
         92         self.win_freq = None
         93         self.axis = obj._get_axis_number(axis) if axis is not None else None
    ---> 94         self.validate()
         95         self._numba_func_cache: Dict[Optional[str], Callable] = dict()
         96 


    /Library/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages/pandas/core/window/rolling.py in validate(self)
       1860             return
       1861         elif not is_integer(self.window):
    -> 1862             raise ValueError("window must be an integer")
       1863         elif self.window < 0:
       1864             raise ValueError("window must be non-negative")


    ValueError: window must be an integer



```python
aov_df[aov_df.created_at>start_date_for_AOV]
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
      <th>created_at</th>
      <th>order_amount</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4833</th>
      <td>2017-03-30 00:22:19.920</td>
      <td>3237.896359</td>
    </tr>
    <tr>
      <th>4834</th>
      <td>2017-03-30 00:36:01.921</td>
      <td>3237.321613</td>
    </tr>
    <tr>
      <th>4835</th>
      <td>2017-03-30 00:42:12.094</td>
      <td>3236.705955</td>
    </tr>
    <tr>
      <th>4836</th>
      <td>2017-03-30 00:54:43.962</td>
      <td>3236.095514</td>
    </tr>
    <tr>
      <th>4837</th>
      <td>2017-03-30 00:57:20.356</td>
      <td>3235.458247</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>4995</th>
      <td>2017-03-30 23:12:13.085</td>
      <td>3147.476781</td>
    </tr>
    <tr>
      <th>4996</th>
      <td>2017-03-30 23:16:09.573</td>
      <td>3146.895737</td>
    </tr>
    <tr>
      <th>4997</th>
      <td>2017-03-30 23:26:54.436</td>
      <td>3146.294518</td>
    </tr>
    <tr>
      <th>4998</th>
      <td>2017-03-30 23:41:34.347</td>
      <td>3145.723545</td>
    </tr>
    <tr>
      <th>4999</th>
      <td>2017-03-30 23:55:35.408</td>
      <td>3145.128000</td>
    </tr>
  </tbody>
</table>
<p>167 rows × 2 columns</p>
</div>



Here we calculate AOV without the outliers and get the desired results:

## Part b) & c) 

First Approach: We can remove the outliers and then calculate the AOV for the dataset. We can introduce a column called "outlier" and one-hot encode it. Following, we can delete the outliers and check for the AOV by calculating the mean. Alternatively, we can use a metric "Revenue per item" and can be calculated by. 


```python
import numpy as np 
# A outlier is considered as 1 if it exceeds the order amount of 2500, otherwise 0. 
df['outlier'] = np.where(df.order_amount > 2500, 1, 0) 

df.head()
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
      <th>order_id</th>
      <th>shop_id</th>
      <th>user_id</th>
      <th>order_amount</th>
      <th>total_items</th>
      <th>payment_method</th>
      <th>created_at</th>
      <th>outlier</th>
      <th>RPI</th>
      <th>RPI1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>53</td>
      <td>746</td>
      <td>224</td>
      <td>2</td>
      <td>cash</td>
      <td>2017-03-13 12:36:56.190</td>
      <td>0</td>
      <td>112.0</td>
      <td>112.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>92</td>
      <td>925</td>
      <td>90</td>
      <td>1</td>
      <td>cash</td>
      <td>2017-03-03 17:38:51.999</td>
      <td>0</td>
      <td>90.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>44</td>
      <td>861</td>
      <td>144</td>
      <td>1</td>
      <td>cash</td>
      <td>2017-03-14 04:23:55.595</td>
      <td>0</td>
      <td>144.0</td>
      <td>144.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>18</td>
      <td>935</td>
      <td>156</td>
      <td>1</td>
      <td>credit_card</td>
      <td>2017-03-26 12:43:36.649</td>
      <td>0</td>
      <td>156.0</td>
      <td>156.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>18</td>
      <td>883</td>
      <td>156</td>
      <td>1</td>
      <td>credit_card</td>
      <td>2017-03-01 04:35:10.773</td>
      <td>0</td>
      <td>156.0</td>
      <td>156.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Creating a dataframe removing all the outliers
df2 = df.loc[df['outlier'] == 0]
print(df2.shape)

```

    (4937, 10)



```python
#Calculating mean
df2['order_amount'].mean()
```




    302.58051448247926




```python
#Calculating the Summary Statistics 
df2.describe()
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
      <th>order_id</th>
      <th>shop_id</th>
      <th>user_id</th>
      <th>order_amount</th>
      <th>total_items</th>
      <th>outlier</th>
      <th>RPI</th>
      <th>RPI1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>4937.000000</td>
      <td>4937.000000</td>
      <td>4937.000000</td>
      <td>4937.000000</td>
      <td>4937.000000</td>
      <td>4937.0</td>
      <td>4937.000000</td>
      <td>4937.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2499.551347</td>
      <td>49.846465</td>
      <td>849.752279</td>
      <td>302.580514</td>
      <td>1.994734</td>
      <td>0.0</td>
      <td>151.788536</td>
      <td>151.788536</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1444.069407</td>
      <td>29.061131</td>
      <td>86.840313</td>
      <td>160.804912</td>
      <td>0.982821</td>
      <td>0.0</td>
      <td>29.034215</td>
      <td>29.034215</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>700.000000</td>
      <td>90.000000</td>
      <td>1.000000</td>
      <td>0.0</td>
      <td>90.000000</td>
      <td>90.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1248.000000</td>
      <td>24.000000</td>
      <td>775.000000</td>
      <td>163.000000</td>
      <td>1.000000</td>
      <td>0.0</td>
      <td>132.000000</td>
      <td>132.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>2497.000000</td>
      <td>50.000000</td>
      <td>850.000000</td>
      <td>284.000000</td>
      <td>2.000000</td>
      <td>0.0</td>
      <td>153.000000</td>
      <td>153.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>3751.000000</td>
      <td>74.000000</td>
      <td>925.000000</td>
      <td>387.000000</td>
      <td>3.000000</td>
      <td>0.0</td>
      <td>166.000000</td>
      <td>166.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>5000.000000</td>
      <td>100.000000</td>
      <td>999.000000</td>
      <td>1760.000000</td>
      <td>8.000000</td>
      <td>0.0</td>
      <td>352.000000</td>
      <td>352.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Calculating Revenue per Item: 

df['RPI'] = df['order_amount'] / df['total_items']
df.head()

#Calculating mean

df['RPI'].mean()

# we can also calculate RPI by removing outliers or filtering for different price ranges of shoes. 
```




    387.7428



### Thus after removing the outliers, the AOV looks reasonable at around 302.5

Approach 2: Instead of taking the mean, take another descriptive Statistic : Median. Median has little effect on the presence of outliers. 


```python
# calculating the median
df.order_amount.median()
```




    284.0



## QUESTION 2 : USING SQL
Ques 1) How many orders were shipped by Speedy Express in total? 

# Code:

select count(*) from 
(select * from Orders o join shippers s on o.ShipperID = s.ShipperID) 
where ShipperName = 'Speedy Express'
### Answer -> 54
Ques 2) How many orders were shipped by Speedy Express in total?

# Code: 

select LastName from Employees 
where EmployeeID in 
(select EmployeeID from (SELECT EmployeeID, 
count(OrderID) as orders FROM [Orders] group by 
EmployeeID) order by orders DESC limit 1)

### Answer -> Peacock
Ques 3) What product was ordered the most by customers in Germany?

#Code: 
select ProductName from 
(SELECT ProductID,sum(Quantity) as 
product_quantity FROM Orders o Join 
(select CustomerID,Country from Customers) cs 
on o.CustomerID=cs.CustomerID Join 
OrderDetails od on 
o.OrderID = od.OrderID 
where Country = 'Germany' 
group by Quantity order by product_quantity DESC 
limit 1) od 
join 
(select ProductName,ProductID from Products) 
pd_details on 
od.ProductID = pd_details.ProductID

### Answer -> Boston Crab Meat



```python

```
