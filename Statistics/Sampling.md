----------------------------------------------------------------------------------------------------------------------------------------------------------------
# Sampling
https://rfriend.tistory.com/58

1) 단순 임의 추출 (Simple random sampling)
* 모집단으로부터 샘플을 균등하게 임의로 추출하는 방법 (복원추출, 비복원추출)

2) 계통적 추출 (Systematic sampling)
* 무작위로 배열된 표본에서 시간적 혹은 공간적으로 일정한 간격을 두고 표본 추출 (ex. 매 5번째 추출 등)

3) 층화 임의 추출 (Stratified random sampling)
* 모집단이 몇 개의 계층으로 구성되어 있을 때, 각 계층 원소로부터 임의 추출 (ex. 성별, 연령대별 등)

4) 군집 추출 (cluster sampling)
* 모집단이 여러 군집을 이룰 때, 우선 군집을 선택하고 그 집단에서 표본을 추출

5) 다단계 추출 (multi-stage sampling)
* 여러 단계로 나누어서 표본 추출 수행
----------------------------------------------------------------------------------------------------------------------------------------------------------------

## 층화추출법
> * 층화추출법(Stratified sampling)은 모집단을 먼저 중복되지 않도록 층으로 나눈 다음 각 층에서 표본을 추출하는 방법이다. 
    * 층을 나눌 때 층내는 동질적, 층간은 이질적 특성을 가지도록 하면 적은 비용으로 더 정확한 추정을 할 수 있으며,전체 모집단뿐만 아니라 각 층의 특성에 대한 추정도 할 수 있다. 
    
**활용 분야** 
* 층화추출법은 표본조사방법에서 실제적으로 가장 많이 이용되는 추출법이다. 
    * 단순임의추출의 단점을 보완하려는 목적 및 기타 다른 추출법과 비교하여 적은 비용으로 추정치를 다소 정확히 구할 수 있다.
    
**장점** <br>
> 1) 단순임의 추출보다 신뢰성이 높은 추정치를 구할 수 있다.<br>
각 층을 동질적으로 묶어 층화함으로써 층화추출에서 구한 추정치의 분산이 단순임의추출로 구한 추정치의 분산보다 적어지기 때문에 보다 신뢰성이 높은 추정치를 구할 수 있다.

> 2) 비용 절감 및 자료분석이 용이하다.<br>
비용을 줄일 수 있음은 물론 자료정리나 분석이 용이한 이유는 층화추출에 의해 표본으로 선택된 단위만을 조사하기 때문이다.

> 3) 각 층에 대한 추정치를 부수적으로 구할 수 있다.<br>
이는 각 층을 동일성을 갖는 집단으로 구분하여 층화하기 때문에 각 층이 하나의 대상이 되는 경우가 있다. 이러한 경우 각 층에 대한 부수적인 자료를 구할 수 있다.

**단점**<br>
> 1) 방대한 모집단의 경우 목록작성의 어려움<br>
모집단의 크기가 너무도 큰 경우 목록을 작성하는 경우는 표본 추출을 하는 것보다 어려울 때가 많다.

> 2) 정확한 정보 필요<br>
적절하게 층을 나누기 위해서는 모집단 각 층에 대한 정확한 정보를 필요로 한다

> 3) 층화의 어려움<br>
층화추출에서 가장 중요한 층 내에 동질성과 층 간에 이질성을 갖추어야 하는 문제에서 이는 이론상으로는 쉬울 수 있으나 이를 실질적으로 층화하는 과정에서는 어려움을 동반하는 경우가 많다.


```python
from sklearn.model_selection import StratifiedShuffleSplit
```


```python
# 층화추출법 쓰려면 그룹을 먼저 나눠져있어야 함.
split = StratifiedShuffleSplit(n_splits=1, test_size=0.04, random_state=1004)

for train_idx, test_idx in split.split(df, df["grp"]):
    df_strat_train = df_photoSlide.loc[train_idx]
    df_strat_test = df_photoSlide.loc[test_idx]
```

### 계통적 추출 (Systematic sampling)
https://towardsdatascience.com/probability-sampling-with-python-8c977ad78664

**1) 독립적인 두집단 차이 검정 => Mannwhitneyu 검정** <br>
> 비모수검정 중 Mannwhitneyu 검정 사용. 두 집단 비교이면서, 표본 수가 다르기 때문.

