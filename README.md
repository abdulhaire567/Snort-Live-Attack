# Snort-Live-Attack
This project involves a live network attack simulation on TryHackMe. In this scenario, I acted as a SOC Analyst tasked with stopping a live brute force attack using SNORT. As a SOC Analyst, it's crucial to investigate thoroughly before making any conclusions. Given the nature of brute force attacks, which involve attempting to remotely log into a machine using random passwords, I anticipated that port 22 (SSH) would likely be targeted.
<h2>Utilities and Tools Used</h2>

- <b>Terminal</b> 
- <b>Snort</b>

<h2>Environments Used </h2>

- <b>Linux</b>

<h2>Attack Scenario</h2>
<img src="https://i.imgur.com/x5KqbON.png" height="80%" width="80%" />
<br />
<br />


<h2>Stopping the Attack</h2>

<p align="center">
I initiated Snort in packet logger mode to identify the source, service, and port associated with the attack. The captured packets will be stored in a log file, allowing for further analysis to determine the attacker's origin and method. <br/>
<img src="https://i.imgur.com/IVKg5DB.png" height="80%" width="80%"/>
<br />
<br />

I have a log file from the previous command to capture the packets going on in and out the network. I am going to use the command sudo snort -r snort.log.<number> -X to read and analyze the packets we captured and hope to find where our network attack happened. -X so I can read the packets in full to be able to analyze them better <br/>
<img src="https://i.imgur.com/nKz6qMp.png" height="80%" width="80%"/>
<br />
<br />

While analyzing the packet data, I observed a significant number of packets originating from IP address 10.10.245.36, specifically from port 46684, targeting our machine on port 22, which is designated for SSH. This indicates that a connection attempt was made, most likely an unauthorized remote access attempt. <br/>
<img src="https://imgur.com/vpgskbR.png" height="80%" width="80%" />
<br />
<br />

After identifying the source of the attack, I need to create a rule that will generate alerts whenever a similar connection attempt is made by the attacker. To do this, I will navigate to our local rules file at /etc/snort/rules/local.rules. Once the rule is created, I will automatically receive alerts whenever the attacker's suspicious IP attempts to connect.  <br/>
<img src="https://i.imgur.com/YLo4rBM.png" height="80%" width="80%" />
<br />
<br />

I will now test my new rule in console mode, which displays real-time alerts directly on the console screen. My objective is to verify whether I receive alerts whenever an attempt is detected. After conducting the test successfully, it is time to implement the rule in practice. I can now run Snort with the -A full option, enabling the display of comprehensive alert information, as outlined in the task requirements. <br/>
<img src="https://i.imgur.com/UiHRhF1.png" height="80%" width="80%"/>
<br />
<br />

After implementing the rule, I successfully mitigated the attack. As indicated in the top right corner, the system confirms that the attack has been successfully stopped.  <br/>
<img src="https://i.imgur.com/CQ8yguw.png" height="80%" width="80%" />
<br />
<br />

</p>
