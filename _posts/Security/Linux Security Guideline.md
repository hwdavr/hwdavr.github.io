---


---

<h2 id="minimize-software-and-services">Minimize Software and Services</h2>
<p>If you don’t need a piece of software, don’t install it.<br>
If you don’t need a service, don’t start it.<br>
If you no longer need the software or service, stop and uninstall it.</p>
<h2 id="run-services-on-separate-systems">Run Services on Separate Systems</h2>
<p>Minimizes the risk of one compromised service leading to other compromised services.</p>
<h2 id="encypt-data-transmissions">Encypt Data Transmissions</h2>
<p>FTP-&gt;SFTP<br>
telnet-&gt;SSH<br>
SNMP v1/2-&gt;V3<br>
HTTP-&gt;HTTPs</p>
<h2 id="avoid-shared-accounts">Avoid shared Accounts</h2>
<h2 id="avoid-direct-root-logins">Avoid Direct root Logins</h2>
<p>Do not allow direct login of shared accounts.<br>
Users must login to their personal accounts and then switch to the shared account.<br>
Control and monitor access with sudo.</p>
<h2 id="user-multifactor-authentication">User Multifactor Authentication</h2>
<p>Something you know + something you have or something you are.<br>
Examples:<br>
password + OTP<br>
password + fingerprint</p>
<h2 id="the-principle-of-least-privilege">The Principle of Least Privilege</h2>
<p>Only use root privileges when required.<br>
Avoid running services as the root user.<br>
Use restrictive permission that allow people and services enough access to do their jobs.</p>
<h2 id="monitor-system-activity">Monitor System Activity</h2>
<p>Routinely review logs.<br>
<strong>Send logs to a central logging system.</strong></p>
<h2 id="user-a-firewall">User a firewall</h2>
<p>Netfilters + iptables.<br>
Only allow network connections from desired sources.</p>
<h2 id="encrypt-your-data">Encrypt your data</h2>
<p>Encrypt data on disk</p>

