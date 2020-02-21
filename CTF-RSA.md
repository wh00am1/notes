# CTF-RSA
## Tools
[factordb.com](http://factordb.com/index.php)

[RSA-winer-Attack](https://github.com/pablocelayes/rsa-wiener-attack)

and `Python`,  `openssl`

Install `libnum` first

## Solution to some types of challenge
### 1.Basic(decrypt it!)
```python
phi = (p - 1) * (q - 1)
d = libnum.modular.invmod(e, phi)
text = libnum.n2s(pow(ciphertext, d, n)) 
print(text)  
```
### 2.
