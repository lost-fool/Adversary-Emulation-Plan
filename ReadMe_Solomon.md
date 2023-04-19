# Caldera 
Caldera refers to an open-source framework used for automated adversary emulation, which is also commonly known as Red Teaming or Penetration Testing. This tool is designed to enable users to simulate real-world attacks, test the security defenses of a network or system, and provide a detailed report of the results.
    
  Caldera-srv 
    This is the virtual machine in the attack vpc on which the caldera tool is installed and run. The server has two network interfaces one is internal and the other external.
 Specifications
   * OS: Debian Linux
   * Machine Type: e2-standard-2
   * CPUs: 2 vCPU
   * Memory: 8 GBs
    
 Caldera-client
 Specifications
  This is the virtual machine in the attack vpc that is used to access the caldera services. The caldera tool GUI is accessed via the web.
  * OS: Windows server 2022
  * Machine Type: e2-medium
  * CPUs: 1-2 vCPU (1 shared core)
  * Memory: 4 GBs
  
Caldera Resources used
* https://github.com/mitre/caldera
* https://caldera.readthedocs.io/en/latest/
* https://www.youtube.com/watch?v=EIHLXWnK1Dw

Web Domains w/ Email Accounts
  - Two domains were registered on godaddy one being cy7900team.com and another being cy79ooteam3.com.
  - Three email addresses were added to the domains solomon.ruzima@cy7900team3.com, brian.fields@cy7900team3.com and brianfields@cy79ooteam3.com.


itadmin
This is the windows virtual machine which belongs to the IT Manager. In this machine is where brian.fields@cy7900team3.com email is accessed. And from this machine is where the legitimate email from IT manager was sent to the new user whose email is solomon.ruzima@cy7900team3.com
Specifications
  * OS: Windows server 2022
  * Machine Type: e2-medium
  * CPUs: 1-2 vCPU (1 shared core)
  * Memory: 4 GBs
