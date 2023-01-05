# good_duck
Rubber Ducky script for EDR agent automation for Wazuh.

# Introduction 📖

I created this project as part of my College Capstone, to which I wanted to use my skills in Ethical Hacking to automate the process of assigning an agent in EDRs (Wazuh) through the use of ducky scripts. The main appeal as to why create a ducky script, is that these payloads can then be loaded on a rubber ducky to then give to non-IT individuals who trust the user with handling EDR management for their endpoints. The other appeal is that any system out of the box (i.e. Windows and Linux) can then be added to the EDR manager for further threat analysis.

More ducky scripts will be put in place in this project as the need arises.

# Setup ⚙️

Most of the Setup will be based on the users experience with the different technologies in this project, as prior exprience with any of these technologies may be needed to configure the environment to their liking. I will provide links to resources that I found were helpful, but there are many different ways to setup the environment:

Wazuh:
- Initial Setup https://documentation.wazuh.com/current/quickstart.html
- Adding Wazuh Agents https://socfortress.medium.com/part-4-wazuh-agent-install-endpoint-monitoring-f24f6a0464ac
- Creating your own SOC at home series by Taylor Walton (Very detailed guide on adding what is beyond this project)

VPN (can be whichever VPN, but providing ZeroTier for reference):
- ZeroTier Setup https://www.zerotier.com/download/

CloudFlare Tunnel (another alternative instead of using VPN):
- NetworkChuck video on initial install of using CloudFlare https://www.youtube.com/watch?v=ey4u7OUAF3c&t=1s

Once the EDR is created and configured (the indexer, manager, and dashboard) and a remote means of communication is established (i.e VPN, public hosted site) we can then take advantage of the ducky script payloads.

# Running the Ducky Script 🦆

The medium in which I use for running rubber ducky's is through the flipperzero, however this can be done by any rubber ducky or badusb type of device. There are many different rubber ducky projects to look at as to which medium works best, here is an example of a cheap way to run a rubber ducky (feel free to use other mediums outside of this project as well): 
- $2 Rubber Ducky https://www.youtube.com/watch?v=uH-4btjE56E 
- $8 Rubber Ducky https://www.youtube.com/watch?v=e_f9p-_JWZw

## Steps

1. download the ducky payload for the OS you will be working in (i.e. git clone repo, download contents, copy raw contents of specific payload).
2. Modify the payload with the following changes:
	1. modify the use of the VPN that is used, with using an authorization key (preferably ephemeral) in the payload. Some examples can be found here for [ZeroTier](https://docs.zerotier.com/service/v1/#operation/updateNetwork) and [TailScale](https://tailscale.com/kb/1085/auth-keys/). Paste this oneliner in the portion labeled `VPN_CONNECT`
	2. Place the script that will be used to connect the agent to the Wazuh manager. Paste this oneliner in the portion labeled `WAZUH_CONNECT`
3. Prepare Wazuh to recieve an agent, which can be found [here](https://documentation.wazuh.com/current/installation-guide/wazuh-agent/index.html#:~:text=You%20can%20also%20deploy%20a,to%20deploy%20a%20new%20agent.) 
4. Load the ducky payload onto a USB, and connect to endpoint you would like to connect back to Wazuh for EDR management.
