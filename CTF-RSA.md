# CTF-RSA
## Tools
[factordb.com](http://factordb.com/index.php)

[RSA-winer-Attack](https://github.com/pablocelayes/rsa-wiener-attack)

and `Python`,  `openssl`

openssl:

`openssl   rsautl -encrypt -in FLAG -inkey public.pem -pubin -out flag.enc`

## Solution to some types of challenge
### 1.Basic(decrypt it!)
```python
phi = (p - 1) * (q - 1)
d = libnum.modular.invmod(e, phi)
m = libnum.n2s(pow(c, d, n)) 
print(m)  
```
