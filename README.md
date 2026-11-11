<div align="center">


<img width="1007" height="831" alt="Copilot_20261027_105204" src="https://github.com/user-attachments/assets/b2c4ae05-abb6-4cbe-94e3-65bbfaa1a0fd" />

# 🛡️ PENETRATION TESTING REPORT

### 🔎 FOOTPRINTING, RECONNAISSANCE & NETWORK SCANNING STAGES



<img src="https://img.shields.io/badge/CYBERSECURITY-NETWORKWALKS-0A66C2?style=for-the-badge&logo=hackthebox&logoColor=white" />
<img src="https://img.shields.io/badge/WEEK%202-B084-6F42C1?style=for-the-badge" />
<img src="https://img.shields.io/badge/PERMITTED-YES-22C55E?style=for-the-badge" />





**W2-PM-FINAL | CYBERSECURITY |  NETWORKWALKS**


## 🛡️ WORK HIGHLIGHTS


| **Sectors** | **Deliverables** |
|---|---|
| 👤 **Pentester name** | Popoola Emmanuel Babalola |
| 🎓 **Program / Batch** | B084 Networkwalks |
| 📅 **Date delivered** | 09 November 2026 |
| 🧪 **Core Features Built** | W2-PM1 Multiple Kali Tools<br>W2-PM5 Scanning using Zenmap |
| 🎯 **Targets** | Networkwalks Permitted Target<br>My Own Local LAN Network |
| 🔐 **Privilege Management** | Written Permission Approved |
| 🔎 **Phase 1** | Reconnaissance & Footprinting |
| 🌐 **Phase 2** | Scanning & Network Discovery |
| 🚧 **Phases 3–5** | In Progress |
| 🖥️ **Baseline TOOLS** | Kali Linux & Windows |

---



# 1. Liability Disclaimer

> **PERMISSION MANAGEMENT ACCESS ONLY**
> 
**I have carried out security testing activities only on systems and devices that I personally own or for which I have obtained explicit, written authorization. All demonstrations, notes, and materials provided here are intended solely for educational and research purposes**.

Nothing in this project should be used to engage in unlawful activity. The authors, instructors, and NETWORKWALKS accept no responsibility for how this information is applied. Every individual is accountable for their own actions.

**Improper or unauthorized use of these techniques can result in criminal prosecution, severe financial penalties, termination of employment, and a permanent record. In most cases, even accessing a system without permission  regardless of whether damage occurs is considered a crime.
By engaging with this material, you acknowledge these risks and agree to act responsibly, ethically, and within the boundaries of the law.**


> 🛡️ **Security principle:** Endeavor to respect and define the authorized policies before starting reconnaissance or security testing.


# 2. Introduction

**Cybersecurity is a discipline built on understanding how attackers think, and penetration testing provides a safe, controlled environment to explore those methods. In the week 2 of my internship at Networkwalks, I focused on two important parts of the penetration testing process: footprinting and scanning.**

**Footprinting involves the process of gathering publicly available information about a target domain in this case, (networkwalks.com) using specialized tools within Kali Linux. This phase demonstrates how an adversary(attacker) begins by mapping the digital footprint of an organization before attempting deeper intrusion.**

**Scanning, on the other hand, shifts the perspective inward. Using Zenmap on my personal Windows machine, I explored my own local network to identify active hosts and services. This exercise highlights how attackers moves from external reconnaissance to internal mapping, building a clearer picture of potential entry points.**

These two steps show how an attacker might move from gathering information about a system to actively mapping devices on a network. In this report, I explain each command I used, the results I saw, screenshots as proof, and short notes on why the findings matter from an attacker’s point of view.

-------


# 3. Tools Used

**The table below lists each tool used in this report and its purpose.**

| **Tool 	| **Purpose** |
| ----|----|
| **Kali Linux & Windows** |	Security testing and reconnaisance environment |
| **Whois**	| Retrieves domain registration information such as ownership details, creation/expiry dates, and associated name servers. |
| **WhatWeb** |	Identifies technologies running on a web server, including CMS platforms, plugins, and IP details |
| **Nslookup**  |	Resolve the domain name to its IP address using DNS |
| **Curl -I**	| Displays HTTP response headers to reveal server information and configurations |
| **Wafw00f**   |	Detects the presence of a Web Application Firewall protecting the target site |
| **DNSrecon**   |	Enumerate all DNS records (NS, MX, SPF, TXT, SRV) |
| **Zenmap (Nmap GUI)** 	| Scan the local subnet to find live hosts, IPs and MAC addresses |
| **Windows CMD**  |	Used to check local IP and MAC address details on the host machine |

-----

# 4. Activities Performed
## 4.1 Footprinting & Reconnaissance

During this phase, I performed reconnaissance against the networkwalks.com domain using six different tools available in Kali Linux: WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, and DNSRecon. Each tool was applied to gather a specific type of information about the target.


*WHOIS Used to obtain publicly available domain registration details, including ownership information and the domain’s name servers. This provided insight into the registration and hosting infrastructure.*

*WhatWeb  I applied this to identify the technologies running on the website. The scan revealed WordPress version 7.0.4 and WP Download Manager 3.3.58, along with other components exposed by the site.*

*Nslookup Executed to resolve the domain name into its IP address. The result showed the IP address 192.232.216.135.*

*Curl (-I option) I used this to inspect the HTTP response headers. This revealed additional details about the web application, including the exposed WordPress REST API endpoint /wp-json/.*

*Wafw00f Run to check for the presence of a Web Application Firewall. The tool identified ModSecurity (SpiderLabs) protecting the site.*

*DNSRecon Employed to enumerate DNS records. The results included information about name servers, mail servers, SPF/TXT records, service records, and DNS software details.*

-------