* G-power로 산출된 적정 샘플수 = 그룹당 527
    * 그룹B 의 적정 샘플수를 위한 step = 16
    * 그룹C 의 적정 샘플수를 위한 step = 13
    
* 결과
    * 계통적추출 방법으로 샘플링한 경우, 그룹B와 그룹C 간의 차이가 있다고 할 수 있다.


```python
# 그룹별 샘플수 = 527
print('groupB',groupB.shape)   
print('groupC',groupC.shape)
```

    groupB (8518, 3)
    groupC (6579, 3)



```python
# G-power로 나온 적정 샘플수 = 527에 근사하게 step을 잡기 위함
print('그룹B Systematic-sampling 수',len(np.arange(0,len(groupB['pv']),step=16)))
print('그룹C Systematic-sampling 수',len(np.arange(0,len(groupC['pv']),step=13)))
```

    그룹B Systematic-sampling 수 533
    그룹C Systematic-sampling 수 507



```python
# Define systematic sampling function
def systematic_sampling(df, step):
    indexes = np.arange(0,len(df),step=step)
    systematic_sample = df.iloc[indexes]
    return systematic_sample
    
# Obtain a systematic sample and save it in a new variable
systematic_sampleB = systematic_sampling(photoSlide_groupB['pv'], 16)    # index값
systematic_sampleC = systematic_sampling(photoSlide_groupC['pv'], 13)    # index값
```


```python
from scipy.stats import mannwhitneyu
mannwhitneyu(systematic_sampleB.values, systematic_sampleC.values)
```




    MannwhitneyuResult(statistic=128164.0, pvalue=0.04829569428305991)




```python
# 한번더 시행.
systematic_sampleB = systematic_sampling(photoSlide_groupB['pv'], 15) 
systematic_sampleC = systematic_sampling(photoSlide_groupC['pv'], 12) 
mannwhitneyu(systematic_sampleB.values, systematic_sampleC.values)
```




    MannwhitneyuResult(statistic=144244.5, pvalue=0.005782949309935229)



**2) 독립적인 세집단 차이 검정** => kruskal-wallis<br>
> 비모수 검정중 kruskal-wallis 검정법 사용. 세 집단이면서 표본수 동일

* G-power로 산출된 적정 샘플수 = 그룹당 423
    * 그룹A 의 적정 샘플수를 위한 step = 115
    * 그룹B 의 적정 샘플수를 위한 step = 133
    * 그룹C 의 적정 샘플수를 위한 step = 129


```python
# 그룹별 샘플수 = 527
print('groupA',photoSlide_allArea_groupA.shape)
print('groupB',photoSlide_allArea_groupB.shape)   
print('groupC',photoSlide_allArea_groupC.shape)
```

    groupA (48615, 3)
    groupB (56240, 3)
    groupC (54285, 3)



```python
# G-power로 산출된 적정 샘플수 = 그룹당 423
print('그룹A Systematic-sampling 수',len(np.arange(0,len(allArea_groupA['pv']),step=115)))
print('그룹B Systematic-sampling 수',len(np.arange(0,len(allArea_groupB['pv']),step=133)))
print('그룹C Systematic-sampling 수',len(np.arange(0,len(allArea_groupC['pv']),step=129)))
```

    그룹A Systematic-sampling 수 423
    그룹B Systematic-sampling 수 423
    그룹C Systematic-sampling 수 421



```python
systematic_allArea_sampleA= systematic_sampling(photoSlide_allArea_groupA['pv'], 116)    # index값
systematic_allArea_sampleB = systematic_sampling(photoSlide_allArea_groupB['pv'], 134)    # index값
systematic_allArea_sampleC = systematic_sampling(photoSlide_allArea_groupC['pv'], 130)    # index값

# 2) 통계검정
stats.kruskal(systematic_allArea_sampleA.values,  systematic_allArea_sampleB.values,systematic_allArea_sampleC.values)
```




    KruskalResult(statistic=0.09646906132343865, pvalue=0.9529102741910516)




```python
# 2) 2차검정
stats.kruskal(systematic_allArea_sampleA.values,  systematic_allArea_sampleB.values,systematic_allArea_sampleC.values)
```




    KruskalResult(statistic=2.609501152629566, pvalue=0.27124018033443853)




```python

```


```python

```
