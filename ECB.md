# ECB加密法 & 為何不能用於重要資料的加密

## 原理
![avatar](https://github.com/wh00am1/notes/blob/master/Ecb_decryption.png)

將資料分成很多區塊 每段分開加密

## 實作問題

每段資料所使用的key相同，因此可以使用選擇明文

先加密過一次後，可以使用選擇的密文替換加密密文

假設:siteA使用ECB來確認付錢的資訊

利用ECB把原本的交易資料，可能是

`    amout:4000`

`    count:1`
   
做加密後:

`   amout:0x040004`

`   count:0x010001`

之類的

