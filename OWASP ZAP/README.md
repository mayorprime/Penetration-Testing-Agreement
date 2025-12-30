## This lab focuses on OWASP ZAP

## OWASP ZAP (Zed Attack Proxy) 
It is an open-source security testing tool that helps you identify vulnerabilities in web applications. It's mainly used for penetration testing and security scanning to find potential security flaws such as SQL injection, cross-site scripting (XSS), and other common web-based threats.

## What makes OWASP ZAP important:

Proxy Functionality: ZAP acts as a "man-in-the-middle" proxy that sits between the web browser and the application you're testing. It intercepts and inspects the HTTP(S) traffic, allowing you to analyze and modify requests and responses in real-time.

Automated Scanning: It can automatically scan a web application for vulnerabilities by analyzing the website’s traffic. It checks for things like authentication issues, input validation flaws, and session handling problems.

Manual Testing Features: Besides automated scans, ZAP also has tools for manual testing, such as fuzzing (sending random data to test how the app responds) and advanced request modification.

Easy to Use: It’s designed to be user-friendly, with a GUI (Graphical User Interface) that makes it easy to visualize vulnerabilities. It’s a great tool for both beginner and advanced users.

Extensibility: ZAP can be extended with plugins to add more features or integrate with other tools, such as CI/CD pipelines for continuous security testing.

Community and Support: Since ZAP is maintained by OWASP (Open Web Application Security Project), a community-driven organization focused on improving software security, it has a lot of community support and documentation available.

## owasp zap.md has the lab practice on how to use owasp zap on your web app
In the lab we use an intentionally vulnerable website that is available on our VM
