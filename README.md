# Adversary-Emulation-Plan

- Introduction
-   Team Members
-   Description of project
-   Purpose of the attack
- Tools/Applications
-     Caldera
-       (what did this tool do?)
-     Wazuh
-     Squid
-     Social Engineering Toolkit
-     Web Domains w/ Email Accounts
- Network Architecture Picture(s)
-   <img width="591" alt="Screen Shot 2023-04-17 at 9 58 30 PM" src="https://user-images.githubusercontent.com/84095697/232651827-8dfe4dc1-98b7-4840-9022-4884f607e3bd.png">

- Network Architecture Description
-   Firewall Rules
-     Should be in a separate config file (insert filename here)

-  Attackvpc
-     Caldera-srv - description of the VM
-         OS
-         CPUs
-         Memory
-     Caldera-client
-         OS
-         CPUs
-         Memory
-     proxy-server
-         OS
-         CPUs
-         Memory
-     socialengineeringtoolkit
-         OS
-         CPUs
-         Memory
-  targetvpc
-     usermachine1 - Machine that served as victim for this simulated attack
-         OS
-         CPUs
-         Memory
-     linux-target - Alternate machine that lived on the same network; intended to demonstrate lateral movement after successful attack
-         OS
-         CPUs
-         Memory
-     windowsinstance
-         OS
-         CPUs
-         Memory
-     itadmin
-         OS
-         CPUs
-         Memory
-     wazuh-siem
-         OS
-         CPUs
-         Memory
-  default
-     emailserver - 
-         OS
-         CPUs
-         Memory

Included .conf files:
- 

-Tools configuration info
