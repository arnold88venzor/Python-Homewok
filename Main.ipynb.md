```python
import pandas as pd
from pathlib import Path
%matplotlib inline
```


```python
csv_path = Path("Instructions/PyBank/Resources/budget_data.csv")
G14classified = pd.read_csv(csv_path)
G14classified
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
      <th>Date</th>
      <th>Profit/Losses</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Jan-2010</td>
      <td>867884</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Feb-2010</td>
      <td>984655</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Mar-2010</td>
      <td>322013</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Apr-2010</td>
      <td>-69417</td>
    </tr>
    <tr>
      <th>4</th>
      <td>May-2010</td>
      <td>310503</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>81</th>
      <td>Oct-2016</td>
      <td>102685</td>
    </tr>
    <tr>
      <th>82</th>
      <td>Nov-2016</td>
      <td>795914</td>
    </tr>
    <tr>
      <th>83</th>
      <td>Dec-2016</td>
      <td>60988</td>
    </tr>
    <tr>
      <th>84</th>
      <td>Jan-2017</td>
      <td>138230</td>
    </tr>
    <tr>
      <th>85</th>
      <td>Feb-2017</td>
      <td>671099</td>
    </tr>
  </tbody>
</table>
<p>86 rows × 2 columns</p>
</div>




```python
#Total Months
G14classified_total=G14classified.count()
G14classified_total[0]
```




    86




```python
G14classified.set_index(G14classified["Date"],inplace=True)
G14classified.head()
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
      <th>Date</th>
      <th>Profit/Losses</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Jan-2010</th>
      <td>Jan-2010</td>
      <td>867884</td>
    </tr>
    <tr>
      <th>Feb-2010</th>
      <td>Feb-2010</td>
      <td>984655</td>
    </tr>
    <tr>
      <th>Mar-2010</th>
      <td>Mar-2010</td>
      <td>322013</td>
    </tr>
    <tr>
      <th>Apr-2010</th>
      <td>Apr-2010</td>
      <td>-69417</td>
    </tr>
    <tr>
      <th>May-2010</th>
      <td>May-2010</td>
      <td>310503</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Net total amount of Profit/Losses.

G14classified.drop(columns=["Date"],inplace=True)
netamount=G14classified.sum(axis=None,numeric_only=None,skipna=None,min_count=0,level=None)
netamount[0]
```




    38382578



changes=G14classified.diff()
changes.head()


```python
#Average of the changes in Profit/Losses over the entire period.
avg_changes=changes.mean()
avg_changes[0]
```




    -2315.1176470588234




```python
#greatest increase in profits
greatest_increase=changes.max()
greatest_increase[0]

```




    1926159.0




```python
#greatest decrease in profits
greatest_decrease=changes.min()
greatest_decrease[0]
```




    -2196167.0




```python
G14classified_total=G14classified.count()
G14classified_total[0]
```




    86




```python
print(f'Financial Analysis')
print(f'---------------------')
print(f'Total Profit/Losses {netamount[0]}')
print(f'Average Change {avg_changes[0]}')
print(f'Greatest Increase in Profits {greatest_increase[0]}')
print(f'Greatest Decrease in Profits {greatest_decrease[0]}')
```

    Financial Analysis
    ---------------------
    Total Profit/Losses 38382578
    Average Change -2315.1176470588234
    Greatest Increase in Profits 1926159.0
    Greatest Decrease in Profits -2196167.0



```python

```
