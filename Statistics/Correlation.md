# Correlation
* 일자 : 2020-03-19

### 피어슨 상관계수 
* (x와 y가 함께 변하는 정도) / (x와 y가 각각 변하는 정도)

#### [ 사용시 주의점 ]
- 상관관계가 인과관계를 의미하는 것은 아님. 단순히 두 변수의 연관성을 확인하는 것.
- 두 변수가 정규분포일 때 잘 작동한다. 
- 이상치(outlier)에 민감하므로, 이상치는 제거하는 것이 좋음.
- 두 변수가 완전히 동일하면 피어슨 상관계수는 1.0이다. 완전히 반대방향으로 동일하면 -1.0, 전혀 상관 없으면 0이다.

### what I Learned

outlier제거 전과 후 상관계수 차이
> * 99.7percentile 이상값 제거하여 상관관계 다시 살펴봤더니, 상관계수가 outlier제거 전 보다 약간 상승함
    * ss와 aa의 상관계수가 0.17 이었는데 0.39로 증가.
    
스케일링 전 후 상관계수 차이
> * 스케일링 전후로는 상관계수가 차이가 없음.


```python
import numpy as np
import pandas as pd
from pandas import Series, DataFrame
import matplotlib as mpl
import matplotlib.pyplot as plt
import seaborn as sns
import scipy as sp
```


```python
import chart_studio.plotly as py
# import cufflinks as cf
from plotly.offline import plot
import plotly.express as px
```


```python
# warning 무시
import warnings
warnings.filterwarnings(action='ignore')
```


```python
df_notzero=pd.read_excel('./data/yt_data.xlsx')
```


```python
df_notzero=df_notzero.drop(columns='Unnamed: 0')
```


```python
# v1 : ad, v2: search, v3: contents
df_notzero.columns=['id','cnt','yt_cnt','yt_prop','aa','ss','cc']
```

### **원본 데이터로 상관관계 분석**


```python
df_corr=df_notzero[['yt_prop','aa','ss','cc']]
df_corr.head()
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
      <th>yt_prop</th>
      <th>aa</th>
      <th>ss</th>
      <th>cc</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>0.02</td>
      <td>0</td>
      <td>2</td>
      <td>0</td>
    </tr>
    <tr>
      <td>1</td>
      <td>0.29</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>2</td>
      <td>0.10</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>3</td>
      <td>0.06</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>4</td>
      <td>0.01</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



**상관관계 확인**


```python
df_corr.corr()
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
      <th>yt_prop</th>
      <th>aa</th>
      <th>ss</th>
      <th>cc</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>yt_prop</td>
      <td>1.000000</td>
      <td>-0.091848</td>
      <td>-0.121276</td>
      <td>-0.157065</td>
    </tr>
    <tr>
      <td>aa</td>
      <td>-0.091848</td>
      <td>1.000000</td>
      <td>0.168031</td>
      <td>0.226419</td>
    </tr>
    <tr>
      <td>ss</td>
      <td>-0.121276</td>
      <td>0.168031</td>
      <td>1.000000</td>
      <td>0.292377</td>
    </tr>
    <tr>
      <td>cc</td>
      <td>-0.157065</td>
      <td>0.226419</td>
      <td>0.292377</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>



### **heatmap**
> * aa, ss, cc 모두 yt_prop과의 상관계수가 -0.1~ -0.2 이내이므로 거의 무시될수 있는 선형관계로 봐도 무관.
> * aa와 cc간의 상관계수가 0.2, ss과 cc 간의 상관계수가 0.3으로 약한 양의 상관관계를 띈다.


```python
plt.figure(figsize=(12,7))
ax = sns.heatmap(data=df_corr.corr(), annot=True, fmt='.2f', linewidths=.5, cmap="YlGn")
buttom, top= ax.get_ylim()
ax.set_ylim(buttom+0.5, top-0.9)
```




    (4.0, -0.4)




![png](./pic/output_14_1.png)


------------------------------------------
### **outlier제거**
* 제거 기준 : 99.7percentile이상 제거


```python
df_notzero.shape
```




    (515474, 7)




