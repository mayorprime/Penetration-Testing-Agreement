## Scan a Website and Investigate Vulnerability

In this part of the lab, you will conduct a vulnerability scan using the
**Zed Attack Proxy** (ZAP).

## What is OWASP ZAP:

OWASP ZAP (Zed Attack Proxy) is a popular open-source security testing
tool used for finding vulnerabilities in web applications. It is
maintained by the Open Web Application Security Project (OWASP) and is
widely used by penetration testers, security researchers, and developers
to identify security flaws early in the development lifecycle.

Features and uses of OWASP ZAP:

### 1. **Web Application Security Testing**

ZAP is designed to automatically scan and identify vulnerabilities in
web applications. It provides both manual and automated security testing
capabilities.

### 2. **Intercepting Proxy** 

ZAP works as a proxy server that sits between the user and the target
web application. It intercepts HTTP and HTTPS traffic, allowing you to
analyze and manipulate requests and responses. This feature is useful
for testing various security issues like:

- Cross-Site Scripting (XSS)
- SQL Injection
- Session Management flaws
- Security misconfiguration

### 3. **Active Scanning** 

ZAP has an active scanning feature that automatically checks for known
vulnerabilities in web applications, such as injection flaws, security
misconfiguration, and sensitive data exposure. Active scans are
generally more comprehensive and intrusive compared to passive scans.

### 4. **Passive Scanning** 

Passive scanning analyzes the HTTP/HTTPS traffic for security weaknesses
without actually altering the requests or responses. It doesn\'t
actively send malicious payloads but looks for vulnerabilities based on
patterns in the traffic, like identifying missing HTTP headers, outdated
software, or weak cookie settings.

### 5. **Automated Vulnerability Scanning**

ZAP can be configured to run vulnerability scans automatically, making
it useful for continuous integration (CI) pipelines and DevSecOps
processes. It can integrate with Jenkins, GitLab CI, and other CI tools
to run security checks during development.

### Key Benefits:

- **Open-source and free**: No licensing costs.
- **Cross-platform**: Runs on Windows, macOS, and Linux.
- **Easy to use**: Offers both beginner-friendly and advanced features.
- **Comprehensive**: Covers a wide range of web application
  vulnerabilities.
- **Community Support**: Active development and a large user community.

### How to Use ZAP

1.  **Download and Install**: You can download ZAP from the official
    OWASP website. It is available as an installer or a Docker
    container.
2.  **Configure Proxy**: Set up your browser or other tools to use ZAP
    as an HTTP proxy (usually at *localhost:8080*).
3.  **Passive Scanning**: Start by browsing the application normally
    while ZAP intercepts the traffic. It will automatically scan the
    traffic for vulnerabilities.
4.  **Active Scan**: Initiate an active scan against the target to
    identify vulnerabilities such as XSS, SQL Injection, etc.
5.  **Review Results**: Analyze the findings in ZAP's interface and
    generate detailed reports.

### Start a scanning

The target we will be using for this lab is an intentionally vulnerable
website that is available on our VM. We will then use WSTG to learn more
about a vulnerability that we discovered.

  
**Required Resources**

- Kali VM customized for the Ethical Hacker course
- Internet access

### Step 1: Open ZAP and start a scanning. 

1.  Start the Kali VM as needed. Navigate to the Kali menu. Search for
     ** zap ** and start the OWASP Zap scanner.
<img width="711" height="770" alt="image" src="https://github.com/user-attachments/assets/d0427a03-dd63-4024-8706-aafbe827b30a" />


2.  Click the topmost radio button to persist the session. This means
    that you can return to the session at a later time.

    <img width="1919" height="938" alt="image" src="https://github.com/user-attachments/assets/1657c365-6a63-4cba-804d-f640f78d7fcc" />


3.  Close the Manage Add-ons dialog window.

4.  In the ZAP main window, click the ** Automated Scan ** to initiate a
    scan.

    <img width="1315" height="836" alt="image" src="https://github.com/user-attachments/assets/3a5d99f3-9d2f-428d-9f2b-63dd4c40b818" />


5.  In the ** URL to Attack ** field, enter **172.17.0.2/dvwa**.

    <img width="1283" height="434" alt="image" src="https://github.com/user-attachments/assets/c739e89f-c775-4122-a47f-641f445f8ed1" />


6.  Click the ** Attack ** button to begin the scan. The scan will should
    take less than 10 minutes to complete.

First, ZAP uses a web spider to crawl the URL to identify the resources
that are available there. It then will apply vulnerability scans to each
resource.

Scan is on-going

<img width="1919" height="965" alt="image" src="https://github.com/user-attachments/assets/a738af2f-9e0f-4d5a-9326-a595e2e61727" />


Scan completed

<img width="1919" height="949" alt="image" src="https://github.com/user-attachments/assets/313c6f00-bd65-4df4-b951-d207321249a7" />


### Step 2: Investigate the results. {#step-2-investigate-the-results.}

1.  Select the **Alerts **tab if it is not already selected. When the
    scan finishes.

   <img width="1919" height="938" alt="image" src="https://github.com/user-attachments/assets/1283b27a-662b-461b-8c19-dfc14082215a" />


2. Locate and click the **Remote Code Execution -- CVE-2012-1823
**alert. Scroll through the details of the alert.

<img width="1919" height="929" alt="image" src="https://github.com/user-attachments/assets/b993a038-9d8e-414f-8f59-f36dc6c00c69" />


Scroll down to the Alert Tags section of the vulnerability. Note the
WSTG key and value. Click the value and use the Ctrl-C keys to copy the
URL to the clipboard.

<img width="1919" height="932" alt="image" src="https://github.com/user-attachments/assets/52238260-d1ce-4c22-9cf7-eb2cd84cbe07" />


Open a browser and paste the URL in the URL. Navigate to the WSTG site
and read about the vulnerability and methods of testing for it. Review
this information about the vulnerability to understand what WSTG offers
to the penetration tester.

<img width="1919" height="931" alt="image" src="https://github.com/user-attachments/assets/66f85f86-cec3-4cba-8221-cfcc9f05ea74" />


# Questions:

In what ways can the OWASP Web Security Testing Guide assist
organizations to secure their applications?

It helps organizations to

- identify steps to build and operate a web application testing program
- determine gaps between existing practices and industry best practices
- ensure that software is coded securely and efficiently
- make informed decisions and about which security activities and tools
  to invest in.
