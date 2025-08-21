# Module 1: Fundamentals of Ethical Hacking


## Introduction

This module establishes a strong foundation in ethical hacking, introducing core concepts, terminologies, and methodologies used in the cybersecurity industry. By the end of this module, you’ll understand not just the “what” and “why” of ethical hacking, but also the “how”—including both technical and legal considerations.


## Topics Covered

### 1. Information Security Overview

- **Definition & Importance:**  
  Information Security (InfoSec) is the practice of protecting information (data) and information systems from unauthorized access, disclosure, modification, destruction, or disruption.
- **The CIA Triad:**  
  - **Confidentiality:** Ensuring only authorized persons can access information.
  - **Integrity:** Maintaining the accuracy and trustworthiness of data.
  - **Availability:** Ensuring information and resources are accessible when needed.
- **Security Objectives:**  
  Why organizations must secure assets: to protect business value, reputation, regulatory compliance, and customer trust.
- **Real-World Example:**  
  Discuss recent high-profile breaches and the impact on organizations.


## 2. Types of Threats and Attack Vectors

### **Types of Threats**

- **Malware (Viruses, Worms, Ransomware, Trojans):**  
  Malicious software designed to disrupt, damage, or gain unauthorized access to computer systems.
  - *Example:* WannaCry ransomware attack in 2017 encrypted files on infected computers and demanded ransom payments in Bitcoin.

- **Phishing and Social Engineering:**  
  Deceptive attempts to trick users into giving away sensitive information (credentials, financial info) or performing actions that benefit the attacker.
  - *Example:* An email pretending to be from a bank asking to "verify your account" by clicking a malicious link.

- **Insider Threats:**  
  Security risks originating from within the organization, often by employees or contractors.
  - *Example:* An employee copying confidential customer data to a USB drive and selling it to competitors.

- **Denial of Service (DoS/DDoS):**  
  Attacks that overwhelm systems, networks, or services, rendering them unavailable to users.
  - *Example:* In 2016, the Mirai botnet launched a massive DDoS attack on DNS provider Dyn, causing widespread internet outages.

- **Man-in-the-Middle (MitM) Attacks:**  
  Attackers secretly intercept and possibly alter communications between two parties.
  - *Example:* An attacker intercepts data between a user and a public Wi-Fi hotspot to steal login credentials.

- **Physical Attacks (Theft, Tampering):**  
  Gaining unauthorized physical access to facilities, devices, or hardware.
  - *Example:* Stealing a company laptop from an employee’s car or installing a hardware keylogger on a workstation.


### **Attack Vectors**

- **Email Attachments and Links:**  
  Malicious files or URLs sent via email to trick users into installing malware or giving up credentials.
  - *Example:* Opening an attached Excel file that runs macros to install spyware.

- **Unpatched Vulnerabilities:**  
  Exploiting known software flaws that have not been fixed or updated.
  - *Example:* Exploiting the EternalBlue vulnerability in unpatched Windows systems.

- **Weak Passwords:**  
  Easily guessed or commonly used passwords that attackers can brute-force or guess.
  - *Example:* Using “password123” as an admin password, which is quickly cracked.

- **Social Media and Public Data:**  
  Gathering information from public profiles or posts to craft targeted attacks (reconnaissance).
  - *Example:* Finding an executive’s travel schedule on LinkedIn and timing a phishing attack while they’re abroad.


### **Threat Actors**

- **Script Kiddies:**  
  Inexperienced individuals who use existing tools or scripts to conduct attacks, often for fun or notoriety.
  - *Example:* A teenager using a downloadable DDoS tool to take down a gaming server.

- **Hacktivists:**  
  Individuals or groups who hack to promote a political or social agenda.
  - *Example:* Anonymous defacing government websites in protest of a new law.

- **Organized Crime Groups:**  
  Professional criminals who use cyberattacks for financial gain.
  - *Example:* A syndicate deploying ransomware to extort millions from hospitals.

- **Nation-State Actors:**  
  Government-sponsored attackers conducting espionage, sabotage, or attacks for strategic objectives.
  - *Example:* Alleged Russian APT groups breaching energy sector networks to gather intelligence.


### **Threat Modeling**

- **Definition:**  
  Threat modeling is the structured process of identifying, categorizing, and prioritizing potential threats to a system, application, or network. It helps organizations understand where their greatest risks lie and how to mitigate them with appropriate countermeasures.

