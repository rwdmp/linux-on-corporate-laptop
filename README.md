# linux-on-corporate-laptop
A small summary of how to configure your corporate laptop to run Ubuntu


# Step 1: Install Linux Subystem (WSL) 
Typicalyl requires a user with local admin rights, but no domain updates. 

Option 1:
Start > Run : appwiz.cpl    // Select "Linux Subsystem for Windows"

Option 2:
Powershell : Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux

# Step 2: Install your favorite distro
Typically the windows store is blocked. So you can install Ubuntu using powershell

Powershell: WSL --install -d Ubuntu-20-04
Powershell: WSL --instalö -d kali-linux

# Step 3: Enable the firewall
Typically, any application you use needs to auth with your corporate firewall and/or proxy server in order to access the internet.

Step 3.1 : General Proxy
Bash: sudo nano ~/.bashrc
// Export HTTP_PROXY=USER:PASS@proxy.am-gruppe.de:8080
// Export HTTPS_PROXY=USER :PASS@proxy.am-gruppe.de:8080

Step 3.2 : Enable apt

sudo nano /etc/apt/apt.conf
// Acquire::http::Proxy "http://[username]:[password]@ [proxy-web-or-IP-address]:[port-number]";
// Acquire::https::Proxy "http://[username]:[password]@ [proxy-web-or-IP-address]:[port-number]";

Step 3.3 : Enable weget

sudo nano ~/,wgetrc 

https_proxy=SERVER:PORT
ftp_proxy=ftp://SERVER
http_proxy=http://SERVER

# Step 4: To be realyl cool, you also want to install the Windows Terminal 

Get the portable C++ Runtime
https://docs.microsoft.com/en-us/troubleshoot/developer/visualstudio/cpp/libraries/c-runtime-packages-desktop-bridge?msclkid=3e1dd82aac8b11ec8f9dbd86d5979ca8#how-to-install-and-update-desktop-framework-packages

Then download the installer for terminal from Github
https://github.com/Microsoft/Terminal#installing-and-running-windows-terminal

Now you can move into powershell by typing PS, move into linux by typing Bash and windows command by typing CMD and enter Exit to get back to main mode.

