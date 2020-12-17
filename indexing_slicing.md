## Indexing and Slicing Lists and Dataframes

### Indexing and slicing lists

Indexing a list is very useful when you want to isolate one value. This is especially helpful in long lists! I will be using a short list as an example, but the same code and principles can be applied to any list.


```python
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
```


```python
#creating a simple list

list = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p']
```

Any value in the  list can be indexed based on its position. But, the first value in the list is always 0!


```python
#to obtain the first value in the list

print(list[0])

#to obtain the fourth value in the list

print(list[3])

#to obtain the tenth value in the list

print(list[9])

```

    a
    d
    j


A subset of list elements can be created by slicing the original list. To slice, use this code: list_name[start : stop] where start is the index of the first element you want to include in the subset and stop is the element **after** the last item you want to include in the subset. *The element in the stop position will not be included in the subset list!*


```python
#slicing the first four values 

print(list[0:4])
```

    ['a', 'b', 'c', 'd']


By omitting either the start or stop element, I can slice all elements before or after a specific element. 


```python
#omitting the start element subsets all elements up to the stop element specified

print(list[:6])

#omitting the stop element subsets all elements after the start element specified

print(list[6:])
```

    ['a', 'b', 'c', 'd', 'e', 'f']
    ['g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p']


By passing a third argument through the list, I can print intervals. For example, I can print every second element in a list.


```python
#printing every second element in the list

list[::2]

# printing every second element starting at c

list[2::2]
```




    ['c', 'e', 'g', 'i', 'k', 'm', 'o']



### Indexing a DataFrame 


```python
#creating a random dataframe 

data = np.random.randint(5,30,size= (10, 5))
df = pd.DataFrame(data, columns=['A', 'B', 'C', 'D', 'E'], index = ['one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine', 'ten'])
df
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>26</td>
      <td>19</td>
      <td>14</td>
      <td>18</td>
      <td>16</td>
    </tr>
    <tr>
      <th>two</th>
      <td>24</td>
      <td>27</td>
      <td>15</td>
      <td>8</td>
      <td>11</td>
    </tr>
    <tr>
      <th>three</th>
      <td>29</td>
      <td>27</td>
      <td>13</td>
      <td>8</td>
      <td>27</td>
    </tr>
    <tr>
      <th>four</th>
      <td>9</td>
      <td>16</td>
      <td>21</td>
      <td>20</td>
      <td>12</td>
    </tr>
    <tr>
      <th>five</th>
      <td>18</td>
      <td>5</td>
      <td>10</td>
      <td>29</td>
      <td>7</td>
    </tr>
    <tr>
      <th>six</th>
      <td>14</td>
      <td>7</td>
      <td>28</td>
      <td>19</td>
      <td>9</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>15</td>
      <td>28</td>
      <td>8</td>
      <td>26</td>
      <td>7</td>
    </tr>
    <tr>
      <th>eight</th>
      <td>9</td>
      <td>29</td>
      <td>26</td>
      <td>20</td>
      <td>26</td>
    </tr>
    <tr>
      <th>nine</th>
      <td>14</td>
      <td>10</td>
      <td>29</td>
      <td>19</td>
      <td>21</td>
    </tr>
    <tr>
      <th>ten</th>
      <td>28</td>
      <td>21</td>
      <td>14</td>
      <td>21</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



.loc[] is used to access specific rows or columns or elements in the dataframe.


```python
#selecting only row two

two = df.loc[['two']]
two
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>two</th>
      <td>24</td>
      <td>27</td>
      <td>15</td>
      <td>8</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>



.loc can also be used to select a single element from a certain row and column

#selecting the value from row three, column c

df.loc['three', 'C']

Similar to lists, dataframe rows can be sliced to obtain elements from multiple rows and only one column.


```python
#selecting values from row two to seven and only for column C

column_c = df.loc['two':'seven', 'C']
column_c
```




    two      15
    three    13
    four     21
    five     10
    six      28
    seven     8
    Name: C, dtype: int64



The Dataframe can also be altered by selecting only certain values from one column.


```python
#only rows with values in column A greater than 7 are displayed

df_changed = df.loc[df['A'] > 7]
df_changed
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>26</td>
      <td>19</td>
      <td>14</td>
      <td>18</td>
      <td>16</td>
    </tr>
    <tr>
      <th>two</th>
      <td>24</td>
      <td>27</td>
      <td>15</td>
      <td>8</td>
      <td>11</td>
    </tr>
    <tr>
      <th>three</th>
      <td>29</td>
      <td>27</td>
      <td>13</td>
      <td>8</td>
      <td>27</td>
    </tr>
    <tr>
      <th>four</th>
      <td>9</td>
      <td>16</td>
      <td>21</td>
      <td>20</td>
      <td>12</td>
    </tr>
    <tr>
      <th>five</th>
      <td>18</td>
      <td>5</td>
      <td>10</td>
      <td>29</td>
      <td>7</td>
    </tr>
    <tr>
      <th>six</th>
      <td>14</td>
      <td>7</td>
      <td>28</td>
      <td>19</td>
      <td>9</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>15</td>
      <td>28</td>
      <td>8</td>
      <td>26</td>
      <td>7</td>
    </tr>
    <tr>
      <th>eight</th>
      <td>9</td>
      <td>29</td>
      <td>26</td>
      <td>20</td>
      <td>26</td>
    </tr>
    <tr>
      <th>nine</th>
      <td>14</td>
      <td>10</td>
      <td>29</td>
      <td>19</td>
      <td>21</td>
    </tr>
    <tr>
      <th>ten</th>
      <td>28</td>
      <td>21</td>
      <td>14</td>
      <td>21</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



Similarly, I can alter values within a column so that they all meet a certain condition.


```python
#changing column A so all values are lower than 18 are equal to 18

df.loc[df['A'] < 18] = 18
df
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>one</th>
      <td>26</td>
      <td>19</td>
      <td>14</td>
      <td>18</td>
      <td>16</td>
    </tr>
    <tr>
      <th>two</th>
      <td>24</td>
      <td>27</td>
      <td>15</td>
      <td>8</td>
      <td>11</td>
    </tr>
    <tr>
      <th>three</th>
      <td>29</td>
      <td>27</td>
      <td>13</td>
      <td>8</td>
      <td>27</td>
    </tr>
    <tr>
      <th>four</th>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
    </tr>
    <tr>
      <th>five</th>
      <td>18</td>
      <td>5</td>
      <td>10</td>
      <td>29</td>
      <td>7</td>
    </tr>
    <tr>
      <th>six</th>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
    </tr>
    <tr>
      <th>seven</th>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
    </tr>
    <tr>
      <th>eight</th>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
    </tr>
    <tr>
      <th>nine</th>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
    </tr>
    <tr>
      <th>ten</th>
      <td>28</td>
      <td>21</td>
      <td>14</td>
      <td>21</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>




```python

```