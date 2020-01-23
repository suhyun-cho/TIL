

```python
import numpy as np
import pandas as pd
from pandas import Series, DataFrame
import matplotlib as mpl
import matplotlib.pyplot as plt
import seaborn as sns
sns.set_style('darkgrid')
plt.style.use('ggplot')
#plt.style.use('fivethirtyeight')
import scipy as sp
import re
```


```python
# warning 무시
import warnings
warnings.filterwarnings(action='ignore')
```


```python
pip install plotly==3.10.0
```


```python
pip install chart_studio
```


```python
conda uninstall plotly
```


```python
pip uninstall chart-studio
```


```python
conda uninstall chart-studio
```


```python
conda install -c plotly plotly chart-studio
```


```python
# plotly version = 3.8.1
import chart_studio.plotly as py
#import plotly.plotly as py
import cufflinks as cf
print(cf.__version__)
```

    0.17.0
    


```python
from plotly.offline import plot
```


```python
import plotly
plotly.__version__
```




    '4.5.0'



----------------
### What I learned
* 날짜 데이터 read_csv 로 불러올때
    * parse_dates={'날짜':["년","월"]}
* pivot_table 만들기
    * index 가 행값, column은 열값, values 는 들어갈 값
* isin 구문
    * df[df['type2'].isin(['PV','UV'])]   # PV,UV가 들어있는 경우
* isin 구문 활용해서 없는 값 뽑을 때
    * df[df['type2'].isin(['PV','UV'])==False]   # PV,UV가 없는 경우
* query함수 작성법
    * df.query('type1=="트래픽" and type2=="UV" and service=="뉴스"')[['service','value']]
    * df.query('type2!=["PV","UV","일평균방문횟수"]')['type2']

-----------------
### 한글폰트 설정
https://financedata.github.io/posts/matplotlib-hangul-for-windows-anaconda.html

* 로컬에서 matplotlib 폰트 위치
    * C:\Users\suhyuncho\Anaconda3\Lib\site-packages\matplotlib\mpl-data\fonts\ttf


```python
print ('버전: ', mpl.__version__)
print ('설치 위치: ', mpl.__file__)
print ('설정 위치: ', mpl.get_configdir())
print ('캐시 위치: ', mpl.get_cachedir())
```

    버전:  3.0.3
    설치 위치:  C:\Users\suhyuncho\Anaconda3\lib\site-packages\matplotlib\__init__.py
    설정 위치:  C:\Users\suhyuncho\.matplotlib
    캐시 위치:  C:\Users\suhyuncho\.matplotlib
    


```python
print ('설정 파일 위치: ', mpl.matplotlib_fname())
```

    설정 파일 위치:  C:\Users\suhyuncho\Anaconda3\lib\site-packages\matplotlib\mpl-data\matplotlibrc
    