- **Example:**  
  Imagine a company is developing a new online banking app. During a threat modeling session, the security team:
  - Identifies **assets** (customer data, financial transactions).
  - Lists **potential threats** (SQL injection, unauthorized access, data breaches, phishing).
  - Maps **attack vectors** (web forms, APIs, login pages).
  - **Prioritizes risks** by likelihood and impact (e.g., SQL injection is high risk because it could expose customer accounts).
  - Recommends **countermeasures** (input validation, multi-factor authentication, regular vulnerability scanning).
  
  By using threat modeling, the company proactively addresses critical security issues before the app is deployed, reducing the chance of a successful attack.


### 3. Hacking Concepts and Their Types

- **Definition of Hacking:**  
  Gaining unauthorized access to data in a system or computer.
- **Types of Hackers:**  
  - **White Hat:** Ethical hackers, authorized to test and secure systems.
  - **Black Hat:** Malicious hackers, break into systems for personal gain.
  - **Gray Hat:** Operate between white and black hat, may violate laws or ethical standards but without malicious intent.
- **Ethical Hacking Principles:**  
  - Permission-based testing
  - Responsible disclosure
  - Maintaining confidentiality
- **Common Misconceptions:**  
  Not all hackers are criminals; ethical hacking is legal and beneficial when done with permission.


### 4. Penetration Testing Concepts and Their Types

- **Definition:**  
  Penetration testing (pentesting) simulates real-world attacks to identify vulnerabilities before attackers do.
- **Types of Pentesting:**  
  - **Black-box:** No prior knowledge of the target.
  - **White-box:** Full knowledge of the target (source code, architecture).
  - **Gray-box:** Limited knowledge (user credentials, partial system info).
- **Testing Approaches:**  
  - **External Pentest:** Testing from outside the organization’s network (internet-facing assets).
  - **Internal Pentest:** Testing from within the organization’s network (simulating insider threats).
- **Pentest Phases:**  
  - Planning and reconnaissance
  - Scanning and enumeration
  - Exploitation
  - Post-exploitation
  - Reporting
- **Deliverables:**  
  Detailed findings, risk ratings, and remediation guidance.


### 5. Scope of Ethical Hacking

- **Legal Considerations:**  
  - Laws and regulations (e.g., Computer Fraud and Abuse Act, GDPR)
  - Obtaining written authorization before any testing
- **Responsible Disclosure:**  
  - Reporting vulnerabilities to vendors/organizations privately
  - Coordinating with CERT/bug bounty programs
- **Industry Standards:**  
  - **ISO 27001/27002:** Information security management standards
  - **NIST Cybersecurity Framework:** Guidelines for managing and reducing cybersecurity risk
  - **PCI DSS:** Security standards for organizations handling cardholder data
- **Code of Ethics:**  
  - Respect privacy and property
  - Do no harm
  - Report all findings truthfully


## Hands-on Activities

1. **Research and Summarize a Recent Security Breach**
   - Select a breach from the last 2 years (e.g., MOVEit, SolarWinds, or any recent ransomware incident).
   - Identify:  
     - What was compromised?  
     - Attack vectors used  
     - Threat actors involved  
     - Impact and response

2. **Group Discussion: Types of Hackers and Pentesting Approaches**
   - Prepare a presentation comparing white hat, black hat, and gray hat hackers.
   - Discuss different pentesting methodologies (black-box, white-box, gray-box).
   - Share real-world scenarios for each.

3. **Legal Scope and Code of Ethics for Ethical Hacking**
   - Review and summarize the EC-Council or (ISC)² Code of Ethics.
   - Draft a sample “Authorization to Test” letter.
   - Present the legal and ethical boundaries of pentesting in your country or region.


## Further Study & Resources

- **Books:**  
  - “The Web Application Hacker’s Handbook” by Dafydd Stuttard & Marcus Pinto  
  - “Hacking: The Art of Exploitation” by Jon Erickson
- **Websites:**  
  - [OWASP Top 10](https://owasp.org/www-project-top-ten/)
  - [HackerOne Hacktivity](https://hackerone.com/hacktivity)
  - [CVE Details](https://www.cvedetails.com/)
- **Certifications:**  
  - CEH (Certified Ethical Hacker)
  - OSCP (Offensive Security Certified Professional)


> **Tip:** Always seek proper authorization before performing any security assessment. Ethical hacking without consent is illegal and unethical.
