#new 
We can use [[cURL]] to retrieve server header information from the command line. [[cURL]] is another essential addition to our penetration testing toolkit, and familiarity with its many options is encouraged.

```shell-session
Iskandeur@htb[/htb]$ curl -IL https://www.inlanefreight.com

HTTP/1.1 200 OK
Date: Fri, 18 Dec 2020 22:24:05 GMT
Server: Apache/2.4.29 (Ubuntu)
Link: <https://www.inlanefreight.com/index.php/wp-json/>; rel="https://api.w.org/"
Link: <https://www.inlanefreight.com/>; rel=shortlink
Content-Type: text/html; charset=UTF-8
```