```python
import os
os.listdir('C:/Windows/Fonts/')
```




    ['8514fix.fon',
     '8514fixe.fon',
     '8514fixg.fon',
     '8514fixr.fon',
     '8514fixt.fon',
     '8514oem.fon',
     '8514oeme.fon',
     '8514oemg.fon',
     '8514oemr.fon',
     '8514oemt.fon',
     '8514sys.fon',
     '8514syse.fon',
     '8514sysg.fon',
     '8514sysr.fon',
     '8514syst.fon',
     '85775.fon',
     '85855.fon',
     '85f1255.fon',
     '85f1256.fon',
     '85f1257.fon',
     '85f874.fon',
     '85s1255.fon',
     '85s1256.fon',
     '85s1257.fon',
     '85s874.fon',
     'AGENCYB.TTF',
     'AGENCYR.TTF',
     'ALGER.TTF',
     'ANTQUAB.TTF',
     'ANTQUABI.TTF',
     'ANTQUAI.TTF',
     'app775.fon',
     'app850.fon',
     'app852.fon',
     'app855.fon',
     'app857.fon',
     'app866.fon',
     'app932.fon',
     'app936.fon',
     'app949.fon',
     'app950.fon',
     'arial.ttf',
     'arialbd.ttf',
     'arialbi.ttf',
     'ariali.ttf',
     'ARIALN.TTF',
     'ARIALNB.TTF',
     'ARIALNBI.TTF',
     'ARIALNI.TTF',
     'ariblk.ttf',
     'ARLRDBD.TTF',
     'bahnschrift.ttf',
     'BASKVILL.TTF',
     'batang.ttc',
     'BAUHS93.TTF',
     'BELL.TTF',
     'BELLB.TTF',
     'BELLI.TTF',
     'BERNHC.TTF',
     'BKANT.TTF',
     'BOD_B.TTF',
     'BOD_BI.TTF',
     'BOD_BLAI.TTF',
     'BOD_BLAR.TTF',
     'BOD_CB.TTF',
     'BOD_CBI.TTF',
     'BOD_CI.TTF',
     'BOD_CR.TTF',
     'BOD_I.TTF',
     'BOD_PSTC.TTF',
     'BOD_R.TTF',
     'BOOKOS.TTF',
     'BOOKOSB.TTF',
     'BOOKOSBI.TTF',
     'BOOKOSI.TTF',
     'BRADHITC.TTF',
     'BRITANIC.TTF',
     'BRLNSB.TTF',
     'BRLNSDB.TTF',
     'BRLNSR.TTF',
     'BROADW.TTF',
     'BRUSHSCI.TTF',
     'BSSYM7.TTF',
     'c8514fix.fon',
     'c8514oem.fon',
     'c8514sys.fon',
     'calibri.ttf',
     'calibrib.ttf',
     'calibrii.ttf',
     'calibril.ttf',
     'calibrili.ttf',
     'calibriz.ttf',
     'CALIFB.TTF',
     'CALIFI.TTF',
     'CALIFR.TTF',
     'CALIST.TTF',
     'CALISTB.TTF',
     'CALISTBI.TTF',
     'CALISTI.TTF',
     'cambria.ttc',
     'cambriab.ttf',
     'cambriai.ttf',
     'cambriaz.ttf',
     'Candara.ttf',
     'Candarab.ttf',
     'Candarai.ttf',
     'Candaral.ttf',
     'Candarali.ttf',
     'Candaraz.ttf',
     'CASTELAR.TTF',
     'CENSCBK.TTF',
     'CENTAUR.TTF',
     'CENTURY.TTF',
     'cga40737.fon',
     'cga40850.fon',
     'cga40852.fon',
     'cga40857.fon',
     'cga40866.fon',
     'cga40869.fon',
     'cga40woa.fon',
     'cga80737.fon',
     'cga80850.fon',
     'cga80852.fon',
     'cga80857.fon',
     'cga80866.fon',
     'cga80869.fon',
     'cga80woa.fon',
     'CHILLER.TTF',
     'COLONNA.TTF',
     'comic.ttf',
     'comicbd.ttf',
     'comici.ttf',
     'comicz.ttf',
     'consola.ttf',
     'consolab.ttf',
     'consolai.ttf',
     'consolaz.ttf',
     'constan.ttf',
     'constanb.ttf',
     'constani.ttf',
     'constanz.ttf',
     'COOPBL.TTF',
     'COPRGTB.TTF',
     'COPRGTL.TTF',
     'corbel.ttf',
     'corbelb.ttf',
     'corbeli.ttf',
     'corbell.ttf',
     'corbelli.ttf',
     'corbelz.ttf',
     'coue1255.fon',
     'coue1256.fon',
     'coue1257.fon',
     'couf1255.fon',
     'couf1256.fon',
     'couf1257.fon',
     'cour.ttf',
     'courbd.ttf',
     'courbi.ttf',
     'coure.fon',
     'couree.fon',
     'coureg.fon',
     'courer.fon',
     'couret.fon',
     'courf.fon',
     'courfe.fon',
     'courfg.fon',
     'courfr.fon',
     'courft.fon',
     'couri.ttf',
     'CURLZ___.TTF',
     'cvgafix.fon',
     'cvgasys.fon',
     'desktop.ini',
     'dos737.fon',
     'dos869.fon',
     'dosapp.fon',
     'ebrima.ttf',
     'ebrimabd.ttf',
     'ega40737.fon',
     'ega40850.fon',
     'ega40852.fon',
     'ega40857.fon',
     'ega40866.fon',
     'ega40869.fon',
     'ega40woa.fon',
     'ega80737.fon',
     'ega80850.fon',
     'ega80852.fon',
     'ega80857.fon',
     'ega80866.fon',
     'ega80869.fon',
     'ega80woa.fon',
     'ELEPHNT.TTF',
     'ELEPHNTI.TTF',
     'ENGR.TTF',
     'ERASBD.TTF',
     'ERASDEMI.TTF',
     'ERASLGHT.TTF',
     'ERASMD.TTF',
     'FELIXTI.TTF',
     'fms_metadata.xml',
     'FORTE.TTF',
     'FRABK.TTF',
     'FRABKIT.TTF',
     'FRADM.TTF',
     'FRADMCN.TTF',
     'FRADMIT.TTF',
     'FRAHV.TTF',
     'FRAHVIT.TTF',
     'framd.ttf',
     'FRAMDCN.TTF',
     'framdit.ttf',
     'FREESCPT.TTF',
     'FRSCRIPT.TTF',
     'FTLTLT.TTF',
     'Gabriola.ttf',
     'gadugi.ttf',
     'gadugib.ttf',
     'GARA.TTF',
     'GARABD.TTF',
     'GARAIT.TTF',
     'georgia.ttf',
     'georgiab.ttf',
     'georgiai.ttf',
     'georgiaz.ttf',
     'GIGI.TTF',
     'GILBI___.TTF',
     'GILB____.TTF',
     'GILC____.TTF',
     'GILI____.TTF',
     'GILLUBCD.TTF',
     'GILSANUB.TTF',
     'GIL_____.TTF',
     'GLECB.TTF',
     'GlobalMonospace.CompositeFont',
     'GlobalSansSerif.CompositeFont',
     'GlobalSerif.CompositeFont',
     'GlobalUserInterface.CompositeFont',
     'GLSNECB.TTF',
     'GOTHIC.TTF',
     'GOTHICB.TTF',
     'GOTHICBI.TTF',
     'GOTHICI.TTF',
     'GOUDOS.TTF',
     'GOUDOSB.TTF',
     'GOUDOSI.TTF',
     'GOUDYSTO.TTF',
     'gulim.ttc',
     'H2GPRM.TTF',
     'H2GSRB.TTF',
     'H2GTRE.TTF',
     'H2GTRM.TTF',
     'H2HDRM.TTF',
     'H2MJRE.TTF',
     'H2MJSM.TTF',
     'H2MKPB.TTF',
     'H2PORL.TTF',
     'H2PORM.TTF',
     'H2SA1M.TTF',
     'h8514fix.fon',
     'h8514oem.fon',
     'h8514sys.fon',
     'HARLOWSI.TTF',
     'HARNGTON.TTF',
     'HATTEN.TTF',
     'himalaya.ttf',
     'HMFMMUEX.TTC',
     'HMFMOLD.TTF',
     'HMFMPYUN.TTF',
     'HMKMAMI.TTF',
     'HMKMMAG.TTF',
     'HMKMRHD.TTF',
     'holomdl2.ttf',
     'HTOWERT.TTF',
     'HTOWERTI.TTF',
     'hvgafix.fon',
     'hvgasys.fon',
     'impact.ttf',
     'IMPRISHA.TTF',
     'INFROMAN.TTF',
     'Inkfree.ttf',
     'ITCBLKAD.TTF',
     'ITCEDSCR.TTF',
     'ITCKRIST.TTF',
     'j8514fix.fon',
     'j8514oem.fon',
     'j8514sys.fon',
     'javatext.ttf',
     'JOKERMAN.TTF',
     'jsmalle.fon',
     'jsmallf.fon',
     'JUICE___.TTF',
     'jvgafix.fon',
     'jvgasys.fon',
     'KUNSTLER.TTF',
     'LATINWD.TTF',
     'LBRITE.TTF',
     'LBRITED.TTF',
     'LBRITEDI.TTF',
     'LBRITEI.TTF',
     'LCALLIG.TTF',
     'LeelaUIb.ttf',
     'LeelawUI.ttf',
     'LeelUIsl.ttf',
     'LFAX.TTF',
     'LFAXD.TTF',
     'LFAXDI.TTF',
     'LFAXI.TTF',
     'LHANDW.TTF',
     'LSANS.TTF',
     'LSANSD.TTF',
     'LSANSDI.TTF',
     'LSANSI.TTF',
     'LTYPE.TTF',
     'LTYPEB.TTF',
     'LTYPEBO.TTF',
     'LTYPEO.TTF',
     'lucon.ttf',
     'l_10646.ttf',
     'MAGNETOB.TTF',
     'MAIAN.TTF',
     'malgun.ttf',
     'malgunbd.ttf',
     'malgunsl.ttf',
     'marlett.ttf',
     'MATURASC.TTF',
     'micross.ttf',
     'mingliub.ttc',
     'MISTRAL.TTF',
     'mmrtext.ttf',
     'mmrtextb.ttf',
     'MOD20.TTF',
     'modern.fon',
     'monbaiti.ttf',
     'msgothic.ttc',
     'msjh.ttc',
     'msjhbd.ttc',
     'msjhl.ttc',
     'msyh.ttc',
     'msyhbd.ttc',
     'msyhl.ttc',
     'msyi.ttf',
     'MTCORSVA.TTF',
     'mvboli.ttf',
     'NanumBarunGothic.ttf',
     'NanumBarunGothicBold.ttf',
     'NanumBarunGothicLight.ttf',
     'NanumBarunGothicUltraLight.ttf',
     'NGULIM.TTF',
     'NIAGENG.TTF',
     'NIAGSOL.TTF',
     'Nirmala.ttf',
     'NirmalaB.ttf',
     'NirmalaS.ttf',
     'ntailu.ttf',
     'ntailub.ttf',
     'OCRAEXT.TTF',
     'OLDENGL.TTF',
     'ONYX.TTF',
     'OUTLOOK.TTF',
     'pala.ttf',
     'palab.ttf',
     'palabi.ttf',
     'palai.ttf',
     'PALSCRI.TTF',
     'PAPYRUS.TTF',
     'PARCHM.TTF',
     'PERBI___.TTF',
     'PERB____.TTF',
     'PERI____.TTF',
     'PERTIBD.TTF',
     'PERTILI.TTF',
     'PER_____.TTF',
     'phagspa.ttf',
     'phagspab.ttf',
     'PLAYBILL.TTF',
     'POORICH.TTF',
     'PRISTINA.TTF',
     'RAGE.TTF',
     'RAVIE.TTF',
     'REFSAN.TTF',
     'REFSPCL.TTF',
     'ROCCB___.TTF',
     'ROCC____.TTF',
     'ROCK.TTF',
     'ROCKB.TTF',
     'ROCKBI.TTF',
     'ROCKEB.TTF',
     'ROCKI.TTF',
     'roman.fon',
     's8514fix.fon',
     's8514oem.fon',
     's8514sys.fon',
     'SCHLBKB.TTF',
     'SCHLBKBI.TTF',
     'SCHLBKI.TTF',
     'script.fon',
     'SCRIPTBL.TTF',
     'segmdl2.ttf',
     'segoepr.ttf',
     'segoeprb.ttf',
     'segoesc.ttf',
     'segoescb.ttf',
     'segoeui.ttf',
     'segoeuib.ttf',
     'segoeuii.ttf',
     'segoeuil.ttf',
     'segoeuisl.ttf',
     'segoeuiz.ttf',
     'seguibl.ttf',
     'seguibli.ttf',
     'seguiemj.ttf',
     'seguihis.ttf',
     'seguili.ttf',
     'seguisb.ttf',
     'seguisbi.ttf',
     'seguisli.ttf',
     'seguisym.ttf',
     'sere1255.fon',
     'sere1256.fon',
     'sere1257.fon',
     'serf1255.fon',
     'serf1256.fon',
     'serf1257.fon',
     'serife.fon',
     'serifee.fon',
     'serifeg.fon',
     'serifer.fon',
     'serifet.fon',
     'seriff.fon',
     'seriffe.fon',
     'seriffg.fon',
     'seriffr.fon',
     'serifft.fon',
     'SHOWG.TTF',
     'simsun.ttc',
     'simsunb.ttf',
     'Sitka.ttc',
     'SitkaB.ttc',
     'SitkaI.ttc',
     'SitkaZ.ttc',
     'smae1255.fon',
     'smae1256.fon',
     'smae1257.fon',
     'smaf1255.fon',
     'smaf1256.fon',
     'smaf1257.fon',
     'smalle.fon',
     'smallee.fon',
     'smalleg.fon',
     'smaller.fon',
     'smallet.fon',
     'smallf.fon',
     'smallfe.fon',
     'smallfg.fon',
     'smallfr.fon',
     'smallft.fon',
     'SNAP____.TTF',
     'ssee1255.fon',
     'ssee1256.fon',
     'ssee1257.fon',
     'ssee874.fon',
     'ssef1255.fon',
     'ssef1256.fon',
     'ssef1257.fon',
     'ssef874.fon',
     'sserife.fon',
     'sserifee.fon',
     'sserifeg.fon',
     'sserifer.fon',
     'sserifet.fon',
     'sseriff.fon',
     'sseriffe.fon',
     'sseriffg.fon',
     'sseriffr.fon',
     'sserifft.fon',
     'StaticCache.dat',
     'STENCIL.TTF',
     'svgafix.fon',
     'svgasys.fon',
     'sylfaen.ttf',
     'symbol.ttf',
     'tahoma.ttf',
     'tahomabd.ttf',
     'taile.ttf',
     'taileb.ttf',
     'TCBI____.TTF',
     'TCB_____.TTF',
     'TCCB____.TTF',
     'TCCEB.TTF',
     'TCCM____.TTF',
     'TCMI____.TTF',
     'TCM_____.TTF',
     'TEMPSITC.TTF',
     'times.ttf',
     'timesbd.ttf',
     'timesbi.ttf',
     'timesi.ttf',
     'trebuc.ttf',
     'trebucbd.ttf',
     'trebucbi.ttf',
     'trebucit.ttf',
     'verdana.ttf',
     'verdanab.ttf',
     'verdanai.ttf',
     'verdanaz.ttf',
     'vga737.fon',
     'vga775.fon',
     'vga850.fon',
     'vga852.fon',
     'vga855.fon',
     'vga857.fon',
     'vga860.fon',
     'vga861.fon',
     'vga863.fon',
     'vga865.fon',
     'vga866.fon',
     'vga869.fon',
     'vga932.fon',
     'vga936.fon',
     'vga949.fon',
     'vga950.fon',
     'vgaf1255.fon',
     'vgaf1256.fon',
     'vgaf1257.fon',
     'vgaf874.fon',
     'vgafix.fon',
     'vgafixe.fon',
     'vgafixg.fon',
     'vgafixr.fon',
     'vgafixt.fon',
     'vgaoem.fon',
     'vgas1255.fon',
     'vgas1256.fon',
     'vgas1257.fon',
     'vgas874.fon',
     'vgasys.fon',
     'vgasyse.fon',
     'vgasysg.fon',
     'vgasysr.fon',
     'vgasyst.fon',
     'VINERITC.TTF',
     'VIVALDII.TTF',
     'VLADIMIR.TTF',
     'webdings.ttf',
     'wingding.ttf',
     'WINGDNG2.TTF',
     'WINGDNG3.TTF',
     'YuGothB.ttc',
     'YuGothL.ttc',
     'YuGothM.ttc',
     'YuGothR.ttc']




