```
生成密钥 openssl genrsa -out tls.key 2048

查看密钥 openssl pkey -in tls.key -text -noout 

提取公钥 openssl pkey -in tls.key -pubout -out pub.key
查看私钥中公钥sha值  openssl pkey -in tls.key -pubout | openssl sha256  

生成自签名证书 openssl req -x509 -key ca.key -out ca.crt -days 365
openssl x509 -req -in server/tls.csr -CA ca/ca.crt -CAkey ca/ca.key -out server/tls.crt -days 365

创建CSR openssl req -new -key tls.key -out tls.csr
验证CSR openssl req -verify -in tls.csr -noout 
从CSR中获取公钥 openssl req -in tls.csr -pubkey -noout | openssl sha256

验证证书 openssl verify -CAfile ca/ca.crt server/tls.crt

格式转换 openssl rsa -inform DER -in tls.der -outform PEM -out tls.key
```