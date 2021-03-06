# CTF-RSA
## Tools
[factordb.com](http://factordb.com/index.php)

[RSA-winer-Attack](https://github.com/pablocelayes/rsa-wiener-attack)

and `Python`,  `openssl`

Install `libnum`, `gmpy2`, `Crypto` first

## 一些解題方法
### 1. 最基本(decrypt it!)
```python
phi_n = (p - 1) * (q - 1)
d = libnum.modular.invmod(e, phi_n)
text = libnum.n2s(pow(ciphertext, d, n)) 
print(text)  
```
### 2. 求d的值 
```python
phi_n= (p - 1) * (q - 1)
d = gmpy2.invert(e, phi_n)
print(d)
```
### 3. 已知n, e 解密
use [factordb.com](http://factordb.com/index.php) to factor

=>p,q known, phi(n)=(p-1)(q-1)

```python
phi_n= (p - 1) * (q - 1)
d = gmpy2.invert(e, phi_n)
text = libnum.n2s(pow(ciphertext, d, n)) 
print(text)
```

### 4. 已知p, q, e(解密)
n p*q

=>n known, decrypt it:
```python
n = p*q
phi_n= (p - 1) * (q - 1)
d = gmpy2.invert(e, phi_n)
text = libnum.n2s(pow(ciphertext, d, n)) 
print(text)
```
### 5. 公因數分解兩個n
```python
n1 = n1
n2 = n2
p = gmpy2.gcd(n1, n2)
q1 = n1 / p
q2 = n2 / p
print('p:', p)
print('q1:', q1)
print('q2:', q2)
```
### 6. e=3(e過小)
```python
for k in xrange(200000000):    
    if gmpy2.iroot(ciphertext + n*k, 3)[1]==1:    
        text = gmpy2.iroot(ciphertext + n*k, 3)[0]    
        print('k:', k)    
        print(libnum.n2s(text)) 
```