```python
plt.rcParams["font.family"] = 'NanumBarunGothic.ttf'
```


```python
print (plt.rcParams['font.size'] ) 
print (plt.rcParams['font.family'] )
```

    10.0
    ['NanumBarunGothic.ttf']
    


```python
import matplotlib.font_manager as fm

path = 'C:/Windows/Fonts/NanumBarunGothic.ttf'
fontprop = fm.FontProperties(fname=path, size=8)
```


```python
mpl.get_cachedir()
```




    'C:\\Users\\suhyuncho\\.matplotlib'



### 데이터 불러오기


```python
# 날짜 데이터 불러올 때 
df=pd.read_csv('./data/Ad_cost_traffic.csv',encoding='euc-kr',parse_dates={'날짜':["년","월"]})
df=df.rename(columns={'날짜':'date','분류1':'device','분류2':'shopping_type','서비스분류1':'service','종류1':'type1','종류2':'type2','값':'value'})

# 종합_쇼핑기여 제외
df=df[df['shopping_type']=='종합']
df.head(10)
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
      <th>date</th>
      <th>device</th>
      <th>shopping_type</th>
      <th>service</th>
      <th>type1</th>
      <th>type2</th>
      <th>value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>트래픽</td>
      <td>UV</td>
      <td>12442693.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>트래픽</td>
      <td>PV</td>
      <td>499468949.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>트래픽</td>
      <td>일평균방문횟수</td>
      <td>16111902.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>트래픽 평균단가</td>
      <td>UV</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>트래픽 평균단가</td>
      <td>PV</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>직접광고</td>
      <td>354009020.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>네트워크</td>
      <td>59873778.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>쇼핑</td>
      <td>463578266.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>제휴</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>총매출</td>
      <td>877461064.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_pivot=pd.pivot_table(df, index=['date','device','service'], columns=['type2'],values='value' ).reset_index()
df_pivot.head()
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
      <th>type2</th>
      <th>date</th>
      <th>device</th>
      <th>service</th>
      <th>PV</th>
      <th>UV</th>
      <th>네트워크</th>
      <th>쇼핑</th>
      <th>일평균방문횟수</th>
      <th>제휴</th>
      <th>직접광고</th>
      <th>총매출</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>TV</td>
      <td>2886043.0</td>
      <td>458170.5</td>
      <td>1581022.5</td>
      <td>NaN</td>
      <td>186196.0</td>
      <td>2327833.5</td>
      <td>NaN</td>
      <td>7817711.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>검색</td>
      <td>30893214.0</td>
      <td>2601265.5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1993110.0</td>
      <td>428398268.5</td>
      <td>NaN</td>
      <td>856796536.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>기사박스</td>
      <td>22466677.0</td>
      <td>1218236.5</td>
      <td>22491450.5</td>
      <td>NaN</td>
      <td>1449463.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>44982900.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>뉴스</td>
      <td>5609517.5</td>
      <td>629886.0</td>
      <td>8091387.0</td>
      <td>NaN</td>
      <td>361904.0</td>
      <td>NaN</td>
      <td>250000.0</td>
      <td>16682773.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>스푼피드</td>
      <td>158867.0</td>
      <td>62826.5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10249.0</td>
      <td>275486.5</td>
      <td>NaN</td>
      <td>550972.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# PC, 서비스 전체 트래픽 데이터
data_traffic=df.query('device=="PC" and type1=="트래픽" and (type2=="UV" or type2=="PV") ')[['date', 'device','service','type1','type2','value']]
data_traffic.head()
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
      <th>date</th>
      <th>device</th>
      <th>service</th>
      <th>type1</th>
      <th>type2</th>
      <th>value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>프런트</td>
      <td>트래픽</td>
      <td>UV</td>
      <td>12442693.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>프런트</td>
      <td>트래픽</td>
      <td>PV</td>
      <td>499468949.0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>검색</td>
      <td>트래픽</td>
      <td>UV</td>
      <td>5202366.0</td>
    </tr>
    <tr>
      <th>15</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>검색</td>
      <td>트래픽</td>
      <td>PV</td>
      <td>61786414.0</td>
    </tr>
    <tr>
      <th>28</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>기사박스</td>
      <td>트래픽</td>
      <td>UV</td>
      <td>2436455.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
data_traffic_front=df.query('device=="PC" and service=="프런트" and type1=="트래픽" and (type2=="UV" or type2=="PV") ')[['date', 'device','service','type1','type2','value']]
```


```python
# 광고 타입 (직접광고, 네트워크 ...) 별 매출
## 서비스 전체매출
data_adtype_sales=df.query('type2!=["PV","UV","일평균방문횟수"] and device=="PC" and type1 == "매출 구분"')
data_adtype_sales.head()
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
      <th>date</th>
      <th>device</th>
      <th>shopping_type</th>
      <th>service</th>
      <th>type1</th>
      <th>type2</th>
      <th>value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>직접광고</td>
      <td>354009020.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>네트워크</td>
      <td>59873778.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>쇼핑</td>
      <td>463578266.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>제휴</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>총매출</td>
      <td>877461064.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# # 위와같은 결과
# data_adtype_sales=df[(df['type2'].isin(['PV','UV','일평균방문횟수'])==False)&(df['device']=='PC')&(df['type1']=='매출 구분')]
```


```python
# 날짜별 트래픽
plt.figure(figsize=(17,9))
sns.lineplot(x='date', y='value',markers=True,dashes=False, hue='type2',style="type2",data=data_traffic_front)
plt.show()
```


![png](output_27_0.png)



```python
# 월별 광고 종류별 매출
plt.figure(figsize=(17,9))
plt.rcParams["font.family"] ='NanumBarunGothic'
plt.title('광고 종류별 매출')
# plt.legend(fontproperties=fontprop)
sns.lineplot(x='date', y='value',markers=True,dashes=False, hue='type2',data=data_adtype_sales)
plt.show()
```


![png](output_28_0.png)


---------
# plotly 시각화
[line-chart] https://plot.ly/python/line-charts/  <br>
[bar-chart] https://plot.ly/python/bar-charts/


```python
from plotly.offline import plot
import plotly.express as px
```

#### line-plot 그리는법 1
PV, UV가 같은 dataframe 안에 type2컬럼에 있을 때는 <br>
seaborn 에서 hue처럼 color="" 로 구분가능


```python
# PV, UV가 같은 dataframe안에 있을 때
data_traffic.head()
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
      <th>date</th>
      <th>device</th>
      <th>service</th>
      <th>type1</th>
      <th>type2</th>
      <th>value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>프런트</td>
      <td>트래픽</td>
      <td>UV</td>
      <td>12442693.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>프런트</td>
      <td>트래픽</td>
      <td>PV</td>
      <td>499468949.0</td>
    </tr>
    <tr>
      <th>504</th>
      <td>2018-10-01</td>
      <td>PC</td>
      <td>프런트</td>
      <td>트래픽</td>
      <td>UV</td>
      <td>13439308.0</td>
    </tr>
    <tr>
      <th>505</th>
      <td>2018-10-01</td>
      <td>PC</td>
      <td>프런트</td>
      <td>트래픽</td>
      <td>PV</td>
      <td>561194125.0</td>
    </tr>
    <tr>
      <th>1008</th>
      <td>2018-11-01</td>
      <td>PC</td>
      <td>프런트</td>
      <td>트래픽</td>
      <td>UV</td>
      <td>13308607.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# PV, UV가 같은 dataframe안에 있을 때
fig = px.line(data_traffic_front, x="date", y="value",color="type2",title="월별 PV,UV")
fig.show()
```