```python
# ad, se, con
P_ss=np.percentile(df_notzero['ss'],[1,99.7])
P_cc=np.percentile(df_notzero['cc'],[1,99.7])
P_aa=np.percentile(df_notzero['aa'],[1,99.7])
```


```python
print("ss",P_ss[1])
print("cc",P_cc[1])
print("aa",P_aa[1])
```

    ss 146.0
    cc 280.0
    aa 12.0



```python
df_out_ss=df_notzero[(df_notzero['ss']<P_ss[1])]
df_out_cc=df_notzero[df_notzero['cc']<P_cc[1]]
df_out_aa=df_notzero[df_notzero['aa']<P_aa[1]]
print("ss outlier제거",df_out_ss.shape)
print("cc outlier제거",df_out_cc.shape)
print("aa outlier제거",df_out_aa.shape)
```

    ss outlier제거 (513912, 7)
    cc outlier제거 (513907, 7)
    aa outlier제거 (513663, 7)


### **outlier제거한 데이터셋**
* outlier제거 전 : 515,474 
* outlier제거 후: 510,822 (99%)


```python
df_out_ss=df_out_ss[['id','ss']].reset_index(drop=True)
df_out_cc=df_out_cc[['id','cc']].reset_index(drop=True)
df_out_aa=df_out_aa[['id','aa']].reset_index(drop=True)
df_yt=df_notzero[['id','yt_prop']].reset_index(drop=True)
```


```python
df_corr_out=pd.merge(df_yt,
        pd.merge(df_out_ss,
                pd.merge(df_out_cc,df_out_aa,how='left',on='id'),how='left',on='id'),how='left',on='id').dropna(axis=0)
df_corr_out=df_corr_out[['yt_prop','ss','cc','aa']]
df_corr_out.columns=['yt','aa','ss','cc']
```


```python
df_corr_out.shape
```




    (510822, 4)




```python
df_corr_out.head()
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
      <th>yt</th>
      <th>aa</th>
      <th>ss</th>
      <th>cc</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>0.02</td>
      <td>2.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>1</td>
      <td>0.29</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>2</td>
      <td>0.10</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>3</td>
      <td>0.06</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>4</td>
      <td>0.01</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>



### **heatmap**
> * aa, ss, cc 모두 yt_prop과의 상관계수는 음의 상관성을 띔.
> * aa와 ss 간의 상관계수가 0.4로 중간정도의 양의상관을 갖고 있다.
> * aa와 cc, ss과 cc 간의 상관계수는 0.22, 0.25로 약한 양의상관성을 갖고 있다.



```python
plt.figure(figsize=(12,7))
ax = sns.heatmap(data=df_corr_out.corr(), annot=True, fmt='.2f', linewidths=.5, cmap='Blues')
buttom, top= ax.get_ylim()
ax.set_ylim(buttom+0.5, top-0.9)
```




    (4.0, -0.4)




![png](./pic/output_26_1.png)


### **outlier 제거 and 스케일링**


```python
from sklearn.preprocessing import RobustScaler
robustScaler = RobustScaler()
```


```python
feature = robustScaler.fit(df_corr_out)
feature = pd.DataFrame(robustScaler.transform(df_corr_out))
feature.head()
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>-0.375</td>
      <td>-0.111111</td>
      <td>-0.125</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>1</td>
      <td>3.000</td>
      <td>-0.333333</td>
      <td>-0.125</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>2</td>
      <td>0.625</td>
      <td>-0.333333</td>
      <td>-0.125</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>3</td>
      <td>0.125</td>
      <td>-0.333333</td>
      <td>-0.125</td>
      <td>0.0</td>
    </tr>
    <tr>
      <td>4</td>
      <td>-0.500</td>
      <td>-0.333333</td>
      <td>-0.125</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>



### **heatmap**


```python
plt.figure(figsize=(12,7))
ax = sns.heatmap(data=feature.corr(), annot=True, fmt='.2f', linewidths=.5, cmap='viridis')
buttom, top= ax.get_ylim()
ax.set_ylim(buttom+0.5, top-0.9)
```




    (4.0, -0.4)




![png](./pic/output_31_1.png)



```python

```


```python

```


```python

```
