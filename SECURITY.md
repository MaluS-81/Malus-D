# Security Policy

## Supported Versions

Use this section to tell people about which versions of your project are
currently being supported with security updates.

| Version | Supported          |
| ------- | ------------------ |
| 5.1.x   | :white_check_mark: |
| 5.0.x   | :x:                |
| 4.0.x   | :white_check_mark: |
| < 4.0   | :x:                |

## Reporting a Vulnerability

Use this section to tell people how to report a vulnerability.

Tell them where to go, how often they can expect to get an update on a
reported vulnerability, what to expect if the vulnerability is accepted or
declined, etc.

import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart

# Email address where security vulnerabilities should be reported
security_email = 'security@example.com'

# Function to report a security vulnerability
def report_vulnerability(description, version, operating_system, additional_info=''):
    # Compose email
    subject = 'Security Vulnerability Report'
    body = f"Description: {description}\nVersion: {version}\nOperating System: {operating_system}\nAdditional Information: {additional_info}"
    message = MIMEMultipart()
    message['From'] = security_email
    message['To'] = security_email
    message['Subject'] = subject
    message.attach(MIMEText(body, 'plain'))

    # Send email
    smtp_server = 'smtp.gmail.com'
    smtp_port = 587
    smtp_username = 'your_username'
    smtp_password = 'your_password'
    smtp_conn = smtplib.SMTP(smtp_server, smtp_port)
    smtp_conn.starttls()
    smtp_conn.login(smtp_username, smtp_password)
    smtp_conn.sendmail(security_email, security_email, message.as_string())
    smtp_conn.quit()
    
    # Confirmation message
    print("Thank you for reporting the vulnerability. We take security seriously and will investigate promptly.")