<div>
        
        
            <div id="6e1694e0-78fa-42c4-b51d-e6593b6d9f76" class="plotly-graph-div" style="height:525px; width:100%;"></div>
            <script type="text/javascript">
                require(["plotly"], function(Plotly) {
                    window.PLOTLYENV=window.PLOTLYENV || {};
                    
                if (document.getElementById("6e1694e0-78fa-42c4-b51d-e6593b6d9f76")) {
                    Plotly.newPlot(
                        '6e1694e0-78fa-42c4-b51d-e6593b6d9f76',
                        [{"hoverlabel": {"namelength": 0}, "hovertemplate": "type2=UV<br>date=%{x}<br>value=%{y}", "legendgroup": "UV", "line": {"color": "#636efa", "dash": "solid"}, "mode": "lines", "name": "UV", "showlegend": true, "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "xaxis": "x", "y": [12442693.0, 13439308.0, 13308607.0, 12916740.0, 13501607.0, 11847788.0, 12657246.0, 12100658.0, 11630770.0, 11130701.0, 11267725.0, 10840548.0, 10623594.0], "yaxis": "y"}, {"hoverlabel": {"namelength": 0}, "hovertemplate": "type2=PV<br>date=%{x}<br>value=%{y}", "legendgroup": "PV", "line": {"color": "#EF553B", "dash": "solid"}, "mode": "lines", "name": "PV", "showlegend": true, "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "xaxis": "x", "y": [499468949.0, 561194125.0, 558074008.0, 551426931.0, 575578560.0, 488203262.0, 558670136.0, 556896816.0, 556968512.0, 528776273.0, 560294857.0, 522817808.0, 507726363.0], "yaxis": "y"}],
                        {"legend": {"title": {"text": "type2"}, "tracegroupgap": 0}, "template": {"data": {"bar": [{"error_x": {"color": "#2a3f5f"}, "error_y": {"color": "#2a3f5f"}, "marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "bar"}], "barpolar": [{"marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "barpolar"}], "carpet": [{"aaxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "baxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "type": "carpet"}], "choropleth": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "choropleth"}], "contour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "contour"}], "contourcarpet": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "contourcarpet"}], "heatmap": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmap"}], "heatmapgl": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmapgl"}], "histogram": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "histogram"}], "histogram2d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2d"}], "histogram2dcontour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2dcontour"}], "mesh3d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "mesh3d"}], "parcoords": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "parcoords"}], "pie": [{"automargin": true, "type": "pie"}], "scatter": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter"}], "scatter3d": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter3d"}], "scattercarpet": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattercarpet"}], "scattergeo": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergeo"}], "scattergl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergl"}], "scattermapbox": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattermapbox"}], "scatterpolar": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolar"}], "scatterpolargl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolargl"}], "scatterternary": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterternary"}], "surface": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "surface"}], "table": [{"cells": {"fill": {"color": "#EBF0F8"}, "line": {"color": "white"}}, "header": {"fill": {"color": "#C8D4E3"}, "line": {"color": "white"}}, "type": "table"}]}, "layout": {"annotationdefaults": {"arrowcolor": "#2a3f5f", "arrowhead": 0, "arrowwidth": 1}, "coloraxis": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "colorscale": {"diverging": [[0, "#8e0152"], [0.1, "#c51b7d"], [0.2, "#de77ae"], [0.3, "#f1b6da"], [0.4, "#fde0ef"], [0.5, "#f7f7f7"], [0.6, "#e6f5d0"], [0.7, "#b8e186"], [0.8, "#7fbc41"], [0.9, "#4d9221"], [1, "#276419"]], "sequential": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "sequentialminus": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]]}, "colorway": ["#636efa", "#EF553B", "#00cc96", "#ab63fa", "#FFA15A", "#19d3f3", "#FF6692", "#B6E880", "#FF97FF", "#FECB52"], "font": {"color": "#2a3f5f"}, "geo": {"bgcolor": "white", "lakecolor": "white", "landcolor": "#E5ECF6", "showlakes": true, "showland": true, "subunitcolor": "white"}, "hoverlabel": {"align": "left"}, "hovermode": "closest", "mapbox": {"style": "light"}, "paper_bgcolor": "white", "plot_bgcolor": "#E5ECF6", "polar": {"angularaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "radialaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "scene": {"xaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "yaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "zaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}}, "shapedefaults": {"line": {"color": "#2a3f5f"}}, "ternary": {"aaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "baxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "caxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "title": {"x": 0.05}, "xaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}, "yaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}}}, "title": {"text": "\uc6d4\ubcc4 PV,UV"}, "xaxis": {"anchor": "y", "domain": [0.0, 1.0], "title": {"text": "date"}}, "yaxis": {"anchor": "x", "domain": [0.0, 1.0], "title": {"text": "value"}}},
                        {"responsive": true}
                    ).then(function(){
                            
var gd = document.getElementById('6e1694e0-78fa-42c4-b51d-e6593b6d9f76');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })
                };
                });
            </script>
        </div>


위와 같은 결과


```python
# # 월별 프런트 트래픽
# import plotly.graph_objects as go

# fig=go.Figure()
# fig.add_trace(go.Scatter(x=list(data_traffic_front.query('type2=="PV"')['date']), y=list(data_traffic_front.query('type2=="PV"')['value']),
#                          mode='lines+markers',
#                         name='PV'))   # X,Y값은 list형태로 들어가야 함.
# fig.add_trace(go.Scatter(x=list(data_traffic_front.query('type2=="UV"')['date']), y=list(data_traffic_front.query('type2=="UV"')['value']),
#                          mode='lines+markers',
#                         name='UV'))
# fig.show()
```

#### line-plot 그리는법 2
PV,UV가 서로 다른 dataframe안에 있을 때는 <br>
plotly.graph_objects 활용해서 go.Scatter를 각각 그려준다. <br>
dote를 추가하고 싶으면, mode='lines+markers' 로 추가 가능.


```python
data_traffic_front_PV=data_traffic_front.query("type2=='PV'")
data_traffic_front_UV=data_traffic_front.query("type2=='UV'")
```


```python
# 월별 프런트 트래픽
import plotly.graph_objects as go

fig=go.Figure()
fig.add_trace(go.Scatter(x=list(data_traffic_front_PV.date), y=list(data_traffic_front_PV.value),
                         mode='lines+markers',
                        name='PV'))   # X,Y값은 list형태로 들어가야 함.
fig.add_trace(go.Scatter(x=list(data_traffic_front_UV.date), y=list(data_traffic_front_UV.value),
                         mode='lines+markers',
                        name='UV'))
fig.update_layout(
    title={'text':"PC프런트 트래픽",
          'y':0.9,
          'x':0.5,
          'xanchor':'center',
          'yanchor':'top'})
fig.show()
```


<div>
        
        
            <div id="4f4357fe-24e8-4800-894a-dc0a4563e77d" class="plotly-graph-div" style="height:525px; width:100%;"></div>
            <script type="text/javascript">
                require(["plotly"], function(Plotly) {
                    window.PLOTLYENV=window.PLOTLYENV || {};
                    
                if (document.getElementById("4f4357fe-24e8-4800-894a-dc0a4563e77d")) {
                    Plotly.newPlot(
                        '4f4357fe-24e8-4800-894a-dc0a4563e77d',
                        [{"mode": "lines+markers", "name": "PV", "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "y": [499468949.0, 561194125.0, 558074008.0, 551426931.0, 575578560.0, 488203262.0, 558670136.0, 556896816.0, 556968512.0, 528776273.0, 560294857.0, 522817808.0, 507726363.0]}, {"mode": "lines+markers", "name": "UV", "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "y": [12442693.0, 13439308.0, 13308607.0, 12916740.0, 13501607.0, 11847788.0, 12657246.0, 12100658.0, 11630770.0, 11130701.0, 11267725.0, 10840548.0, 10623594.0]}],
                        {"template": {"data": {"bar": [{"error_x": {"color": "#2a3f5f"}, "error_y": {"color": "#2a3f5f"}, "marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "bar"}], "barpolar": [{"marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "barpolar"}], "carpet": [{"aaxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "baxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "type": "carpet"}], "choropleth": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "choropleth"}], "contour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "contour"}], "contourcarpet": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "contourcarpet"}], "heatmap": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmap"}], "heatmapgl": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmapgl"}], "histogram": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "histogram"}], "histogram2d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2d"}], "histogram2dcontour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2dcontour"}], "mesh3d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "mesh3d"}], "parcoords": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "parcoords"}], "pie": [{"automargin": true, "type": "pie"}], "scatter": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter"}], "scatter3d": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter3d"}], "scattercarpet": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattercarpet"}], "scattergeo": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergeo"}], "scattergl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergl"}], "scattermapbox": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattermapbox"}], "scatterpolar": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolar"}], "scatterpolargl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolargl"}], "scatterternary": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterternary"}], "surface": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "surface"}], "table": [{"cells": {"fill": {"color": "#EBF0F8"}, "line": {"color": "white"}}, "header": {"fill": {"color": "#C8D4E3"}, "line": {"color": "white"}}, "type": "table"}]}, "layout": {"annotationdefaults": {"arrowcolor": "#2a3f5f", "arrowhead": 0, "arrowwidth": 1}, "coloraxis": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "colorscale": {"diverging": [[0, "#8e0152"], [0.1, "#c51b7d"], [0.2, "#de77ae"], [0.3, "#f1b6da"], [0.4, "#fde0ef"], [0.5, "#f7f7f7"], [0.6, "#e6f5d0"], [0.7, "#b8e186"], [0.8, "#7fbc41"], [0.9, "#4d9221"], [1, "#276419"]], "sequential": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "sequentialminus": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]]}, "colorway": ["#636efa", "#EF553B", "#00cc96", "#ab63fa", "#FFA15A", "#19d3f3", "#FF6692", "#B6E880", "#FF97FF", "#FECB52"], "font": {"color": "#2a3f5f"}, "geo": {"bgcolor": "white", "lakecolor": "white", "landcolor": "#E5ECF6", "showlakes": true, "showland": true, "subunitcolor": "white"}, "hoverlabel": {"align": "left"}, "hovermode": "closest", "mapbox": {"style": "light"}, "paper_bgcolor": "white", "plot_bgcolor": "#E5ECF6", "polar": {"angularaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "radialaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "scene": {"xaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "yaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "zaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}}, "shapedefaults": {"line": {"color": "#2a3f5f"}}, "ternary": {"aaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "baxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "caxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "title": {"x": 0.05}, "xaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}, "yaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}}}, "title": {"text": "PC\ud504\ub7f0\ud2b8 \ud2b8\ub798\ud53d", "x": 0.5, "xanchor": "center", "y": 0.9, "yanchor": "top"}},
                        {"responsive": true}
                    ).then(function(){
                            
var gd = document.getElementById('4f4357fe-24e8-4800-894a-dc0a4563e77d');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })
                };
                });
            </script>
        </div>



