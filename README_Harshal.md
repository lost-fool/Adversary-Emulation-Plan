# Wazuh
> Hello guys!
```
git init
git run
```
Try colors `#ffffff`

try links
[Github](https://pages.github.com/)

Try List
- List1
* List2
+ List3

Try Emoji 
:smiley:

Try foot notes
1st footnote[^1].
[^1]: Voila!

Try icons
[![My Skills](https://skillicons.dev/icons?i=gcp&theme=light)](https://skillicons.dev)


# Wazuh [![Wazuh Logo]( https://github.com/wazuh/wazuh-packages/blob/4.3/stack/dashboard/base/files/etc/custom_welcome/Assets/Favicons/favicon-32x32.png )](https://wazuh.com/)


A unified system for safeguarding solutions such as XDR and SIEM that cater to endpoints and workloads.
> We used it as a SIEM for our endpoints in Google Cloud Platform.

&nbsp;

## Installation guide
### Wazuh Platform
- Use wazuh installtion assistant and run it using the command below:

  ```
  curl -sO https://packages.wazuh.com/4.4/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
  ```
> Note: Copy the username and password from the console at the end of installation process.


- Alternatively you can use the below command to view the Wazuh web portal's credentials

  ```
  sudo tar -O -xvf wazuh-install-files.tar wazuh-install-files/wazuh-passwords.txt
  ```

> Note: For more information about the Wazuh installation process [Click Me]( https://documentation.wazuh.com/current/installation-guide/index.html )

&nbsp;
### Wazuh Agent Installation
For installation of wazuh agents on various operating systems [Click Me]( https://documentation.wazuh.com/current/installation-guide/wazuh-agent/index.html )

> Note: For more information about the configuration refer to the Wazuh configuration file [here]( add link for wazuh config file)

&nbsp; 


# Squid Proxy Server [![Squid Proxy Server Logo]( http://www.squid-cache.org/Artwork/SN.png )]( http://www.squid-cache.org/ )
Squid is a caching and forwarding HTTP web proxy. It has a wide variety of uses, including speeding up a web server by caching repeated requests, caching web, DNS and other computer network lookups.

&nbsp;

## Installation Guide
To install Squid proxy server on an instance in Google Cloud Platform (GCP) follow the steps mentioned in the link [here]( https://cloud.google.com/vpc/docs/special-configurations ).

> Note: You will have to configure firewall rule in GCP to allow tcp traffic on port 3128
> For more information about the common Squid proxy configurations

&nbsp;

## Squid Proxy Configurations on Virtual Instances in GCP Guide
As per the project\'s requirements following changes were adopted:

### Configure Linux Based Instances to Use the Squid Proxy Server
- Edit \'_environment_\' file in etc either as a root user or using \'sudo\' as shown below:

```
nano /etc/environment
http_proxy=http://<squid-proxy-ip>:3128/
https_proxy=http://<squid-proxy-ip>:3128/
ftp_proxy=http://<squid-proxy-ip>:3128/
export no_proxy=169.254.169.254,metadata,metadata.google.internal
```
> Note: Standard Squid proxy port is 3128.

  - Lastly run the following command in the terminal:
  ```
  source /etc/environment
  ```
  
- Configure \'_curl_\' using a text editor of your choice using the below commands:

  ```
  touch ~/.curlrc
  nano ~/.curlrc
  ```
  - Edit and add the below line to the \'_.curlrc_\' file
  ```
  proxy=http://<squid-proxy-ip>:proxy-port/
  ```
  
- Configure \'_apt_\' to use Squid proxy server using a text editor of your choice:
  ```
  nano /etc/apt/apt.conf
  ```
  - Add the below lines to the *_apt.conf_* file:
    ```
    Acquire::http::Proxy "http://<squid-proxy-ip>:3128/";
    Acquire::https::Proxy "http://<squid-proxy-ip>:3128/";
    Acquire::ftp::Proxy "http://<squid-proxy-ip>:3128/";
    ```

### Configure Windows Based Instances to Use the Squid Proxy Server
Follow the steps mentioned in the link [here]( https://www.anoopcnair.com/how-to-configure-proxy-settings-in-windows-11/ )


Add below section to the Network Architecture Section

### proxy-server
This instance served as a proxy server to all the instances in both _targetvpc_ and _attackvpc_
  - OS: debian-11-bullseye-v20230206
  - Machine Type: e2-medium
  - CPUs: 1-2vCPU (1 shared core)
  - Memory: 4GB
  - Architecture: x86

### wazuh-siem
This instance served as a Security Information and Event Management (SIEM) tool for the instances in _targetvpc_. It acted as a centralized log collector.
  - OS: ubuntu-1804-bionic-v20230215
  - Machine Type: e2-medium
  - CPUs: 1-2vCPU (1 shared core)
  - Memory: 4GB
  - Architecture: x86


