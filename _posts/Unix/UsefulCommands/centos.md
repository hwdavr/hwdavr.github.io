---


---

<h2 id="setup-network-in-virtualbox">Setup Network in Virtualbox</h2>
<h3 id="start-internet-connect">start internet connect</h3>
<p>sudo dhclient</p>
<h3 id="check-ip-address">check ip address</h3>
<p>ip addr show</p>
<h2 id="openjdk">OpenJDK</h2>
<h3 id="enable-unlimited-policy">Enable unlimited policy</h3>
<p>Add below line in java.security file:<br>
crypto.policy=unlimited<br>
<a href="https://stackoverflow.com/questions/31971499/ecdhe-cipher-suites-not-supported-on-openjdk-8-installed-on-ec2-linux-machine">https://stackoverflow.com/questions/31971499/ecdhe-cipher-suites-not-supported-on-openjdk-8-installed-on-ec2-linux-machine</a></p>
<h1 id="ec2">EC2</h1>
<p>Switch to root<br>
sudo su</p>