# 4.2 Network Scanning with Zenmap

For the second task, I carried out network discovery on my local environment using Zenmap. The goal was to determine my local IP address and subnet, identify active hosts, record their IP and MAC addresses, and create a basic network topology.

I began by running the ipconfig command in Windows to confirm my local IP address and the subnet of my LAN. With this information, I entered the subnet range into Zenmap and selected the Ping Scan option to detect devices that were online.

####The practical exercise produced the following example results, showing four live hosts within the subnet:

```text
10.0.0.1
10.0.0.4
10.0.0.19
10.0.0.5
```

This process demonstrated how attackers can move from identifying a network range to mapping out which devices are active, forming the foundation for deeper probing or service enumeration.

# Network Topology Results

In addition to identifying live hosts, the scan also revealed their corresponding MAC addresses, giving a clearer picture of the devices present on the subnet.

Once the discovery phase was complete, I navigated to the Topology view in Zenmap. I enabled the legend for clarity and exported the generated network map in PDF format, as required by the practical exercise.
Note: When finalizing the report, the subnet range, number of hosts, and address details should be updated with the actual results from my own network environment rather than the example values shown here.


# 5. Risk Analysis / Impact

Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.
	Risk/Finding	Evidence/Observation	Potential Impact 	Risk Level
1.	Exposure of web technologies	WhatWeb revealed WordPress and WP Download Manager versions in use	Attackers could leverage version details to search for known vulnerabilities or outdated components	● Medium
2.	Server IP address disclosed	Nslookup resolved the domain to 192.232.216.135	Provides adversaries with direct knowledge of the network location hosting the service	● Low
3.	HTTP header information visible	Curl output displayed response headers and exposed the /wp-json/ endpoint	Assists in fingerprinting the application and may enable further enumeration	● Low
4.	WAF technology identifie	Wafw00f detected ModSecurity (SpiderLab	Reveals details about the site’s defensive setup, which could guide attackers in tailoring bypass attempts	● Low
5.	DNS records enumerated.	DNSRecon listed name servers, mail servers, SPF/TXT, and service records	Offers a broader view of the infrastructure, potentially aiding in mapping and targeted attacks	● Medium
6.	Active hosts detected on local network	
Zenmap scan showed four live hosts in the example subnet	Presence of unknown or unauthorized devices could pose internal security risks	● Medium

Risk level key:  ● Critical  ● Medium  ● Low
The items listed above represent observations from footprinting and scanning exercises, rather than confirmed vulnerabilities. These practical tasks were focused on information gathering and host discovery, and did not involve exploitation or vulnerability validation.
As a result, details such as software versions, IP addresses, or DNS records should be viewed as potential indicators rather than proof of weakness. Their presence alone does not confirm that a system is insecure. To determine whether any actual vulnerabilities exist, further authorized security testing and validation would be required.

6. Recommendations
Based on the observations from these activities, I recommend the following security improvements:
1.Assess Publicly Exposed Technology Details Regularly evaluate what information about web technologies, CMS platforms, and plugins is visible externally to reduce unnecessary exposure.

2.Maintain UptoDate Software Ensure CMS platforms, plugins, and supporting technologies are consistently updated and checked against current security advisories.

3.Harden HTTP Response Headers Review and adjust HTTP headers to minimize disclosure of technical details that could aid attackers in reconnaissance.

4.Audit DNS Records Periodically Conduct routine checks of DNS records to confirm that only essential information and services are publicly accessible.

5.Optimize and Monitor WAF Configuration Keep the Web Application Firewall (ModSecurity) active, properly tuned, and continuously monitored to strengthen protection against common attacks.

6.Conduct Internal Network Discovery Perform scheduled scans of internal networks to identify active devices and maintain visibility of the environment.

7.Investigate Unrecognized Devices Any unexpected or unauthorized device detected during scanning should be promptly investigated and validated.

8.Maintain Accurate Network Documentation Keep network topology diagrams and device inventories updated to support effective monitoring and incident response.

9.Ensure Authorized Security Testing Reconnaissance and scanning activities must only be performed on systems and networks where explicit authorization has been granted.

7. Conclusion
During the second week of my internship at Networkwalks, I focused on practical exercises in footprinting, reconnaissance, and network scanning. These activities helped me understand how attackers gather information before attempting exploitation, and how defenders can use the same techniques to strengthen security at large.
Footprinting & Reconnaissance
Using six tools in Kali Linux, I explored different ways to collect information about a target domain:
WHOIS – retrieved domain registration details and name servers.
WhatWeb – identified web technologies in use, including CMS and plugins.
Nslookup – resolved the domain name to its IP address.
Curl (-I) – inspected HTTP response headers and revealed endpoints.
Wafw00f – detected the presence of a Web Application Firewall (ModSecurity).
DNSRecon – enumerated DNS records such as mail servers, SPF/TXT, and service records.
Network Scanning
On my local environment, I used Zenmap to:
Identify my IP address and subnet.
Discover active hosts and collect their IP/MAC addresses.
Generate a network topology map for visualization.
Lesson learned:
Information gathering is critical: even without exploitation, a large amount of intelligence can be collected from public sources and basic scans.
Documentation matters: a strong cybersecurity report should clearly explain what was done, what was found, why it matters, and how risks can be reduced.
Ethics and authorization are essential: all reconnaissance and scanning must be performed within an approved scope. My activities were limited to authorized lab environments and my own network.
8. Evidences Collected









-End-


👤 Author
Popoola Emmanuel (Manueldcyberspeaks!)
Cybersecurity Professional || Networkwalks Intern || B084 
LinkedIn: https://www.linkedin.com/in/popoolaemmanuel/

📌 Project Information
Program Name: Cybersecurity program at Networkwalks | Week: 02 | Repository: GitHub