```python
data_traffic.service.unique()
```




    array(['프런트', '검색', '기사박스', '뉴스', '허브', '코인', '여행', '자동차', 'TV', '이슈트렌드',
           '스푼피드', '증권정보', '이글루스'], dtype=object)




```python
# 서비스별 PV,UV
import plotly.graph_objects as go

fig=go.Figure()
fig.add_trace(go.Scatter(x=list(data_traffic.query('type2=="PV"and service=="프런트"')['date']), y=list(data_traffic.query('type2=="PV"and service=="프런트"')['value']),
                         mode='lines+markers',
                        name='프런트'))   # X,Y값은 list형태로 들어가야 함.
fig.add_trace(go.Scatter(x=list(data_traffic.query('type2=="PV"and service=="검색"')['date']), y=list(data_traffic.query('type2=="PV"and service=="검색"')['value']),
                         mode='lines+markers',
                        name='검색')) 
fig.add_trace(go.Scatter(x=list(data_traffic.query('type2=="PV"and service=="기사박스"')['date']), y=list(data_traffic.query('type2=="PV"and service=="기사박스"')['value']),
                         mode='lines+markers',
                        name='기사박스')) 
fig.add_trace(go.Scatter(x=list(data_traffic.query('type2=="PV"and service=="뉴스"')['date']), y=list(data_traffic.query('type2=="PV"and service=="뉴스"')['value']),
                         mode='lines+markers',
                        name='뉴스')) 
fig.add_trace(go.Scatter(x=list(data_traffic.query('type2=="PV"and service=="허브"')['date']), y=list(data_traffic.query('type2=="PV"and service=="허브"')['value']),
                         mode='lines+markers',
                        name='허브')) 

fig.add_trace(
    go.Bar(x=list(data_traffic.query('type2=="PV"and service=="프런트"')['date']), y=list(data_traffic.query('type2=="PV"and service=="프런트"')['value']),
                        name='프런트'))
fig.add_trace(
    go.Bar(x=list(data_traffic.query('type2=="PV"and service=="검색"')['date']), y=list(data_traffic.query('type2=="PV"and service=="검색"')['value']),
                        name='검색')) 
fig.add_trace(
    go.Bar(x=list(data_traffic.query('type2=="PV"and service=="기사박스"')['date']), y=list(data_traffic.query('type2=="PV"and service=="기사박스"')['value']),
                        name='기사박스')) 
fig.add_trace(
    go.Bar(x=list(data_traffic.query('type2=="PV"and service=="뉴스"')['date']), y=list(data_traffic.query('type2=="PV"and service=="뉴스"')['value']),
                        name='뉴스')) 
fig.add_trace(
    go.Bar(x=list(data_traffic.query('type2=="PV"and service=="허브"')['date']), y=list(data_traffic.query('type2=="PV"and service=="허브"')['value']),
                        name='허브')) 


fig.update_layout(
    title={'text':"PC 서비스별 트래픽",
          'y':0.9,
          'x':0.5,
          'xanchor':'center',
          'yanchor':'top'})
fig.show()
```


<div>
        
        
            <div id="7b63dc8a-430e-42d6-8f72-c1c694d52ff4" class="plotly-graph-div" style="height:525px; width:100%;"></div>
            <script type="text/javascript">
                require(["plotly"], function(Plotly) {
                    window.PLOTLYENV=window.PLOTLYENV || {};
                    
                if (document.getElementById("7b63dc8a-430e-42d6-8f72-c1c694d52ff4")) {
                    Plotly.newPlot(
                        '7b63dc8a-430e-42d6-8f72-c1c694d52ff4',
                        [{"mode": "lines+markers", "name": "\ud504\ub7f0\ud2b8", "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "y": [499468949.0, 561194125.0, 558074008.0, 551426931.0, 575578560.0, 488203262.0, 558670136.0, 556896816.0, 556968512.0, 528776273.0, 560294857.0, 522817808.0, 507726363.0]}, {"mode": "lines+markers", "name": "\uac80\uc0c9", "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "y": [61786414.0, 67856995.0, 67055949.0, 64996261.0, 70943299.0, 58098096.0, 66115513.0, 66489893.0, 64390785.0, 59734809.0, 64844132.0, 61820705.0, 60659510.0]}, {"mode": "lines+markers", "name": "\uae30\uc0ac\ubc15\uc2a4", "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "y": [44933353.0, 47675095.0, 44950401.0, 43541496.0, 45889789.0, 24412065.0, 29855687.0, 30802742.0, 22887689.0, 27410437.0, 29579406.0, 32831478.0, 27726714.0]}, {"mode": "lines+markers", "name": "\ub274\uc2a4", "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "y": [11219034.0, 12171678.0, 11588226.0, 10785350.0, 13484806.0, 42371651.0, 44295268.0, 47366983.0, 44406755.0, 41806823.0, 48831140.0, 30476305.0, 25171220.0]}, {"mode": "lines+markers", "name": "\ud5c8\ube0c", "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "y": [8119701.0, 8057643.0, 8354186.0, 7716948.0, 8426780.0, 7523057.0, 10063298.0, 9975113.0, 12162521.0, 11727479.0, 15220634.0, 12497301.0, 10503446.0]}, {"name": "\ud504\ub7f0\ud2b8", "type": "bar", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "y": [499468949.0, 561194125.0, 558074008.0, 551426931.0, 575578560.0, 488203262.0, 558670136.0, 556896816.0, 556968512.0, 528776273.0, 560294857.0, 522817808.0, 507726363.0]}, {"name": "\uac80\uc0c9", "type": "bar", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "y": [61786414.0, 67856995.0, 67055949.0, 64996261.0, 70943299.0, 58098096.0, 66115513.0, 66489893.0, 64390785.0, 59734809.0, 64844132.0, 61820705.0, 60659510.0]}, {"name": "\uae30\uc0ac\ubc15\uc2a4", "type": "bar", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "y": [44933353.0, 47675095.0, 44950401.0, 43541496.0, 45889789.0, 24412065.0, 29855687.0, 30802742.0, 22887689.0, 27410437.0, 29579406.0, 32831478.0, 27726714.0]}, {"name": "\ub274\uc2a4", "type": "bar", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "y": [11219034.0, 12171678.0, 11588226.0, 10785350.0, 13484806.0, 42371651.0, 44295268.0, 47366983.0, 44406755.0, 41806823.0, 48831140.0, 30476305.0, 25171220.0]}, {"name": "\ud5c8\ube0c", "type": "bar", "x": ["2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00"], "y": [8119701.0, 8057643.0, 8354186.0, 7716948.0, 8426780.0, 7523057.0, 10063298.0, 9975113.0, 12162521.0, 11727479.0, 15220634.0, 12497301.0, 10503446.0]}],
                        {"template": {"data": {"bar": [{"error_x": {"color": "#2a3f5f"}, "error_y": {"color": "#2a3f5f"}, "marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "bar"}], "barpolar": [{"marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "barpolar"}], "carpet": [{"aaxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "baxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "type": "carpet"}], "choropleth": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "choropleth"}], "contour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "contour"}], "contourcarpet": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "contourcarpet"}], "heatmap": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmap"}], "heatmapgl": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmapgl"}], "histogram": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "histogram"}], "histogram2d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2d"}], "histogram2dcontour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2dcontour"}], "mesh3d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "mesh3d"}], "parcoords": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "parcoords"}], "pie": [{"automargin": true, "type": "pie"}], "scatter": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter"}], "scatter3d": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter3d"}], "scattercarpet": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattercarpet"}], "scattergeo": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergeo"}], "scattergl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergl"}], "scattermapbox": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattermapbox"}], "scatterpolar": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolar"}], "scatterpolargl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolargl"}], "scatterternary": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterternary"}], "surface": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "surface"}], "table": [{"cells": {"fill": {"color": "#EBF0F8"}, "line": {"color": "white"}}, "header": {"fill": {"color": "#C8D4E3"}, "line": {"color": "white"}}, "type": "table"}]}, "layout": {"annotationdefaults": {"arrowcolor": "#2a3f5f", "arrowhead": 0, "arrowwidth": 1}, "coloraxis": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "colorscale": {"diverging": [[0, "#8e0152"], [0.1, "#c51b7d"], [0.2, "#de77ae"], [0.3, "#f1b6da"], [0.4, "#fde0ef"], [0.5, "#f7f7f7"], [0.6, "#e6f5d0"], [0.7, "#b8e186"], [0.8, "#7fbc41"], [0.9, "#4d9221"], [1, "#276419"]], "sequential": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "sequentialminus": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]]}, "colorway": ["#636efa", "#EF553B", "#00cc96", "#ab63fa", "#FFA15A", "#19d3f3", "#FF6692", "#B6E880", "#FF97FF", "#FECB52"], "font": {"color": "#2a3f5f"}, "geo": {"bgcolor": "white", "lakecolor": "white", "landcolor": "#E5ECF6", "showlakes": true, "showland": true, "subunitcolor": "white"}, "hoverlabel": {"align": "left"}, "hovermode": "closest", "mapbox": {"style": "light"}, "paper_bgcolor": "white", "plot_bgcolor": "#E5ECF6", "polar": {"angularaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "radialaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "scene": {"xaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "yaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "zaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}}, "shapedefaults": {"line": {"color": "#2a3f5f"}}, "ternary": {"aaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "baxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "caxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "title": {"x": 0.05}, "xaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}, "yaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}}}, "title": {"text": "PC \uc11c\ube44\uc2a4\ubcc4 \ud2b8\ub798\ud53d", "x": 0.5, "xanchor": "center", "y": 0.9, "yanchor": "top"}},
                        {"responsive": true}
                    ).then(function(){
                            
var gd = document.getElementById('7b63dc8a-430e-42d6-8f72-c1c694d52ff4');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })
                };
                });
            </script>
        </div>



