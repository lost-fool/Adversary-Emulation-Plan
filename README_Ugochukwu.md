# Social Engineering Toolkit 
The Social Engineering Toolkit is an open-source penetration testing framework designed for social engineering. SET has many custom attack vectors that allow a user to make a believable attack quickly. SET offers multiple attack vectors and techniques and below are some of the common attacks used on the kit
    * Phishing attacks
    * Web attacks
    * Infectious Media Generator
    * Create a Payload and Listener
    * Mass Mailer Attack
    
 # Installation
Installing the Social Engineering Toolkit is a pretty straightforward process with most operating systems. On most Linux distros the manual installation can be performed by using the following commands

git clone https://github.com/trustedsec/social-engineer-toolkit/ set/
cd set
pip install -r requirements.txt

# Specifications
Below are the specifications of the system used for the installation of the SET
    * OS: Debian Linux
    * Machine Type: e2-standard-2
    * CPUs: 2 vCPU
    * Memory: 10 GB
    
# Credential Harvester
For this project, the attack used is the credential harvester method. Credential harvester method is used when a user doesn't want to specifically get a shell but perform phishing attacks to obtain usernames and passwords from the system. In this attack vector, a website will be cloned, and when the victim enters the user credentials, the usernames and passwords will be posted back to the attacker's machine. After that, the victim will be redirected back to the legitimate site.

#Attack Procedure
The procedure for launching the credential harvester attack is given as follows:
    * Run “sudo setoolkit”
    * Select "Social-Engineering Attacks"
    * Select "Website Attack Vectors"
    * Select "Credential Harvester Attack Method"
    * Select "Web Templates"
    * Type in your IP address
    * Select "Twitter"
    * Open Kali Linux IP address in a browser
The victim will then proceed to input their username and password. The credentials are captured and displayed in SET
