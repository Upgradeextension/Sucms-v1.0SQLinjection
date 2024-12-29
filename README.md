# Sucms-v1.0SQLinjection
## Download link: https://down.chinaz.com/api/index/download?id=37818&type=code.
## Vulnerability description
Sucheng Film and Television Management System (sucms). There is a SQL injection vulnerability in the background management of Sucheng Film and Television Management System. Vulnerability URL: http://127.0.0.1/admin/admin_members.php?ac=search, which can cause SQL injection vulnerability and can be temporarily solved by filtering parameters.
## Vulnerability analysis
In /admin/admin_members.php, multiple query statements are not filtered for SQL injection, and there is a SQL injection vulnerability in the uid parameter.
![image](https://github.com/user-attachments/assets/8380a9b7-7271-40a7-b533-9e345ccc4919)
## Affected versions: Sucms v1.0 web application is affected by this vulnerability.
## Vulnerability Verification Process
```
POST /admin/admin_members.php?ac=search HTTP/1.1
Host: 127.0.0.1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:70.0) Gecko/20100101 Firefox/70.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/x-www-form-urlencoded
Content-Length: 39
Origin: http://127.0.0.1
Connection: close
Referer: http://127.0.0.1/admin/admin_members.php
Cookie: PHPSESSID=8k8r2hfra80o3opt0beua9mga5; zh_choose=n; _currentWebUrl_=%2Findex.php%2Findex-category-id-81.html; _currentAdminUrl_=%2Findex.php%2Fadmin-sys-managers.html; user=21232f297a57a5a743894a0e4a801fc3; DedeUserID=1; DedeUserID__ckMd5=2bc70c6d99eeb958; DedeLoginTime=1625041565; DedeLoginTime__ckMd5=7cac447604e50983; YUNYECMSADM_admusername=admin2; YUNYECMSADM_admuserid=4; YUNYECMSADM_admroleid=1; YUNYECMSADM_admloginrnd=gikoruvX045%23_%7B%60%3D.%3B%3A%7C; YUNYECMSADM_admlogintruetime=1625102419; YUNYECMSADM_admlogintime=1625102589; YUNYECMSADM_admloginlicense=yunyecmslicense; YUNYECMSADM_loginyunyecmsckpass=3ab05cc7fa6027423125becc4f1a9f54; YUNYECMSADM_loginyunyecmsfilernd=bdfhijnqstuxzCENOQRSTVXZ017
Upgrade-Insecure-Requests: 1

uname=1&uid=1&Submit=%E6%90%9C%E7%B4%A2
```
![image](https://github.com/user-attachments/assets/07b5d7fc-0744-4b5d-b35a-e859a6838b84)

## Solutions
Use Prepared Statements (Parameterized Queries):
Always use prepared statements with parameterized queries to separate SQL code from data inputs, ensuring user inputs are treated strictly as data.

Input Validation and Sanitization:
Validate and sanitize all user inputs by enforcing strict rules (e.g., regex or type checking) to ensure they conform to expected formats and remove harmful characters.

Implement Least Privilege Principle:
Configure database accounts with minimal permissions to reduce the impact of a potential SQL injection attack, ensuring no excessive privileges are granted.
