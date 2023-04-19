# Adversary-Emulation-Plan

-   Team Members: Adeel Fareed, Brian Fields, Harshal Shinde, Solomon Ruzima, Ugochukwu Egonu.
-   Description of project
-     This project is intended to apply the MITRE ATT&CK framework and tools to map a cyber incident and then use the Caldera tool to complete an emulation plan. The attack chosen is a 2020 spear phishing campaign launched against Twitter, in which the credentials of many high profile users were compromised.
-   Objectives of the attack
-     To identify a real-world cybersecurity incident that we will make to the MITRE ATT&CK framework.
-     To map a real-world incident to the MITRE ATT&CK framework. By mapping the attack to the MITRE ATT&CK framework, we will be able to understand the tactics, techniques, and procedures used by attackers in a specific incident.
-     To use the information gathered in the mapping process to create an Adversary Emulation Plan using the Caldera tool that simulates the identified incident.
-     To conduct an emulation of the incident using the created Adversary Emulation Plan in a mock-up scenario built in the cloud that accurately represents the system compromised in the incident.
-     To create an incident report including a STIX2.1JSON representation using the information gathered in the incident mapping and emulation.​
# Tools/Applications
[![GCP Logo](https://skillicons.dev/icons?i=gcp&theme=light)](https://skillicons.dev)  [![Wazuh Logo]( https://github.com/wazuh/wazuh-packages/blob/4.3/stack/dashboard/base/files/etc/custom_welcome/Assets/Favicons/mstile-70x70.png?raw=true )](https://wazuh.com/)  [![Squid Proxy Server Logo]( http://www.squid-cache.org/Artwork/SN.png )]( http://www.squid-cache.org/ )
- Caldera
-       Caldera refers to an open-source framework used for automated adversary emulation, which is also commonly known as Red Teaming or Penetration Testing. This tool is designed to enable users to simulate real-world attacks, test the security defenses of a network or system, and provide a detailed report of the results.
-         Caldera Resources used:
-           https://github.com/mitre/caldera
-           https://caldera.readthedocs.io/en/latest/
-          https://www.youtube.com/watch?v=EIHLXWnK1Dw
- Wazuh
-       Open-source security platform that unifies XDR and SIEM protection for endpoints and cloud workloads. We used it as a SIEM for our endpoints in Google Cloud Platform.
-         Wazuh Resources used:
-           https://documentation.wazuh.com/current/installation-guide/index.html
-           https://documentation.wazuh.com/current/installation-guide/wazuh-agent/index.html
- Squid
-       Squid is a caching and forwarding HTTP web proxy. It has a wide variety of uses, including speeding up a web server by caching repeated requests, caching web, DNS and other computer network lookups.
-         Squid Resources used:
-           https://cloud.google.com/vpc/docs/special-configurations
-           https://www.anoopcnair.com/how-to-configure-proxy-settings-in-windows-11/
- Social Engineering Toolkit
-       The Social Engineering Toolkit is an open-source penetration testing framework designed for social engineering. SET has many custom attack vectors that allow a user to make a believable attack quickly. SET offers multiple attack vectors and techniques and below are some of the common attacks used on the kit
-         SET Resources used:
-           https://github.com/trustedsec/social-engineer-toolkit/blob/master/README.md

-         Phishing attacks
-         Web attacks
-         Infectious Media Generator
-         Create a Payload and Listener
-         Mass Mailer Attack
-       For this project, the attack used is the credential harvester method. Credential harvester method is used when a user doesn't want to specifically get a shell but perform phishing attacks to obtain usernames and passwords from the system. In this attack vector, a website will be cloned, and when the victim enters the user credentials, the usernames and passwords will be posted back to the attacker's machine. After that, the victim will be redirected back to the legitimate site.

- Web Domains w/ Email Accounts
-         Two domains were registered on godaddy one being cy7900team.com and another being cy79ooteam3.com.
-         Three email addresses were added to the domains solomon.ruzima@cy7900team3.com, brian.fields@cy7900team3.com and brianfields@cy79ooteam3.com.
-       
# Network Architecture Picture(s)
-   <img width="591" alt="Screen Shot 2023-04-17 at 9 58 30 PM" src="https://user-images.githubusercontent.com/84095697/232651827-8dfe4dc1-98b7-4840-9022-4884f607e3bd.png">

# Network Architecture Description
-   Firewall Rules
-     Should be in a separate config file (firewall-rules.json)

- Attackvpc
- Caldera-srv - This is the virtual machine in the attack vpc on which the caldera tool is installed and run. The server has two network interfaces one is internal and the other external.
-         OS: Debian
-         Machine Type: e2-standard-2
-         CPUs: 2 vCPU
-         Memory: 8 GBs
- Caldera-client - This is the virtual machine in the attack vpc that is used to access the caldera services. The caldera tool GUI is accessed via the web.
-         OS: Windows
-         Machine Type: e2-medium
-         CPUs: 1-2 vCPU (1 shared core)
-         Memory: 4 GBs
- proxy-server - This instance served as a proxy server to all the instances in both targetvpc and attackvpc
-         OS: Debian
-         Machine Type: e2-medium
-         CPUs: 1-2 vCPU (1 shared core)
-         Memory: 4 GBs
- socialengineeringtoolkit - VM used for launching the credential harvester attack.
-         OS: Debian
-         Machine Type: e2-medium
-         CPUs: 1-2 vCPU (1 shared core)
-         Memory: 4 GBs
- targetvpc
- usermachine1 - Machine that served as victim for this simulated attack. It was used to access solomon.ruzima@cy7900team3.com emails and open the phishing email.
-         OS: Windows
-         Machine Type: e2-medium
-         CPUs: 1-2 vCPU (1 shared core)
-         Memory: 4 GBs
- linux-target - Alternate machine that lived on the same network; intended to demonstrate lateral movement after successful attack
-         OS: Debian
-         Machine Type: e2-medium
-         CPUs: 1-2 vCPU (1 shared core)
-         Memory: 4 GBs
- windowsinstance - 
-         OS: Windows
-         Machine Type: e2-medium
-         CPUs: 1-2 vCPU (1 shared core)
-         Memory: 4 GBs
- itadmin - This is the windows virtual machine which belongs to the IT Manager. In this machine is where brian.fields@cy7900team3.com email is accessed. And from this machine is where the legitimate email from IT manager was sent to the new user whose email is solomon.ruzima@cy7900team3.com
-         OS: Windows
-         Machine Type: e2-medium
-         CPUs: 1-2 vCPU (1 shared core)
-         Memory: 4 GBs
- wazuh-siem - This instance served as a Security Information and Event Management (SIEM) tool for the instances in targetvpc. It acted as a centralized log collector.
-         OS: Ubuntu
-         Machine Type: e2-medium
-         CPUs: 1-2 vCPU (1 shared core)
-         Memory: 4 GBs
- default
- emailserver - This is a the vartual machine which was used to access brian.fields@cy79ooteam3.com email. From this machine is where the phishing email was sent. It it important to note that it was set in the default vpc so that there is no way it can be tracked back to attack vpc since domains and emails leave trails of location of access.
-         OS: Windows
-         Machine Type: e2-medium
-         CPUs: 1-2 vCPU (1 shared core)
-         Memory: 4 GBs

# Included .conf files:
- Caldera
- SEToolkit
- Wazuh SIEM
- Squid proxy
- Caldera agent configuration script
