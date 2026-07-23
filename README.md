# 🛡️ SOC Lab – FTP Dictionary Attack Detection

## 📖 Project Overview

This project demonstrates a hands-on Security Operations Center (SOC) lab focused on authentication monitoring, attack simulation, log analysis, and defensive security controls.

The lab covers Windows authentication event monitoring, FTP server configuration, dictionary attack simulation using Hydra, Bash-based alert scripts, and automated protection with Fail2Ban.

This project was completed as part of practical SOC analyst training to strengthen blue team skills through real-world attack simulation and detection.

## 📑 Table of Contents

- [Project Overview](#-project-overview)
- [Objectives](#-objectives)
- [Technologies Used](#️-technologies-used)
- [Lab Environment](#-lab-environment)
- [Lab Architecture](#-lab-architecture)
- [Task 1 – Windows Authentication Monitoring](#-task-1--windows-authentication-monitoring)
- [Task 2 – FTP Server Configuration](#-task-2--ftp-server-configuration)
- [Task 3 – FTP Dictionary Attack Simulation using Hydra](#-task-3--ftp-dictionary-attack-simulation-using-hydra)
- [Task 4 – FTP Log Analysis](#-task-4--ftp-log-analysis)
- [Task 5 – Bash Alert Scripts](#-task-5--bash-alert-scripts)
- [Task 6 – Fail2Ban Configuration](#️-task-6--fail2ban-configuration)
- [Skills Demonstrated](#-skills-demonstrated)
- [Key Takeaways](#-key-takeaways)
- [References](#-references)
- [License](#-license)
- [Author](#-author)
- [Future Improvements](#-future-improvements)
- [Project Outcome](#-project-outcome)

## 🎯 Objectives

The primary objectives of this lab were to:

- Monitor Windows authentication events using Event IDs **4624** (Successful Logon) and **4625** (Failed Logon).
- Configure and secure an FTP server using **vsftpd**.
- Simulate an FTP dictionary attack using **Hydra**.
- Analyze FTP authentication logs to identify successful and failed login attempts.
- Develop Bash scripts to generate alerts based on login activity.
- Configure **Fail2Ban** to automatically block repeated unauthorized login attempts.
- Gain practical experience with SOC workflows, attack detection, and defensive security monitoring.

  ## 🛠️ Technologies Used

|       Category            |       Technology       |
|---------------------------|------------------------|
| Operating System          | Kali Linux, Windows 11 |
| Virtualization            | Oracle VirtualBox      |
| Authentication Monitoring | Windows Event Viewer   |
| FTP Server                | vsftpd                 |
| Attack Simulation         | Hydra                  |
| Log Analysis              | Linux System Logs      |
| Scripting                 | Bash                   |
| Intrusion Prevention      | Fail2Ban               |

## 💻 Lab Environment

- **Host Operating System:** Windows 11
- **Virtualization Platform:** Oracle VirtualBox
- **Guest Operating System:** Kali Linux
- **FTP Server:** vsftpd
- **Attack Tool:** Hydra
- **Monitoring Tool:** Windows Event Viewer
- **Defensive Tool:** Fail2Ban
- **Shell Scripting:** Bash

## 🏗️ Lab Architecture

```text
                    Windows 11
                         │
                         ▼
        Windows Event Viewer (4624 / 4625)

                    Kali Linux VM
                         │
            ┌────────────┴────────────┐
            ▼                         ▼
     vsftpd FTP Server        Hydra Dictionary Attack
            │
            ▼
        FTP Authentication Logs
            │
            ▼
      Bash Alert Scripts
            │
            ▼
          Fail2Ban
```

## 🔐 Task 1 – Windows Authentication Monitoring

### Objective

Monitor successful and failed Windows logon events using Windows Event Viewer.

### Event IDs Monitored

| Event ID | Description |
|----------|-------------|
| 4624 | Successful Logon |
| 4625 | Failed Logon |

### Activities Performed

- Created a Custom View for Event ID **4624**.
- Created a Custom View for Event ID **4625**.
- Verified successful authentication events.
- Verified failed authentication events.
- Observed event details including user account, logon type, source workstation, and timestamps.

### Skills Demonstrated

- Windows Event Analysis
- Authentication Monitoring
- Security Event Investigation

### Screenshots

#### Successful Logon (Event ID 4624)

![Successful Logon 4624](images/Successful%20Logon%204624%20Custom%20Views.png)

#### Failed Logon (Event ID 4625)

![Failed Logon 4625](images/Failed%20Logon%204625%20Custom%20Views%20.png)

## 📂 Task 2 – FTP Server Configuration

### Objective

Configure a secure FTP server using **vsftpd** to provide a controlled environment for authentication monitoring and attack simulation.

### Activities Performed

- Installed the **vsftpd** FTP server.
- Started and verified the FTP service.
- Created a dedicated FTP user account.
- Configured the FTP server for local user authentication.
- Verified successful FTP login using valid credentials.

### Skills Demonstrated

- Linux System Administration
- FTP Server Configuration
- User Account Management
- Service Verification

### Screenshot

> *(Insert screenshot of the FTP server configuration and successful FTP login here.)*

## 🎯 Task 3 – FTP Dictionary Attack Simulation using Hydra

### Objective

Simulate an FTP dictionary attack using **Hydra** to evaluate the effectiveness of authentication monitoring and defensive security controls.

### Activities Performed

- Used **Hydra** to perform a dictionary attack against the FTP server.
- Configured the target IP address, username, and password wordlist.
- Monitored authentication attempts during the attack.
- Successfully identified valid FTP credentials from the supplied wordlist.
- Verified the attack results through FTP server logs.

### Skills Demonstrated

- Attack Simulation
- Password Auditing
- Dictionary Attack Techniques
- Security Testing
- Authentication Analysis

### Screenshot

![Hydra Dictionary Attack](images/Dictionary%20Attack%20on%20ftp%20user.png)

## 📊 Task 4 – FTP Log Analysis

### Objective

Analyze FTP server logs to identify successful and failed authentication attempts generated during the dictionary attack simulation.

### Activities Performed

- Examined FTP authentication logs generated by **vsftpd**.
- Identified failed login attempts during the dictionary attack.
- Identified the successful login after the correct credentials were discovered.
- Correlated login events with the Hydra attack activity.
- Verified timestamps, usernames, and authentication status.

### Skills Demonstrated

- Log Analysis
- Authentication Monitoring
- Event Correlation
- Security Investigation
- Threat Detection

### Screenshot

![FTP Log Analysis](images/Checking%20FTP%20Failed%20Logins.png)

## 📜 Task 5 – Bash Alert Scripts

### Objective

Develop Bash scripts to automate the detection of FTP authentication events and generate alerts based on login activity.

### Activities Performed

- Created a Bash script to detect successful FTP logins.
- Developed a Bash script to monitor repeated failed login attempts.
- Generated alerts based on predefined conditions.
- Verified that the scripts correctly identified authentication events from the FTP logs.
- Tested the scripts using simulated login attempts.

### Skills Demonstrated

- Bash Scripting
- Security Automation
- Log Monitoring
- Alert Generation
- Linux Administration

### Screenshots

#### Success Alert Script

![Success Alert](images/Sucess%20Alert%20Script%20Created.png)

#### Threshold Alert Script

![Threshold Alert](images/Threshold_Alert%20Created.png)

## 🛡️ Task 6 – Fail2Ban Configuration

### Objective

Configure **Fail2Ban** to automatically detect and block repeated unauthorized FTP login attempts, enhancing the security of the FTP server against dictionary attacks.

### Activities Performed

- Installed **Fail2Ban** on the Kali Linux system.
- Configured the **vsftpd** jail for FTP protection.
- Defined the maximum number of failed login attempts before a ban.
- Configured the ban duration and monitoring settings.
- Verified that Fail2Ban successfully detected and blocked repeated failed login attempts.
- Confirmed the banned IP addresses using Fail2Ban status commands.

### Skills Demonstrated

- Intrusion Prevention
- Linux Security Hardening
- Fail2Ban Configuration
- Automated Threat Mitigation
- Defensive Security

### Screenshots

#### Fail2Ban Service

![Fail2Ban Service](images/Fail2ban%20Created%20and%20Active.png)

#### vsftpd Jail Status

![Fail2Ban Status](images/Fail2ban%20client%20status%20and%20client%20status%20vsftpd.png)

## 🎓 Skills Demonstrated

- Windows Authentication Monitoring
- Windows Event Log Analysis
- Linux System Administration
- FTP Server Configuration (vsftpd)
- Dictionary Attack Simulation
- Hydra Usage
- FTP Log Analysis
- Bash Scripting
- Security Automation
- Fail2Ban Configuration
- Intrusion Prevention
- Security Monitoring
- Blue Team Fundamentals
- SOC Analyst Workflow

  ## 📝 Key Takeaways

This project provided practical experience in monitoring authentication events, simulating password attacks, analyzing security logs, automating detection through Bash scripting, and implementing defensive security controls using Fail2Ban.

The lab demonstrates a complete blue team workflow consisting of:

1. Environment Setup
2. Attack Simulation
3. Event Monitoring
4. Log Analysis
5. Alert Generation
6. Automated Threat Mitigation

Completing this lab strengthened my understanding of authentication security, attack detection, and incident response from a SOC analyst's perspective.

## 📚 References

- [Hydra Documentation](https://github.com/vanhauser-thc/thc-hydra)
- [vsftpd Documentation](https://security.appspot.com/vsftpd.html)
- [Fail2Ban Documentation](https://www.fail2ban.org/)
- [Microsoft Windows Security Auditing](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/security-auditing-overview)

## 📄 License

This project is licensed under the MIT License. See the `LICENSE` file for more information.

## 👨‍💻 Author

**Joshua Samuel**

Aspiring SOC Analyst | Blue Team | Cybersecurity Enthusiast

- 💼 LinkedIn: www.linkedin.com/in/joshuasamuel-soc
- 🐙 GitHub: https://github.com/JoshuSam

## 🚀 Future Improvements

Future enhancements planned for this lab include:

- Integrating Sysmon for enhanced endpoint monitoring.
- Forwarding logs to Splunk SIEM for centralized log analysis.
- Developing custom SPL detection queries.
- Enhancing Bash alert scripts with email notifications.
- Expanding the lab to include additional attack scenarios.
- Creating dashboards for real-time security monitoring.

## 📈 Project Outcome

This project demonstrates a practical Security Operations Center (SOC) workflow—from authentication monitoring and FTP server configuration to attack simulation, log analysis, security automation, and automated threat mitigation.

Completing this lab strengthened my understanding of authentication security, event monitoring, defensive security practices, and SOC analyst responsibilities through hands-on implementation using industry-relevant tools.

*"Every alert tells a story—my job is to uncover it."*