```python

```

### bar-plot 


```python
data_adtype_sales.head()
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
      <th>date</th>
      <th>device</th>
      <th>shopping_type</th>
      <th>service</th>
      <th>type1</th>
      <th>type2</th>
      <th>value</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>직접광고</td>
      <td>354009020.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>네트워크</td>
      <td>59873778.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>쇼핑</td>
      <td>463578266.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>제휴</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2018-09-01</td>
      <td>PC</td>
      <td>종합</td>
      <td>프런트</td>
      <td>매출 구분</td>
      <td>총매출</td>
      <td>877461064.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
fig = px.bar(data_adtype_sales, x='date', y='value', color='type2',title='광고 종류별 매출')
fig.show()
```


<div>
        
        
            <div id="426a6e4c-55ea-49d3-ba84-731aa7eb9f00" class="plotly-graph-div" style="height:525px; width:100%;"></div>
            <script type="text/javascript">
                require(["plotly"], function(Plotly) {
                    window.PLOTLYENV=window.PLOTLYENV || {};
                    
                if (document.getElementById("426a6e4c-55ea-49d3-ba84-731aa7eb9f00")) {
                    Plotly.newPlot(
                        '426a6e4c-55ea-49d3-ba84-731aa7eb9f00',
                        [{"alignmentgroup": "True", "hoverlabel": {"namelength": 0}, "hovertemplate": "type2=\uc9c1\uc811\uad11\uace0<br>date=%{x}<br>value=%{y}", "legendgroup": "\uc9c1\uc811\uad11\uace0", "marker": {"color": "#636efa"}, "name": "\uc9c1\uc811\uad11\uace0", "offsetgroup": "\uc9c1\uc811\uad11\uace0", "orientation": "v", "showlegend": true, "textposition": "auto", "type": "bar", "x": ["2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00"], "xaxis": "x", "y": [354009020.0, null, null, 500000.0, null, 500000.0, null, null, null, null, null, null, null, 362897480.0, null, null, null, null, null, null, null, null, null, null, null, null, 378614550.0, null, null, null, null, 1000000.0, null, 200000.0, null, null, null, null, null, 415522920.0, null, null, null, null, null, null, 200000.0, null, null, null, null, null, 440863670.0, null, null, null, null, null, null, 400000.0, null, null, null, null, null, 348846100.0, null, null, null, null, 300000.0, null, 300000.0, null, null, null, null, null, 386217860.0, null, null, null, null, null, null, 550000.0, null, null, null, null, null, 381829700.0, null, null, null, null, null, null, 150000.0, null, null, null, null, null, 370309000.0, null, null, null, null, null, null, 150000.0, null, null, null, null, null, 379152150.0, null, null, 5000000.0, null, null, null, 150000.0, null, null, null, null, null, 406857050.0, null, null, 500000.0, null, null, null, 150000.0, null, null, null, null, null, 366447850.0, null, null, null, null, null, null, 150000.0, null, null, null, null, null, 331231450.0, null, null, null, null, null, null, 150000.0, null, null, null, null, null], "yaxis": "y"}, {"alignmentgroup": "True", "hoverlabel": {"namelength": 0}, "hovertemplate": "type2=\ub124\ud2b8\uc6cc\ud06c<br>date=%{x}<br>value=%{y}", "legendgroup": "\ub124\ud2b8\uc6cc\ud06c", "marker": {"color": "#EF553B"}, "name": "\ub124\ud2b8\uc6cc\ud06c", "offsetgroup": "\ub124\ud2b8\uc6cc\ud06c", "orientation": "v", "showlegend": true, "textposition": "auto", "type": "bar", "x": ["2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00"], "xaxis": "x", "y": [59873778.0, null, 44982900.0, 16182773.0, 10295417.0, 240849.0, 360666.0, 1773949.0, 3162045.0, null, null, null, 1424793.0, 69964782.0, null, 48998390.0, 17609344.0, 10215018.0, 327208.0, 352707.0, 1781740.0, 4075632.0, null, null, null, 1411672.0, 78824804.0, null, 48433595.0, 17451406.0, 11598219.0, 409870.0, 406849.0, 1924201.0, 3936935.0, null, null, null, 1471511.0, 75269397.0, null, 46520628.0, 15781734.0, 11238319.0, 384706.0, 353983.0, 2355539.0, 4389256.0, null, null, null, 1347988.0, 75006000.0, null, 45446534.0, 15355218.0, 13983051.0, 392592.0, 284569.0, 2337993.0, 10393891.0, null, null, null, 1323164.0, 61071957.0, null, 26813000.0, 16963340.0, 12539977.0, 316699.0, 255965.0, 1876914.0, 9112992.0, null, null, null, 1048305.0, 59716246.0, null, 33289128.0, 21079358.0, 16421134.0, 210151.0, 223353.0, 1775503.0, 10126630.0, null, null, null, 1178304.0, 63338702.0, null, 35540465.0, 32686151.0, 15423212.0, 238922.0, 14316.0, 1629526.0, 9715619.0, 462.0, null, null, 1304100.0, 63152522.0, null, 28776704.0, 31252941.0, 17915459.0, 285813.0, 1314.0, 1783715.0, 12287842.0, 12461.0, null, null, 1297301.0, 58233010.0, null, 34279345.0, 28811430.0, 17767623.0, 281259.0, null, 1697039.0, 13741188.0, 16410.0, null, null, 1129255.0, 72168361.0, null, 37256528.0, 32681087.0, 21280571.0, 211509.0, null, 810121.0, 15107232.0, 11595.0, null, null, 1249419.0, 72865343.0, null, 39268208.0, 26912713.0, 16847775.0, 206555.0, null, 886362.0, 11513196.0, 19154.0, null, null, 1241593.0, 70026142.0, null, 36628316.0, 21903745.0, 14636544.0, 209607.0, null, 981246.0, 12384130.0, 15254.0, null, null, 1120547.0], "yaxis": "y"}, {"alignmentgroup": "True", "hoverlabel": {"namelength": 0}, "hovertemplate": "type2=\uc1fc\ud551<br>date=%{x}<br>value=%{y}", "legendgroup": "\uc1fc\ud551", "marker": {"color": "#00cc96"}, "name": "\uc1fc\ud551", "offsetgroup": "\uc1fc\ud551", "orientation": "v", "showlegend": true, "textposition": "auto", "type": "bar", "x": ["2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00"], "xaxis": "x", "y": [463578266.0, null, null, null, null, null, null, null, null, null, null, null, null, 533608908.0, null, null, null, null, null, null, null, null, null, null, null, null, 530217058.0, null, null, null, null, null, null, null, null, null, null, null, null, 527594295.0, null, null, null, null, null, null, null, null, null, null, null, null, 491419001.0, null, null, null, null, null, null, null, null, null, null, null, null, 350207524.0, null, null, null, null, null, null, null, null, null, null, null, null, 510425144.0, null, null, null, null, null, null, null, null, null, null, null, null, 492730866.0, null, null, null, null, null, null, null, null, null, null, null, null, 513200259.0, null, null, null, null, null, null, null, null, null, null, null, null, 521035697.0, null, null, null, null, null, null, null, null, null, null, null, null, 515555120.0, null, null, null, null, null, null, null, 343064.0, null, null, null, null, 415507316.0, null, null, null, null, null, null, null, 2110681.0, null, null, null, null, 489837805.0, null, null, null, null, null, null, null, null, null, null, null, null], "yaxis": "y"}, {"alignmentgroup": "True", "hoverlabel": {"namelength": 0}, "hovertemplate": "type2=\uc81c\ud734<br>date=%{x}<br>value=%{y}", "legendgroup": "\uc81c\ud734", "marker": {"color": "#ab63fa"}, "name": "\uc81c\ud734", "offsetgroup": "\uc81c\ud734", "orientation": "v", "showlegend": true, "textposition": "auto", "type": "bar", "x": ["2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00"], "xaxis": "x", "y": [null, 856796536.0, null, null, null, null, 278640.0, 1917000.0, 4655666.0, null, 550972.0, 916342.0, null, null, 1000944050.0, null, null, null, null, 294118.0, 1020000.0, 8632268.0, null, 613558.0, 806932.0, null, null, 994914532.0, null, null, null, null, 241920.0, 1084700.0, 6479487.0, null, 529366.0, 1178227.0, null, null, 963579980.0, null, null, null, null, 343882.0, 585000.0, 9356724.0, null, 662573.0, 683276.0, null, null, 998566032.0, null, null, null, null, 515550.0, 595000.0, 7422994.0, null, 713769.0, 615603.0, null, null, 811605339.0, null, null, null, null, 201260.0, 535000.0, 7856456.0, null, 444689.0, 211439.0, null, null, 944315126.0, null, null, null, null, 69340.0, 550000.0, 7980340.0, null, 361427.0, 230145.0, null, null, 929758756.0, null, null, null, null, 302000.0, 615000.0, 10575351.0, null, 517866.0, 62735.0, null, null, 899711673.0, null, null, null, null, null, 661000.0, 18547311.0, null, 406047.0, null, null, null, 920724188.0, null, null, null, null, null, 655000.0, 18428902.0, null, 524339.0, null, null, null, 1030568357.0, null, null, null, null, null, 244000.0, 17406323.0, null, 396273.0, null, null, 2800000.0, 902176565.0, null, null, null, null, null, 223000.0, 14378000.0, null, 299168.0, null, null, 2800000.0, 815181358.0, null, null, null, null, null, 202000.0, 16127984.0, null, 263979.0, null, null], "yaxis": "y"}, {"alignmentgroup": "True", "hoverlabel": {"namelength": 0}, "hovertemplate": "type2=\ucd1d\ub9e4\ucd9c<br>date=%{x}<br>value=%{y}", "legendgroup": "\ucd1d\ub9e4\ucd9c", "marker": {"color": "#FFA15A"}, "name": "\ucd1d\ub9e4\ucd9c", "offsetgroup": "\ucd1d\ub9e4\ucd9c", "orientation": "v", "showlegend": true, "textposition": "auto", "type": "bar", "x": ["2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00"], "xaxis": "x", "y": [877461064.0, 856796536.0, 44982900.0, 16682773.0, 10295417.0, 740849.0, 639306.0, 3690949.0, 7817711.0, null, 550972.0, 916342.0, 1424793.0, 966471170.0, 1000944050.0, 48998390.0, 17609344.0, 10215018.0, 327208.0, 646825.0, 2801740.0, 12707900.0, null, 613558.0, 806932.0, 1411672.0, 987656412.0, 994914532.0, 48433595.0, 17451406.0, 11598219.0, 1409870.0, 648769.0, 3208901.0, 10416422.0, null, 529366.0, 1178227.0, 1471511.0, 1018386612.0, 963579980.0, 46520628.0, 15781734.0, 11238319.0, 384706.0, 697865.0, 3140539.0, 13745980.0, null, 662573.0, 683276.0, 1347988.0, 1007288671.0, 998566032.0, 45446534.0, 15355218.0, 13983051.0, 392592.0, 800119.0, 3332993.0, 17816885.0, null, 713769.0, 615603.0, 1323164.0, 760125581.0, 811605339.0, 26813000.0, 16963340.0, 12539977.0, 616699.0, 457225.0, 2711914.0, 16969448.0, null, 444689.0, 211439.0, 1048305.0, 956359250.0, 944315126.0, 33289128.0, 21079358.0, 16421134.0, 210151.0, 292693.0, 2875503.0, 18106970.0, null, 361427.0, 230145.0, 1178304.0, 937899268.0, 929758756.0, 35540465.0, 32686151.0, 15423212.0, 238922.0, 316316.0, 2394526.0, 20290970.0, 462.0, 517866.0, 62735.0, 1304100.0, 946661781.0, 899711673.0, 28776704.0, 31252941.0, 17915459.0, 285813.0, 1314.0, 2594715.0, 30835153.0, 12461.0, 406047.0, null, 1297301.0, 958420857.0, 920724188.0, 34279345.0, 33811430.0, 17767623.0, 281259.0, null, 2502039.0, 32170090.0, 16410.0, 524339.0, null, 1129255.0, 994580531.0, 1030568357.0, 37256528.0, 33181087.0, 21280571.0, 211509.0, null, 1204121.0, 32856619.0, 11595.0, 396273.0, null, 1249419.0, 857620509.0, 902176565.0, 39268208.0, 26912713.0, 16847775.0, 206555.0, null, 1259362.0, 28001877.0, 19154.0, 299168.0, null, 1241593.0, 893895397.0, 815181358.0, 36628316.0, 21903745.0, 14636544.0, 209607.0, null, 1333246.0, 28512114.0, 15254.0, 263979.0, null, 1120547.0], "yaxis": "y"}],
                        {"barmode": "relative", "legend": {"title": {"text": "type2"}, "tracegroupgap": 0}, "template": {"data": {"bar": [{"error_x": {"color": "#2a3f5f"}, "error_y": {"color": "#2a3f5f"}, "marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "bar"}], "barpolar": [{"marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "barpolar"}], "carpet": [{"aaxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "baxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "type": "carpet"}], "choropleth": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "choropleth"}], "contour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "contour"}], "contourcarpet": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "contourcarpet"}], "heatmap": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmap"}], "heatmapgl": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmapgl"}], "histogram": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "histogram"}], "histogram2d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2d"}], "histogram2dcontour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2dcontour"}], "mesh3d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "mesh3d"}], "parcoords": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "parcoords"}], "pie": [{"automargin": true, "type": "pie"}], "scatter": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter"}], "scatter3d": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter3d"}], "scattercarpet": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattercarpet"}], "scattergeo": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergeo"}], "scattergl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergl"}], "scattermapbox": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattermapbox"}], "scatterpolar": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolar"}], "scatterpolargl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolargl"}], "scatterternary": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterternary"}], "surface": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "surface"}], "table": [{"cells": {"fill": {"color": "#EBF0F8"}, "line": {"color": "white"}}, "header": {"fill": {"color": "#C8D4E3"}, "line": {"color": "white"}}, "type": "table"}]}, "layout": {"annotationdefaults": {"arrowcolor": "#2a3f5f", "arrowhead": 0, "arrowwidth": 1}, "coloraxis": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "colorscale": {"diverging": [[0, "#8e0152"], [0.1, "#c51b7d"], [0.2, "#de77ae"], [0.3, "#f1b6da"], [0.4, "#fde0ef"], [0.5, "#f7f7f7"], [0.6, "#e6f5d0"], [0.7, "#b8e186"], [0.8, "#7fbc41"], [0.9, "#4d9221"], [1, "#276419"]], "sequential": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "sequentialminus": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]]}, "colorway": ["#636efa", "#EF553B", "#00cc96", "#ab63fa", "#FFA15A", "#19d3f3", "#FF6692", "#B6E880", "#FF97FF", "#FECB52"], "font": {"color": "#2a3f5f"}, "geo": {"bgcolor": "white", "lakecolor": "white", "landcolor": "#E5ECF6", "showlakes": true, "showland": true, "subunitcolor": "white"}, "hoverlabel": {"align": "left"}, "hovermode": "closest", "mapbox": {"style": "light"}, "paper_bgcolor": "white", "plot_bgcolor": "#E5ECF6", "polar": {"angularaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "radialaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "scene": {"xaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "yaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "zaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}}, "shapedefaults": {"line": {"color": "#2a3f5f"}}, "ternary": {"aaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "baxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "caxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "title": {"x": 0.05}, "xaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}, "yaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}}}, "title": {"text": "\uad11\uace0 \uc885\ub958\ubcc4 \ub9e4\ucd9c"}, "xaxis": {"anchor": "y", "domain": [0.0, 1.0], "title": {"text": "date"}}, "yaxis": {"anchor": "x", "domain": [0.0, 1.0], "title": {"text": "value"}}},
                        {"responsive": true}
                    ).then(function(){
                            
var gd = document.getElementById('426a6e4c-55ea-49d3-ba84-731aa7eb9f00');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })
                };
                });
            </script>
        </div>


