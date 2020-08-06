# Pwn

## Basic knowledge

### Memory Layout

程式時的記憶體mapping大致像是這樣:

![avatar](https://github.com/wh00am1/notes/blob/master/memoryLayoutC.jpg)

其中stack 為FILO型的資料結構，由高位址向低位址生長

heap則為從高位往低位生長的動態配置記憶體空間，以chunk為單位

### Protection Mechanisms

#### PIE
#### NX
#### RELRO
#### ASLR
#### Stack Canary

## stack-based Pwn 

### Basic concept

當使用者的輸入超過程式預期時，將在`stack`上產生溢位

攻擊者能夠控制`return address` 實現任意跳(control PC)

常見不安全函數有`gets()`, `scanf()`, 以及長度配置失誤的`read()`

### Advanced Exploitation

#### ROP

使用程式中的小片段(gadgets) 串聯，以實現所需功能

常見的攻擊手法有:

* ret2text

* ret2plt

* gothijack

* ret2libc

reference : [CTF-wiki](https://ctf-wiki.github.io/ctf-wiki/pwn/linux/stackoverflow/basic-rop-zh/)

## Heap-based pwn

當使用者輸入非法長度的資料時，能夠覆蓋超過當前chunk的資料

從而overwrite 一些資訊(例如`got`, 甚至`return address`)
