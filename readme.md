# Python-Pandas
## Book Chapter
* Python資料科學實戰教本_陳會安, Ch8

## Books


----
## TUTSITE
* [Data to Fish](https://datatofish.com/python-tutorials/)
* [[第 17 天] 資料角力](https://ithelp.ithome.com.tw/articles/10186310)

## Select Rows from Pandas DataFrame
* [How to Select Rows from Pandas DataFrame in Python](https://appdividend.com/2020/04/28/python-how-to-select-rows-from-pandas-dataframe/)
* [Pandas - skip rows while reading csv file to a Dataframe using read_csv() in Python – thisPointer](https://thispointer.com/pandas-skip-rows-while-reading-csv-file-to-a-dataframe-using-read_csv-in-python/)
* [pandas read_csv and keep only certain rows (python) - Stack Overflow](https://stackoverflow.com/questions/39339142/pandas-read-csv-and-keep-only-certain-rows-python)
* [Select the necessary rows and columns of data to load into dataframe](https://symbiosisacademy.org/tutorial-index/pandas-read_csv_select-skip-rows-columns/)
```python==
# SPECIFY (ROW) RANGES
rows = range(1, 6)
# SKIP DATA NOT IN THE (ROW) RANGE
data = pd.read_csv('2222.txt',
                   sep=r'\s+',
                   header=None,
                   skiprows=lambda x: x not in rows)
data.transpose().plot()
plt.show()
```

## ISSUES
* [5 ways to apply an IF condition in pandas DataFrame](https://datatofish.com/if-condition-in-pandas-dataframe/)
* [How to Concatenate Column Values in Pandas DataFrame](https://datatofish.com/concatenate-values-python/)
* [Python pandas: how to specify data types when reading an Excel file?](https://stackoverflow.com/questions/32591466/python-pandas-how-to-specify-data-types-when-reading-an-excel-file)

## enumerate

* code
```python=
string1 = 'abcd'

for i, v in enumerate(string1):
    print(f'位置[{i}]: {v}')
```
* output
```python=
位置[0]: a
位置[1]: b
位置[2]: c
位置[3]: d
```

## zip
* code
```python=
index_list = range(len(string1))
for i, v in zip(index_list,string1):
    print(f'位置[{i}]: {v}')
```
* output
```python=
位置[0]: a
位置[1]: b
位置[2]: c
位置[3]: d
```

## dictionary
* * 範例2
```python=
name1 = { 
    'Billy':165,
    'Bob':160,
    'Mary':170,
    'Joe':168
}
print(name1)
```
* 範例3
```python=
name2 = {}
name2['Billy']=165 
name2['Bob']=168
name2['Joe']=168
name2['Mary']=170
name2['徐小訓']=172
name2
```
* 範例10

```python=
keys='abcd'
values=[1,2,3,4]
d = {key: value for key, value in zip(keys,values)}
d
```

* 範例12
```python=
for k,v in name2.items(): 
    print(k,v)
```

* 範例13
```python=
for k in name2.keys():
    print(k,name2[k])
```

* 範例14
```python=
for v in name2.values():
    print(v)
```

* 範例15
```python=
for k in name2:
    print(k,name2[k])
```

* 範例16
```python=
for k in sorted(name2.keys(), reverse=True):
    print(k,name2[k])    
```

## function

* 範例11
```python=
def add(a,b):
    return a+b 
```
```python=
result = add(1,2)
result
```

* 範例13
```python=
def swap(a,b):
    return b,a
swap(3,5)
```

* 範例14
```python=
def func(*arg):
    print('輸入參數的資料型態',type(arg),'其值為：',arg)
    for i in arg:
        print(i)
```

```python=
func(1,2,3)
func('a','b')
```

* 範例16
```python=
def k_func(**kwargs):
    print('輸入參數的資料型態',type(kwargs),'其值為：',kwargs)
    for k,v in kwargs.items():
        print(f'鍵{k}:值{v}')
k_func(a=1,b=2,c=3)
```

* 範例17
```python=
def square(num):
    return num**2
square(15)
```

* 範例18
```python=
(lambda num: num**2)(15)
```


## Series

* 範例1
```python=
import pandas as pd
pd.Series(data=range(1,5),index=list('abcd'))
```


* 範例5
```python=
s = pd.Series(data=range(1,5),index=list('abcd'))
s.values
s.index
```

* 範例7
```python=
s = pd.Series(data=range(1,5),index=list('abcd'))
s
```

* 範例17
```python=
s.rename({'A':'AA'}, inplace=True)
s
```

## Series - Catetory data
* 範例33
```python=
s=pd.Series(['a','a','b','b','b','c','c','d','b'])
s
```
```python=
s.nunique()

s.unique()
```

```python=
s.value_counts()

s.value_counts(normalize=True)

s.value_counts(normalize=True).round(2)

s.value_counts(normalize=True).round(2).sort_index()
```

```python=
%matplotlib inline  
s.value_counts().sort_index().plot(kind='bar')  
```

## DataFrame
```python=
# 以下兩行是畫圖用
%matplotlib inline
import matplotlib.pyplot as plt 
# 載入pandas套件
import pandas as pd
import numpy as np
```

* 範例1
```python=
scores = {'Math':[90,50,70,80],
          'English':[60,70,90,50],
          'History':[33,75,88,60]}
```


* 範例4
```python=
list1 = [[90, 60, 33],
       [50, 70, 75],
       [70, 90, 88],
       [80, 50, 60]]
pd.DataFrame(list1, columns=['Math', 'English', 'History'])
```

範例5

```python=
list1 = [[90, 60, 33],
       [50, 70, 75],
       [70, 90, 88],
       [80, 50, 60]]
df = pd.DataFrame(list1, columns=['Math', 'English', 'History'], 
                  index=['Simon','Allen','Jimmy','Peter'])
# 因為之後的操作都會以這筆資料為主，我們先備份一份到df_orig裡，如果需要還原時就從df_orig還原。
# 要加copy()才會做出新的一份資料，不然兩個變數會存取同一份資料！
df_orig = df.copy()
df
```

* 範例12
```python=
df = df.rename({'Math':'math'}, axis=1)
df
```

* 範例13
```python=
df = df.rename(columns={'English':'english'})
df
```

* 範例14
```python=
df.columns = ['a', 'b', 'c']
df
```

* 範例16
```python=
df = df.reset_index()
df
```

* 範例17
```python=
df = df.set_index('a') 
df
```

* 範例18
```python=
df = df.set_index('index')
df
```

* 範例19
```python=
df = df.reset_index(drop=True)
df
```
## Dataframe Methods

* 範例83
```python=
df.sample(2)
```

* 範例84
```python=
df.describe()
```

* 範例85
```python=
df.mean()
```

* 範例86
```python=
df.sum()
```

* 範例87
```python=
df.max()
```

* 範例88
```python=
df.min()
```

* 範例89
```python=
df.nlargest(1,'Math')
```

* 範例90
```python=
df.nlargest(2,'Math')
```

* 範例91
```python=
df.sort_values('Math', ascending=False)
```

* 範例92
```python=
df.sort_values('Math', ascending=False).head(2)
```

* 範例93
```python=
df.nsmallest(2,'Math')
```

* 範例94
```python=
df.rank(ascending=False)
```


* 範例95
```python=
df['平均'] = df.mean(axis=1).round(2) # 小數點2位
df['名次'] = df['平均'].rank(ascending=False)
df
```


* 範例96
```python=
df['性別'] = ['男','女','男','男']
df
```


* 範例97
```python=
df['性別'].nunique()
```

* 範例98
```python=
df['性別'].unique()
```

* 範例99
```python=
df['性別'].value_counts()
```

## df.to_datetime
* 範例100
```python=
df['日期'] = pd.to_datetime(['2016-01-01','2017-05-03','2017-05-13','2018-01-05'])
df
```

* 範例101
```python=
df['日期'] + pd.Timedelta(2,'D')
```

* 範例102
```python=
df['日期'].dt.year
```

* 範例103
```python=
df['日期'].dt.month
```

* 範例104
```python=
df['日期'].dt.day
```

* 範例105
```python=
df['日期'].dt.weekday_name
```

* 範例106
```python=
df['日期'].dt.quarter
```

* 範例107
```python=
df[df['日期'].dt.year==2017]
```

* 範例108
```python=
df[df['日期'].dt.month==5]
```

* 範例109
```python=
df.set_index('日期', inplace=True)
df
```

* 範例110
```python=
df['2017']
```

* 範例111
```python=
df.loc['2017']
```

* 範例112
```python=
df['2017-05']
```

* 範例113
```python=
df.index.month
```

* 範例114
```python=
df[df.index.month == 1]
```

## xlwings
* [快速入門 - xlwings Documentation](https://docs.xlwings.org/zh_TW/latest/quickstart.html)
## openpyxl
```python
with pd.ExcelWriter("test.xlsx", mode='a', engine="openpyxl") as writer: 
     df.to_excel(writer) 
```
* [使用PythonOpenPyXL模組控制Excel-1. 緣起 - by Sean Yeh - Python Everywhere -from Beginner to Advanced - Medium](https://medium.com/seaniap/%E4%BD%BF%E7%94%A8pythonopenpyxl%E6%A8%A1%E7%B5%84%E6%8E%A7%E5%88%B6excel-1-76274f799d8f)
* [使用PythonOpenPyXL模組控制Excel-2. 接續上次提到的，我們使用OpenPyXL模組來操控Excel的各種編修，這裡繼續… - by Sean Yeh - Python Everywhere -from Beginner to Ad](https://medium.com/seaniap/%E4%BD%BF%E7%94%A8pythonopenpyxl%E6%A8%A1%E7%B5%84%E6%8E%A7%E5%88%B6excel-2-f1ca0135598c)

----
## Tips - Time Series
* [Pandas resample() tricks you should know for manipulating time-series data](https://towardsdatascience.com/pandas-resample-tricks-you-should-know-for-manipulating-time-series-data-7e9643a7e7f3)

----
## Tips
* [Top 3 Pandas Functions You Don't Know About (Probably)](https://towardsdatascience.com/top-3-pandas-functions-you-dont-know-about-probably-5ae9e1c964c8)
* [How to insert a new row in a Pandas Dataframe--SaralGyaan](https://saralgyaan.com/posts/how-to-insert-a-new-row-in-a-pandas-dataframe/#:~:text=You%20can%20also%20insert%20a%20new%20row%20to,desired%20index%20of%20the%20row%20in%20np.insert%20%28%29.)
* [Remove duplicates from dataframe, based on two columns A,B, keeping row with max value in another column C](https://stackoverflow.com/questions/32093829/remove-duplicates-from-dataframe-based-on-two-columns-a-b-keeping-row-with-max)
```python=
df.sort('C').drop_duplicates(subset=['A', 'B'], keep='last')
```
* [5 Interesting Jupyter Interactive Visualization Extensions - by Cornellius Yudha Wijaya - Oct, 2021 - Towards Data Science](https://towardsdatascience.com/5-interesting-jupyter-interactive-visualization-extensions-ab030c8d0eb9)
* [6 Pandas Mistakes That Silently Tell You Are a Rookie - Towards Data Science](https://towardsdatascience.com/6-pandas-mistakes-that-silently-tell-you-are-a-rookie-b566a252e60d)
* Columns operation
    * [Pandas – Split Column by Delimiter](https://datascienceparichay.com/article/pandas-split-column-by-delimiter/)
    * [pandas.Series.str.split](https://pandas.pydata.org/docs/reference/api/pandas.Series.str.split.html)
###### tags: `pandas` `python` `pd` `pgk`