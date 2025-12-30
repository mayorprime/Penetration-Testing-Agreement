## Scan a Website and Investigate Vulnerability

In this part of the lab, you will conduct a vulnerability scan using the
**Zed Attack Proxy** (ZAP).

What is OWASP ZAP:

OWASP ZAP (Zed Attack Proxy) is a popular open-source security testing
tool used for finding vulnerabilities in web applications. It is
maintained by the Open Web Application Security Project (OWASP) and is
widely used by penetration testers, security researchers, and developers
to identify security flaws early in the development lifecycle.

Features and uses of OWASP ZAP:

### 1. **Web Application Security Testing** {#web-application-security-testing}

ZAP is designed to automatically scan and identify vulnerabilities in
web applications. It provides both manual and automated security testing
capabilities.

### 2. **Intercepting Proxy** {#intercepting-proxy}

ZAP works as a proxy server that sits between the user and the target
web application. It intercepts HTTP and HTTPS traffic, allowing you to
analyze and manipulate requests and responses. This feature is useful
for testing various security issues like:

- Cross-Site Scripting (XSS)
- SQL Injection
- Session Management flaws
- Security misconfiguration

### 3. **Active Scanning** {#active-scanning}

ZAP has an active scanning feature that automatically checks for known
vulnerabilities in web applications, such as injection flaws, security
misconfiguration, and sensitive data exposure. Active scans are
generally more comprehensive and intrusive compared to passive scans.

### 4. **Passive Scanning** {#passive-scanning}

Passive scanning analyzes the HTTP/HTTPS traffic for security weaknesses
without actually altering the requests or responses. It doesn\'t
actively send malicious payloads but looks for vulnerabilities based on
patterns in the traffic, like identifying missing HTTP headers, outdated
software, or weak cookie settings.

### 5. **Automated Vulnerability Scanning** {#automated-vulnerability-scanning}

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

### Step 1: Open ZAP and start a scanning. {#step-1-open-zap-and-start-a-scanning.}

1.  Start the Kali VM as needed. Navigate to the Kali menu. Search for
    **zap **and start the OWASP Zap scanner.

    ![](Pictures/10000000000002C700000302D0F0E197.png){width="14.609cm"
    height="15.82cm"}

2.  Click the topmost radio button to persist the session. This means
    that you can return to the session at a later time.

    ![](Pictures/100000000000077F000003AA41D6BB5C.png){width="17cm"
    height="8.31cm"}

3.  Close the Manage Add-ons dialog window.

4.  In the ZAP main window, click the **Automated Scan **to initiate a
    scan.

    ![](Pictures/100000000000052300000344507DA84B.png){width="17cm"
    height="10.806cm"}

5.  In the **URL to Attack **field, enter **172.17.0.2/dvwa**.

    ![](Pictures/1000000000000503000001B285EC2F2E.png){width="17cm"
    height="5.75cm"}

6.  Click the **Attack **button to begin the scan. The scan will should
    take less than 10 minutes to complete.

First, ZAP uses a web spider to crawl the URL to identify the resources
that are available there. It then will apply vulnerability scans to each
resource.

Scan is on-going

![](Pictures/100000000000077F000003C563064F31.png){width="17cm"
height="8.548cm"}

Scan completed

![](Pictures/100000000000077F000003B513B0A5F8.png){width="17cm"
height="8.405cm"}

### Step 2: Investigate the results. {#step-2-investigate-the-results.}

1.  Select the **Alerts **tab if it is not already selected. When the
    scan finishes.

    ![](Pictures/100000000000077F000003AAE0C9A12D.png){width="17cm"
    height="8.31cm"}

2. Locate and click the **Remote Code Execution -- CVE-2012-1823
**alert. Scroll through the details of the alert.

![](Pictures/100000000000077F000003A117EC83ED.png){width="17cm"
height="8.229cm"}

Scroll down to the Alert Tags section of the vulnerability. Note the
WSTG key and value. Click the value and use the Ctrl-C keys to copy the
URL to the clipboard.

![](Pictures/100000000000077F000003A49DA80D1A.png){width="17cm"
height="8.255cm"}

Open a browser and paste the URL in the URL. Navigate to the WSTG site
and read about the vulnerability and methods of testing for it. Review
this information about the vulnerability to understand what WSTG offers
to the penetration tester.

![](Pictures/100000000000077F000003A3A99AD389.png){width="17cm"
height="8.246cm"}

# Questions:

In what ways can the OWASP Web Security Testing Guide assist
organizations to secure their applications?

It helps organizations to

- identify steps to build and operate a web application testing program
- determine gaps between existing practices and industry best practices
- ensure that software is coded securely and efficiently
- make informed decisions and about which security activities and tools
  to invest in.
