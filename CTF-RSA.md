# CTF-RSA
## Tools
[factordb.com](http://factordb.com/index.php)

[RSA-winer-Attack](https://github.com/pablocelayes/rsa-wiener-attack)

and `Python`,  `openssl`

Install `libnum`, `gmpy2` first

## Solution to some types of challenge
### 1.Basic(decrypt it!)
```python
phi = (p - 1) * (q - 1)
d = libnum.modular.invmod(e, phi)
text = libnum.n2s(pow(ciphertext, d, n)) 
print(text)  
```
### 2.d Unknown
```python
p =gmpy2.mpz(p)
q =gmpy2.mpz(q)
e =gmpy2.mpz(e)
phi_n= (p - 1) * (q - 1)
d = gmpy2.invert(e, phi_n)
print(d)
```
### 3.cipher, n, e known
use [factordb.com](http://factordb.com/index.php) to factor

=>p,q known, phi(n)=(p-1)(q-1)

```python
p =gmpy2.mpz(p)
q =gmpy2.mpz(q)
e =gmpy2.mpz(e)
phi_n= (p - 1) * (q - 1)
d = gmpy2.invert(e, phi_n)
text = libnum.n2s(pow(ciphertext, d, n)) 
print(text)