#### 서비스별 광고구분없이 매출 groupby 한 value값 데이터프레임으로 만들기


```python
# 서비스별 매출 plot
import plotly.graph_objects as go

fig=go.Figure()
fig.add_trace(go.Scatter(x=list(data_adtype_sales.query('service=="프런트"')['date']), y=list(data_adtype_sales.query('service=="프런트"')['value']),
                         mode='lines+markers',
                        name='프런트'))   # X,Y값은 list형태로 들어가야 함.
fig.add_trace(go.Scatter(x=list(data_adtype_sales.query('service=="검색"')['date']), y=list(data_adtype_sales.query('service=="검색"')['value']),
                         mode='lines+markers',
                        name='검색')) 
fig.add_trace(go.Scatter(x=list(data_adtype_sales.query('service=="기사박스"')['date']), y=list(data_adtype_sales.query('service=="기사박스"')['value']),
                         mode='lines+markers',
                        name='기사박스')) 
fig.add_trace(go.Scatter(x=list(data_adtype_sales.query('service=="뉴스"')['date']), y=list(data_adtype_sales.query('service=="뉴스"')['value']),
                         mode='lines+markers',
                        name='뉴스')) 
fig.add_trace(go.Scatter(x=list(data_adtype_sales.query('service=="허브"')['date']), y=list(data_adtype_sales.query('service=="허브"')['value']),
                         mode='lines+markers',
                        name='허브')) 

```


