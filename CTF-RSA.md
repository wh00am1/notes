# CTF-RSA
## Tools
[factordb.com](http://factordb.com/index.php)

[RSA-winer-Attack](https://github.com/pablocelayes/rsa-wiener-attack)

and `Python`,  `openssl`

Install `libnum`, `gmpy2`, `Crypto` first

## Solution to some types of challenge
### 1. Basic(decrypt it!)
```python
phi = (p - 1) * (q - 1)
d = libnum.modular.invmod(e, phi)
text = libnum.n2s(pow(ciphertext, d, n)) 
print(text)  
```
### 2. d Unknown
```python
phi_n= (p - 1) * (q - 1)
d = gmpy2.invert(e, phi_n)
print(d)
```
### 3. cipher, n, e known(decrypt)
use [factordb.com](http://factordb.com/index.php) to factor

=>p,q known, phi(n)=(p-1)(q-1)

```python
phi_n= (p - 1) * (q - 1)
d = gmpy2.invert(e, phi_n)
text = libnum.n2s(pow(ciphertext, d, n)) 
print(text)
```

### 4. p, q, e, cipher known(decrypt)
n p*q

=>n known, decrypt it:
```python
n = p*q
phi_n= (p - 1) * (q - 1)
d = gmpy2.invert(e, phi_n)
text = libnum.n2s(pow(ciphertext, d, n)) 
print(text)
```
### 5. Common divisor
```python
n1 = n1
n2 = n2
p = gmpy2.gcd(n1, n2)
q1 = n1 / p
q2 = n2 / p
print('p:\n', p)
print('q1:\n', q1)
print('q2:\n', q2)
```
### 6. e=3
```python
for k in xrange(200000000):    
    if gmpy2.iroot(c+n*k,3)[1]==1:    
        res=gmpy2.iroot(c+n*k,3)[0]    
        print('k:\n', k)    
        print(libnum.n2s(text)) 
```
