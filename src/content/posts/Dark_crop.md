---
title: Dark Crop
published: 2025-02-19
description: "How to use this blog template."
image: "../../assets/Dark_crop/DarkCorp.png"
tags: ["Cyber"]
category: Hack the box
draft: false
---

# Dark Crop

**Ping**

I verified whether I could communicate or if the IP address was up. 

![image.png](../../assets/Dark_crop/image.png)

The IP address is up. Now I can communicate with the IP address.

**Nmap**

Then used Nmap to 

![image.png](../../assets/Dark_crop/image%201.png)

![image.png](../../assets/Dark_crop/image%202.png)

- **Version detection scan**

![image.png](../../assets/Dark_crop/image%203.png)

**Result**

There are two open ports:

- 22 ssh and,
- 80 hhtp

### **Web enumeration**

I used wappalyzer extension to find the framework the website used.

![image.png](../../assets/Dark_crop/image%204.png)

**Whatweb**

Upon researching I found the tool called *whatweb* that also detects the framework used same like the wappplyzer.

[whatweb | Kali Linux Tools](https://www.kali.org/tools/whatweb/)

![image.png](../../assets/Dark_crop/image%205.png)

![image.png](../../assets/Dark_crop/image%206.png)

**Result**

I found that the website used:

- The web server used is nginx version 1.22.1.
- Used Bootstrap for frond-end

Then I checked the vulnerability of ngnix 1.22.1 in exploit database, but i found nothing.

![image.png](../../assets/Dark_crop/image%207.png)

Then I searched the IP address and I was navigated to the drip.htb and this error appeared

![image.png](../../assets/Dark_crop/image%208.png)

DNS resolution is not setup in **etc/hosts** file. Now let's resolve the DNS resolution using vim(text editor).

![image.png](../../assets/Dark_crop/image%209.png)

![image.png](../../assets/Dark_crop/image%2010.png)

After solving the DNS resolution I was directed to the /index directory and got this page

![image.png](../../assets/Dark_crop/image%2011.png)

I navigated to the sign-in page and then found this

![image.png](../../assets/Dark_crop/image%2012.png)

I was then navigated to the mail.drip.htb

Same like the drip.htb error I resolve the DNS by editing the /etc/hosts

![image.png](../../assets/Dark_crop/image%2013.png)

![image.png](../../assets/Dark_crop/image%2014.png)

Then I was able to find the page and I found this login page.

![image.png](../../assets/Dark_crop/image%2015.png)

I then used ffuf to brute force the directory 

![image.png](../../assets/Dark_crop/image%2016.png)

**Result** 

- Found mail.

This mail subdomain was already found when I navigated to the sign-in page.

![image.png](../../assets/Dark_crop/image%2017.png)

**Result** 

- Found contact
- index.html
- register

I have registered as a user to find out what the website is about

![image.png](../../assets/Dark_crop/image%2018.png)

after signing in I found this page

![image.png](../../assets/Dark_crop/image%2019.png)

- The page is mainly about the mails

Then I was stuck here then I backtracked it and I again gathered information.

**Enumeration**

**WPScan**

I browsed the tools that are used to scan the subdomains and I found this Wpscan.

- WPScan is used for searching for vulnerabilities, such as weak passwords and outdated plugins.

![image.png](../../assets/Dark_crop/image%2020.png)

I was not able to get the result because the website is not running on WordPress.

- I understood that the WPScan is used for the website using WordPress.

**ferric oxide**

 I then found a tool called ferric oxide 

![image.png](../../assets/Dark_crop/image%2021.png)

**Result**

- Found only two 200 status code. Both are the same. It is the landing page.

Nikto

- Nikto scans for insecure files and programs.

![image.png](../../assets/Dark_crop/image%2022.png)

**Result**

I have found that the X-Content-Type-Options header is not set.

- This could allow browsers to interpret files in unintended ways, leading to security issues like MIME-type sniffing attacks.
- Found multiple index files: /index.php, /index.asp, /index.html, /default.aspx, etc.