<div>
        
        
            <div id="1554ba63-cb58-4ff3-acf7-20afbf1945c3" class="plotly-graph-div" style="height:525px; width:100%;"></div>
            <script type="text/javascript">
                require(["plotly"], function(Plotly) {
                    window.PLOTLYENV=window.PLOTLYENV || {};
                    
                if (document.getElementById("1554ba63-cb58-4ff3-acf7-20afbf1945c3")) {
                    Plotly.newPlot(
                        '1554ba63-cb58-4ff3-acf7-20afbf1945c3',
                        [{"mode": "lines+markers", "name": "\ud504\ub7f0\ud2b8", "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00"], "y": [354009020.0, 59873778.0, 463578266.0, null, 877461064.0, 362897480.0, 69964782.0, 533608908.0, null, 966471170.0, 378614550.0, 78824804.0, 530217058.0, null, 987656412.0, 415522920.0, 75269397.0, 527594295.0, null, 1018386612.0, 440863670.0, 75006000.0, 491419001.0, null, 1007288671.0, 348846100.0, 61071957.0, 350207524.0, null, 760125581.0, 386217860.0, 59716246.0, 510425144.0, null, 956359250.0, 381829700.0, 63338702.0, 492730866.0, null, 937899268.0, 370309000.0, 63152522.0, 513200259.0, null, 946661781.0, 379152150.0, 58233010.0, 521035697.0, null, 958420857.0, 406857050.0, 72168361.0, 515555120.0, null, 994580531.0, 366447850.0, 72865343.0, 415507316.0, 2800000.0, 857620509.0, 331231450.0, 70026142.0, 489837805.0, 2800000.0, 893895397.0]}, {"mode": "lines+markers", "name": "\uac80\uc0c9", "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00"], "y": [null, null, null, 856796536.0, 856796536.0, null, null, null, 1000944050.0, 1000944050.0, null, null, null, 994914532.0, 994914532.0, null, null, null, 963579980.0, 963579980.0, null, null, null, 998566032.0, 998566032.0, null, null, null, 811605339.0, 811605339.0, null, null, null, 944315126.0, 944315126.0, null, null, null, 929758756.0, 929758756.0, null, null, null, 899711673.0, 899711673.0, null, null, null, 920724188.0, 920724188.0, null, null, null, 1030568357.0, 1030568357.0, null, null, null, 902176565.0, 902176565.0, null, null, null, 815181358.0, 815181358.0]}, {"mode": "lines+markers", "name": "\uae30\uc0ac\ubc15\uc2a4", "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00"], "y": [null, 44982900.0, null, null, 44982900.0, null, 48998390.0, null, null, 48998390.0, null, 48433595.0, null, null, 48433595.0, null, 46520628.0, null, null, 46520628.0, null, 45446534.0, null, null, 45446534.0, null, 26813000.0, null, null, 26813000.0, null, 33289128.0, null, null, 33289128.0, null, 35540465.0, null, null, 35540465.0, null, 28776704.0, null, null, 28776704.0, null, 34279345.0, null, null, 34279345.0, null, 37256528.0, null, null, 37256528.0, null, 39268208.0, null, null, 39268208.0, null, 36628316.0, null, null, 36628316.0]}, {"mode": "lines+markers", "name": "\ub274\uc2a4", "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00"], "y": [500000.0, 16182773.0, null, null, 16682773.0, null, 17609344.0, null, null, 17609344.0, null, 17451406.0, null, null, 17451406.0, null, 15781734.0, null, null, 15781734.0, null, 15355218.0, null, null, 15355218.0, null, 16963340.0, null, null, 16963340.0, null, 21079358.0, null, null, 21079358.0, null, 32686151.0, null, null, 32686151.0, null, 31252941.0, null, null, 31252941.0, 5000000.0, 28811430.0, null, null, 33811430.0, 500000.0, 32681087.0, null, null, 33181087.0, null, 26912713.0, null, null, 26912713.0, null, 21903745.0, null, null, 21903745.0]}, {"mode": "lines+markers", "name": "\ud5c8\ube0c", "type": "scatter", "x": ["2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-09-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-10-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-11-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2018-12-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-01-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-02-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-03-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-04-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-05-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-06-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-07-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-08-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00", "2019-09-01T00:00:00"], "y": [null, 10295417.0, null, null, 10295417.0, null, 10215018.0, null, null, 10215018.0, null, 11598219.0, null, null, 11598219.0, null, 11238319.0, null, null, 11238319.0, null, 13983051.0, null, null, 13983051.0, null, 12539977.0, null, null, 12539977.0, null, 16421134.0, null, null, 16421134.0, null, 15423212.0, null, null, 15423212.0, null, 17915459.0, null, null, 17915459.0, null, 17767623.0, null, null, 17767623.0, null, 21280571.0, null, null, 21280571.0, null, 16847775.0, null, null, 16847775.0, null, 14636544.0, null, null, 14636544.0]}],
                        {"template": {"data": {"bar": [{"error_x": {"color": "#2a3f5f"}, "error_y": {"color": "#2a3f5f"}, "marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "bar"}], "barpolar": [{"marker": {"line": {"color": "#E5ECF6", "width": 0.5}}, "type": "barpolar"}], "carpet": [{"aaxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "baxis": {"endlinecolor": "#2a3f5f", "gridcolor": "white", "linecolor": "white", "minorgridcolor": "white", "startlinecolor": "#2a3f5f"}, "type": "carpet"}], "choropleth": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "choropleth"}], "contour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "contour"}], "contourcarpet": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "contourcarpet"}], "heatmap": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmap"}], "heatmapgl": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "heatmapgl"}], "histogram": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "histogram"}], "histogram2d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2d"}], "histogram2dcontour": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "histogram2dcontour"}], "mesh3d": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "type": "mesh3d"}], "parcoords": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "parcoords"}], "pie": [{"automargin": true, "type": "pie"}], "scatter": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter"}], "scatter3d": [{"line": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatter3d"}], "scattercarpet": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattercarpet"}], "scattergeo": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergeo"}], "scattergl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattergl"}], "scattermapbox": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scattermapbox"}], "scatterpolar": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolar"}], "scatterpolargl": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterpolargl"}], "scatterternary": [{"marker": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "type": "scatterternary"}], "surface": [{"colorbar": {"outlinewidth": 0, "ticks": ""}, "colorscale": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "type": "surface"}], "table": [{"cells": {"fill": {"color": "#EBF0F8"}, "line": {"color": "white"}}, "header": {"fill": {"color": "#C8D4E3"}, "line": {"color": "white"}}, "type": "table"}]}, "layout": {"annotationdefaults": {"arrowcolor": "#2a3f5f", "arrowhead": 0, "arrowwidth": 1}, "coloraxis": {"colorbar": {"outlinewidth": 0, "ticks": ""}}, "colorscale": {"diverging": [[0, "#8e0152"], [0.1, "#c51b7d"], [0.2, "#de77ae"], [0.3, "#f1b6da"], [0.4, "#fde0ef"], [0.5, "#f7f7f7"], [0.6, "#e6f5d0"], [0.7, "#b8e186"], [0.8, "#7fbc41"], [0.9, "#4d9221"], [1, "#276419"]], "sequential": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]], "sequentialminus": [[0.0, "#0d0887"], [0.1111111111111111, "#46039f"], [0.2222222222222222, "#7201a8"], [0.3333333333333333, "#9c179e"], [0.4444444444444444, "#bd3786"], [0.5555555555555556, "#d8576b"], [0.6666666666666666, "#ed7953"], [0.7777777777777778, "#fb9f3a"], [0.8888888888888888, "#fdca26"], [1.0, "#f0f921"]]}, "colorway": ["#636efa", "#EF553B", "#00cc96", "#ab63fa", "#FFA15A", "#19d3f3", "#FF6692", "#B6E880", "#FF97FF", "#FECB52"], "font": {"color": "#2a3f5f"}, "geo": {"bgcolor": "white", "lakecolor": "white", "landcolor": "#E5ECF6", "showlakes": true, "showland": true, "subunitcolor": "white"}, "hoverlabel": {"align": "left"}, "hovermode": "closest", "mapbox": {"style": "light"}, "paper_bgcolor": "white", "plot_bgcolor": "#E5ECF6", "polar": {"angularaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "radialaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "scene": {"xaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "yaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}, "zaxis": {"backgroundcolor": "#E5ECF6", "gridcolor": "white", "gridwidth": 2, "linecolor": "white", "showbackground": true, "ticks": "", "zerolinecolor": "white"}}, "shapedefaults": {"line": {"color": "#2a3f5f"}}, "ternary": {"aaxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "baxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}, "bgcolor": "#E5ECF6", "caxis": {"gridcolor": "white", "linecolor": "white", "ticks": ""}}, "title": {"x": 0.05}, "xaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}, "yaxis": {"automargin": true, "gridcolor": "white", "linecolor": "white", "ticks": "", "title": {"standoff": 15}, "zerolinecolor": "white", "zerolinewidth": 2}}}},
                        {"responsive": true}
                    ).then(function(){
                            
var gd = document.getElementById('1554ba63-cb58-4ff3-acf7-20afbf1945c3');
var x = new MutationObserver(function (mutations, observer) {{
        var display = window.getComputedStyle(gd).display;
        if (!display || display === 'none') {{
            console.log([gd, 'removed!']);
            Plotly.purge(gd);
            observer.disconnect();
        }}
}});

// Listen for the removal of the full notebook cells
var notebookContainer = gd.closest('#notebook-container');
if (notebookContainer) {{
    x.observe(notebookContainer, {childList: true});
}}

// Listen for the clearing of the current output cell
var outputEl = gd.closest('.output');
if (outputEl) {{
    x.observe(outputEl, {childList: true});
}}

                        })
                };
                });
            </script>
        </div>



```python

```


```python

```


```python

```
