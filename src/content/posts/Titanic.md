---
title: Titanic
published: 2025-02-22
description: "How to use this blog template."
# image: "../../assets/images/my_photo.jpg"
tags: ["Cyber"]
category: Hack the box
draft: false
---

# Titanic

Titanic

**1. Initial Reconnaissance**

**Ping Test:**

- Firstly I performed a ping command to confirm whether the host is up.

![image.png](image.png)

**Nmap Scan:**

- I then conducted an Nmap scan to detect open ports, services, and OS version.

![image.png](image%201.png)

***Result*** 

- there are two ports open :
    - 22 ssh
    - 80 http

Since I got the http port up, I checked the IP address in the browser and got this error result.

![image.png](image%202.png)

Then I edited the */etc/hosts* file using Vim to resolve the domain **titanic.htb.** I then verified DNS resolution by reloading and accessing the site.

![image.png](image%203.png)

![image.png](image%204.png)

Then I was able to successfully reload the configuration and access the site.

![image.png](image%205.png)

1. **Website Analysis**

**Wappalyzer**

I used the wappalyzer extension to analyze the web technologies used on the site.

![image.png](image%206.png)

this is the summary of the site 

![image.png](image%207.png)

- the website used:
    - python (3.10.12) as a programming language
    - Flask (3.0.3) as a web server
    - Bootstrap (4.5.2) as UI framework

I searched for vulnerabilities in exploit db and got nothing

![image.png](image%208.png)

1. **Directory Brute forcing**

Then I ran ffuf to brute-force the directories.

![image.png](image%209.png)

After brute forcing, I found two subdomains:

- book
- server-status

I then navigated to the book domain and found this. I was not able to visit the site

![image.png](image%2010.png)

Then I checked the server-status domain and this time the site was forbidden.

![image.png](image%2011.png)

### 5. Advanced Scanning

- **Feroxbuster**

I used the Ferobuster tool to find the subdomains of the Titanic page

![image.png](image%2012.png)

![image.png](image%2013.png)

Found only two 202 status code. Let’s check both the site 
I then navigated to the [http://titanic.htb/static/styles.css](http://titanic.htb/static/styles.css) page that I found in the result.

But I didn’t find any interesting. It was just the CSS code. 

![image.png](image%2014.png)

**Nikto Scan:**

Used Nikto for vulnerability scanning.

![image.png](image%2015.png)

After doing the scan I got the one directory. Let’s check this one

Found [http://titanic.htb/static/assets/images/favicon.ico](http://titanic.htb/static/assets/images/favicon.ico).

![image.png](image%2016.png)

I was just the image of the Titanic image used.

Then I explored the booking system to understand its behavior.

![image.png](image%2017.png)

After submitting the booking button, I got the JSON file. Let’s check this file. 

![image.png](image%2018.png)

I just found the details from the JSON file.

![image.png](image%2019.png)

So, after that, I again used ffuf brute forcing to find the subdomains

![image.png](image%2020.png)

**Result**

- found *dev* domain

added ***dev.titanic.htb*** in /etc/hosts file 

```jsx
sudo vim /etc/hosts
```

![image.png](image%2021.png)

I got this page 

![image.png](image%2022.png)

I explored all the necessary navigation on the website and after navigating on the explore button I got the developer site.

Also, I used ffuf for brute forcing the dev domain to find the subdomains

![image.png](image%2023.png)

As a result, I got:

- administrator
- developer
- v2

after that to find the valid status code and the path I used feroxbuster tool.

![image.png](image%2024.png)

![image.png](image%2025.png)

found 43 valid 202 status code and checked each and every one. Then I found the flask-app directory.

Explored the development course 

![image.png](image%2026.png)

Inside the flask-app directory, I found this [app.py](http://app.py) code. this might be vulnerable.

![image.png](image%2027.png)

As I got the Python code, I fed the code to the AI and got ideas on how to exploit the machine that could be vulnerable. 

From the result I found that the ticket parameter is used to construct a file path, this allows an attacker to request arbitrary files outside the directory using path traversal.

- Request `/download?ticket=../../../../etc/passwd` in the header side might return the system's password file.

**Lack of authentication**

- anyone can book and download the ticket
- attackers can brute-force.
- attackers can guess the ticket filename to download other users’ tickets.

I used Burp Suite to intercept the network and followed each step. 

I then used the path traversal vulnerabilities upon downloading the ticket.

![image.png](image%2028.png)

This is the response I got.

![image.png](image%2029.png)

![image.png](image%2030.png)

from the above information:

- developer user was found
- another user called _laurel and there is no login shell
- user developer has a home directory(/home/developer) and a **bash shell**

I read [gitea documentation](https://docs.gitea.com/installation/install-with-docker) to find the location of any configuration files. 

Upon reading this documentation 

I found this useful information:

![image.png](image%2031.png)

From the information we got earlier, we know that there is a developer user and now we get that those endpoints can be used by the user having the advantage to download the files using the endpoint.  

![image.png](image%2032.png)

![image.png](image%2033.png)

![image.png](image%2034.png)

![image.png](image%2035.png)

after this, I found that the database has another file called gitea.db from the database path.

There might be vulnerabilities in this gitea.db file. So, I downloaded this file.

![image.png](image%2036.png)

After downloading the gitea.db file. I have extracted the hash from the gitea file to get the users.

![image.png](image%2037.png)

Used hashcat to crack the password of the gitea file.

![image.png](image%2038.png)

![image.png](image%2039.png)

After cracking the user hashes I got the password of the developer user. 

Now I will be able to get into the SSH port 22 with the user developer. Let’s try this

### **ssh login**

Used developer as a user.

![image.png](image%2040.png)

![image.png](image%2041.png)

- After listing the file I got the user.txt flag.

I then used the find command to find directories where we have the write access. I found the identify_images.sh file with write access.

![image.png](image%2042.png)

Found that the scripts folder uses ImageMagick. I checked the version of this.

![image.png](image%2043.png)

Found that the version is 7.1.1-35

After searching the vulnerabilities of ImageMagick version 7.1.1-35, I found the known vulnerability. 

[Arbitrary Code Execution in `AppImage` version `ImageMagick`](https://github.com/ImageMagick/ImageMagick/security/advisories/GHSA-8rxc-922v-phg8)

This allows running code by placing a malicious shared library in the working directory.

- we can exploit it by placing a fake library inside this file.

![image.png](image%2044.png)

This is the code that I found after reading the ImageMagick vulnerability.

After running this I got the root flag. 

![image.png](image%2045.png)

![image.png](image%2046.png)

![image.png](image%2047.png)