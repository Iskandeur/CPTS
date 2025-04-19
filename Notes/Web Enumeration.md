When performing [[Service Enumeration]], we will often run into [[Web Server|web servers]] running on [[Network Ports|ports]] 80 and 443. Web servers host [[Web Application|web applications]] (sometimes more than 1) which often provide a considerable attack surface and a very high-value target during a [[Penetration Testing Process|penetration test]]. Proper web enumeration is critical, especially when an organization is not exposing many services or those services are appropriately patched. It's a key part of [[Information Gathering]].

## Directory Enumeration

After discovering a web application, it is always worth checking to see if we can uncover any hidden files or directories on the webserver that are not intended for public access. We can use a tool such as `[[ffuf]]` or `[[GoBuster]]` to perform this directory enumeration. Sometimes we will find hidden functionality or pages/directories exposing sensitive data that can be leveraged to access the web application or even remote code execution on the web server itself.

## Web Enumeration Techniques

### Banner Grabbing / Web Server Headers

In the last section, we discussed [[Banner Grabbing]] for general purposes. Web server headers provide a good picture of what is hosted on a web server. They can reveal the specific application framework in use, the authentication options, and whether the server is missing essential security options or has been misconfigured.
We can use `[[cURL]]` to retrieve server header information from the command line. `[[cURL]]` is another essential addition to our penetration testing toolkit, and familiarity with its many options is encouraged.

```shell-session
Iskandeur@htb[/htb]$ curl -IL https://www.inlanefreight.com

HTTP/1.1 200 OK
Date: Fri, 18 Dec 2020 22:24:05 GMT
Server: Apache/2.4.29 (Ubuntu)
Link: <https://www.inlanefreight.com/index.php/wp-json/>; rel="https://api.w.org/"
Link: <https://www.inlanefreight.com/>; rel=shortlink
Content-Type: text/html; charset=UTF-8
```

Another handy tool is `[EyeWitness](https://github.com/FortyNorthSecurity/EyeWitness)`, which can be used to take screenshots of target web applications, fingerprint them, and identify possible default credentials.

### Whatweb

We can extract the version of web servers, supporting frameworks, and applications using the command-line tool [[whatweb]]. This information can help us pinpoint the technologies in use and begin to search for potential vulnerabilities.

### Certificates

[[SSL TLS certificates]] are another potentially valuable source of information if HTTPS is in use. Browsing to `https://10.10.10.121/` and viewing the certificate reveals the details below, including the email address and company name. These could potentially be used to conduct a phishing attack if this is within the scope of an assessment.

![Certificate details for Megabank Limited, including subject and issuer information with country, state, locality, organization, and email address.](https://academy.hackthebox.com/storage/modules/77/cert.png)

### Robots.txt

It is common for websites to contain a `[[robots.txt]]` file, whose purpose is to instruct search engine web crawlers such as Googlebot which resources can and cannot be accessed for indexing. The `[[robots.txt]]` file can provide valuable information such as the location of private files and admin pages.

### Source Code

It is also worth checking the source code for any web pages we come across. We can hit `[CTRL + U]` to bring up the source code window in a browser. This example reveals a developer comment containing credentials for a test account, which could be used to log in to the website.

![HTML snippet with test account credentials, meta tags, and admin login title.](https://academy.hackthebox.com/storage/modules/77/source.png)

