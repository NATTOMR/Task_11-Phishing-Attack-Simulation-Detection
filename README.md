# Task_11-Phishing-Attack-Simulation-Detection

## 📌 Project Overview
Phishing is one of the most common and effective social engineering attacks used to compromise organizations.  
This project demonstrates a **controlled phishing attack simulation** conducted in a **lab environment** to understand phishing techniques, analyze user behavior, identify red flags, and document prevention strategies.

> ⚠️ **Ethical Disclaimer**  
> This project was conducted strictly for **educational and security awareness purposes**.  
> No real users, credentials, or organizations were targeted.

---

## 🎯 Objectives
- Understand how phishing attacks are designed and executed
- Simulate a phishing campaign in a controlled environment
- Analyze user interaction and responses
- Identify common phishing red flags
- Learn phishing prevention and mitigation techniques
- Improve social engineering awareness

---

## 🧰 Tools & Technologies

### Primary Tool
- **GoPhish** – Open-source phishing simulation framework

- # 🛠️ Install GoPhish on Kali Linux (Step by Step)

> ⚠️ **Warning**  
> Use GoPhish **ONLY** in a lab or authorized environment for security awareness and training.

---

## ✅ Step 1: Update Kali Linux

Open a terminal and run:
`sudo apt update && sudo apt upgrade -y`

## 🧠 Step 2: Check System Architecture
GoPhish depends on your CPU architecture.
`uname -m`

 ### Expected Output

- ✅ x86_64 → Supported

- ❌ aarch64 (ARM) → Use a VM with x86_64

## 📁 Step 3: Move to /opt Directory
This is the standard location for third-party security tools.
`cd /opt`

## 📥 Step 4: Download GoPhish
Download the latest Linux 64-bit release:

`sudo wget https://github.com/gophish/gophish/releases/download/v0.12.1/gophish-v0.12.1-linux-64bit.zip`

## 📦 Step 5: Extract GoPhish
`sudo unzip gophish-v0.12.1-linux-64bit.zip`

Enter the GoPhish directory:
`cd gophish`

## 🔑 Step 6: Make GoPhish Executable
`sudo chmod +x gophish`

## ⚙️ Step 7: Configure GoPhish (Recommended)
Edit the configuration file:
`sudo nano config.json`

## 🔧 Change Admin Interface to Localhost
Find:

- "listen_url": "0.0.0.0:3333"
Change it to:

- "listen_url": "127.0.0.1:3333"
![image](https://github.com/NATTOMR/Task_11-Phishing-Attack-Simulation-Detection/blob/main/images/GoPhish%20Dashboard.png)
# After open the Gophish to lanche a phishing attack(lab environment)

## 🔹 STEP 1: Create a NEW Email Template

- Go to Email Templates

- Click + New Template

- Fill like this:

1. Name -

`Password Reset Simulation – Test 2`


2. Envelope Sender

`IT Support <it-support@lab.local>`


3. Subject

`Password Reset Required`

4. Text Tab →

Hello {{.FirstName}},

We received a request to reset your account password.

If this was you, please confirm using the link below:
{{.URL}}

If you did not request this, please review immediately.

This email is part of a security awareness exercise.``


5. HTML Tab → paste this:
   
<html>
  <body style="font-family: Arial;">
    <h6>Password Reset Notice</h6>
      <p>Hello {{.FirstName}},</p> 
    <p> A password reset request was initiated for your account. </p>
    <p>
      <a href="{{.URL}}"
         style="background:#2980b9;color:white;
                padding:10px 16px;text-decoration:none;
                border-radius:4px;">
        Confirm Reset
      </a>
    </p>
 <p style="font-size:12px;color:gray;">
      This is a cybersecurity awareness simulation.
    </p>
  </body>
</html>


 ✅ Leave Add Tracking Image ON
 👉 Click Save Template
![image](https://github.com/NATTOMR/Task_11-Phishing-Attack-Simulation-Detection/blob/main/images/GoPhish%20Email-Tamplate.png.jpeg)


#🔹 STEP 2: Create a NEW Landing Page

- Go to Landing Pages

- Click + New Page

- Name
`Password Reset Awareness – Test 2`

- Paste this HTML:
<html>
  <body style="font-family: Arial; text-align:center; margin-top:80px;">
    <h2>Password Reset Simulation</h2>
    <p>
      This was a simulated phishing email.
    </p>
    <p>
      Real attackers often use fake password reset messages
      to steal credentials.
    </p>
    <p style="color:green;">
      Always verify reset requests before clicking links.
    </p>
  </body>
</html>


- ❌ DO NOT check “Capture Submitted Data”
- 👉 Click Save Page
![image](https://github.com/NATTOMR/Task_11-Phishing-Attack-Simulation-Detection/blob/main/images/GoPhish%20Landing-Pages.jpeg.png)
  ## Sending Profile (MailHog)
  🔸 Name
`MailHog Lab`

🔸 Interface Type
`SMTP`

🔸 SMTP From
`alerts@bank-lab.local`


- (Simple email only — no display name)

🔸 Host 🚨 MOST IMPORTANT
`127.0.0.1:1025`

🔸 Username
`(leave empty)`

🔸 Password
`(leave empty)`

🔸 Ignore Certificate Errors

✅ Checked


🔹 STEP 3: Save the Profile

- Click:
- 👉 Save Profile
  
  
## 🔹 STEP 3: Create a NEW Campaign

- Go to Campaigns

- Click + New Campaign

### Fill like this:

- Name

`Password Reset Test – Feb 2026`


- Email Template

`Password Reset Simulation – Test 2`


- Landing Page

`Password Reset Awareness – Test 2`


- URL

`http://127.0.0.1`


- Sending Profile

MailHog Lab


## Groups

`Security Awareness Lab – Feb 2026`

## 🔹 STEP 4: Launch 🚀

- Click Launch Campaign

- Confirm Launch
![image](https://github.com/NATTOMR/Task_11-Phishing-Attack-Simulation-Detection/blob/main/images/Campaign.jpeg)
## 🔹 STEP 5: Watch Results
- Open MailHog
- http://127.0.0.1:8025

  
### Supporting Tools
- Visual Studio Code
- Web browser
- Localhost / Virtual Machine environment

---

## 📖 Understanding Phishing Attacks

### Common Phishing Techniques
- Credential harvesting
- Urgency-based messaging
- Impersonation (IT, HR, banks)
- Malicious links
- Spoofed domains

### Social Engineering Tactics
- Sense of urgency
- Authority impersonation
- Fear of account suspension
- Generic greetings

---

## ✉️ Phishing Email Template (Simulation)

### Scenario
**Theme:** Account Security Alert

**Email Characteristics:**
- Appears to be from internal IT support
- Urgent security message
- Embedded login link

**Intentional Red Flags:**
- Generic greeting
- Slight domain mismatch
- Urgency pressure
- Suspicious link behavior

---

## 🌐 Landing Page Setup

### Purpose
Simulate a credential harvesting page **without storing real credentials**.

### Landing Page Behavior
- Fake login form (username & password fields)
- Logs submission attempts only
- Redirects users to a phishing awareness message

### Awareness Message Example
> “This was a phishing simulation.  
> Always verify email senders and links before entering credentials.”

---

## 📤 Sending the Test Phishing Email

### Campaign Configuration
- Campaign Type: Training Simulation
- Target: Test email accounts
- Email Template: Security Alert
- Landing Page: Fake login page
- Tracking Enabled:
  - Email opened
  - Link clicked
  - Form submitted

---

## 📊 Tracking & Response Analysis

### Metrics Collected
| Metric | Description |
|------|------------|
| Emails Sent | Total phishing emails |
| Emails Opened | User curiosity |
| Links Clicked | Phishing susceptibility |
| Forms Submitted | High-risk behavior |
| Emails Ignored | Security-aware behavior |

### Example Results
- Emails Sent: 10  
- Emails Opened: 7  
- Links Clicked: 4  
- Forms Submitted: 2  

---

## 🚩 Identifying Phishing Red Flags

### Email Indicators
- Suspicious sender address
- Grammar and spelling errors
- Urgent or threatening language
- Unexpected attachments or links

### Link Indicators
- URL shortening services
- Domain mismatches
- HTTP instead of HTTPS

### Behavioral Indicators
- Pressure to act quickly
- Requests for credentials
- Fear-based messaging

---

## 🛡️ Prevention & Mitigation

### User Awareness
- Verify sender identity
- Hover over links before clicking
- Never share credentials via email

### Technical Controls
- SPF, DKIM, and DMARC implementation
- Email filtering and sandboxing
- Multi-factor authentication (MFA)

### Organizational Measures
- Regular phishing simulations
- Security awareness training
- Clear incident reporting procedures

---

## 📝 Documentation & Reporting

### Phishing Simulation Report Includes:
- Project objectives and scope
- Tools and environment used
- Campaign setup
- Results and metrics
- Risk analysis
- Security recommendations

---

## ✅ Final Outcome
- Improved understanding of phishing attacks
- Hands-on experience with phishing detection
- Awareness of social engineering techniques
- Practical blue-team defensive skills

---

## 📁 Project Deliverables
- Phishing simulation report
- Email and landing page templates
- Security awareness documentation

---

## 📌 Portfolio Summary
**Phishing Attack Simulation & Detection**  
Conducted a controlled phishing simulation using GoPhish to analyze user behavior, identify phishing red flags, and document mitigation strategies in a lab environment.

---

## 🔒 Disclaimer
This project is for **educational and defensive security purposes only**.
