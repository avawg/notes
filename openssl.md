```
生成密钥
openssl genrsa -out tls.key 2048

查看密钥 openssl rsa -text -in tls.key -noout

提取公钥 openssl rsa -in tls.key -pubout -out tls_pub.key

创建CSR: openssl req -new -key tls.key -out tls.csr

openssl req -text -in tls.csr -noout -verify

查看私钥中公钥sha值 openssl req -pubkey -in tls.key | openssl sha256

openssl pkey -pubout -in tls.key | openssl sha256  


格式转换 openssl rsa -inform DER -in tls.der -outform PEM -out tls2.key
```