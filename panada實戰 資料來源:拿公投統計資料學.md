### 資料預先處理
```
excel檔亂碼處理
另存到github上 開row
將網址複製:!wget https://raw.githubusercontent.com/MyDearGreatTeacher/AI_and_security_2020/master/referendum2.csv
```
### 使用py.read()讀取.csv
```
cat referendum2.csv
```
```
import pandas as pd
refm = pd.read_csv('referendum2.csv')
refm
```
### 驗證資料是否正確
#### 驗算 「同意票數+不同意票數==有效票數」、 
#### 驗算 「有效票數+無效票數==投票數」：
```
x=refm['同意票數']+refm['不同意票數']-refm['有效票數']
x.describe()

x=refm['有效票數']+refm['無效票數']-refm['投票數']
x.describe()

refm2 = refm[~ refm['鄉鎮市區'].isnull()]
refm2
```
### 計算 「贊成比例」
#### 並且把「鄉鎮市區」冠上縣市名稱。 
#### 只留下三個欄位「案件」、「鄉鎮市區」、「贊成比例」
```
refm3 = refm.dropna(subset=['鄉鎮市區'])
refm = refm3
refm['贊成比例'] = refm['同意票數']/refm['投票數']
refm['鄉鎮市區'] = refm['縣市'] + refm['鄉鎮市區']
refm2 = refm.drop(columns=['縣市', '同意票數', '不同意票數', '有效票數', '無效票數', '投票數', '投票權人數'])
refm3 = refm[['案件', '鄉鎮市區', '贊成比例']]
refm3

refm = refm3
x07 = refm[refm['案件']=='c07'][['鄉鎮市區','贊成比例']]
x08 = refm[refm['案件']=='c08'][['鄉鎮市區','贊成比例']]
tmp = pd.concat([x07.set_index('鄉鎮市區'), x08.set_index('鄉鎮市區')], axis=1, sort=True)
tmp.columns = ['c07', 'c08']
refm3
```
### 製圖
```
summary = refm[refm['案件']=='c07'][['鄉鎮市區','贊成比例']].set_index('鄉鎮市區')
cnames = refm['案件'].unique()
for c in cnames[1:] :
    tmp = refm[refm['案件']==c][['鄉鎮市區','贊成比例']]
    summary = pd.concat([summary, tmp.set_index('鄉鎮市區')], axis=1, sort=True)

summary.columns = cnames

drawing=summary.plot(kind='scatter', x='c07', y='c08')




import matplotlib.pyplot as plt
plt.savefig('ref-07-08.svg')
plt.show()

import plotly
import plotly.graph_objs as go
plotly.offline.plot([
    go.Scatter(
        mode='markers',
        x=summary['c07'],
        y=summary['c08'],
        text=summary.index
    )],
    filename='ref-07-08.html'
)

import math
N = 60
X=[(float(k)/N-0.5)*math.pi*2 for k in range(N+1)]
Y=[math.sin(x) for x in X]
plotly.offline.plot([go.Scatter(mode='lines+markers', x=X, y=Y)])
```

##### 資料來源
```
```

