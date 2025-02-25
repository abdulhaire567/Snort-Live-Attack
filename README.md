# Snort-Live-Attack
This is a live network attack project I did on TryHackMe. Its's a live simulation project where I was asked as a SOC Analyst to stop a live brute force attack with SNORT. As a SOC Analyst you don't jump into conclusions, you investigate first. But I think a possible port that will be targeted will be port 22(SSH) as brute force attack is the attempt to remotely  trying to login into the machine with random passwords hoping one works. Possible through port 22

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
I started Snort in packet logger mode and try to figure out the attack source, service and port. The packets will be saved in a log file so we can use it to read the packets <br/>
<img src="https://i.imgur.com/IVKg5DB.png" height="80%" width="80%"/>
<br />
<br />

I have a log file from the previous command to capture the packets going on in and out the network. I am going to use the command sudo snort -r snort.log.<number> -X to read and analyze the packets we captured and hope to find where our network attack happened. -X so I can read the packets in full to be able to analyze them better <br/>
<img src="https://i.imgur.com/nKz6qMp.png" height="80%" width="80%"/>
<br />
<br />

Going through the packets I noticed a chunk of packets coming from the IP adress 10.10.245.36 port 46684 to our machine to port 22 which is the SSH port. This tells me a connection was attempted. Most likely a remote connection attempt. <br/>
<img src="https://imgur.com/vpgskbR.png" height="80%" width="80%" />
<br />
<br />

After I found the source of our attack, I have to create a rule to alert us whenever a similar connection attempt is made by our attacker. To make this rule, I will navigate to our local rules /etc/snort/rules/local.rules. After creating this rule I will automatically get alerts when the attacker suspicious IP attempts to connect  <br/>
<img src="https://i.imgur.com/YLo4rBM.png" height="80%" width="80%" />
<br />
<br />

Now I will test my new rule in console mode which provides fast style alerts on the console screen. I want to see if i will recieve our alerts whenever theres an attempt. After testing it out and it successfully worked, now it is time to put it into action. Now I can run snort with the -A full option, which adds the printing of full alert information, as suggested in the task <br/>
<img src="https://i.imgur.com/UiHRhF1.png" height="80%" width="80%"/>
<br />
<br />

After putting it into action, I successfully was able to stop the attack. As you can see at the top right corner, it says that I have successfully been able to stop the attack  <br/>
<img src="https://i.imgur.com/CQ8yguw.png" height="80%" width="80%" />
<br />
<br />

</p>
