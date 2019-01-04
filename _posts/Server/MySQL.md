---


---

<p>6212251813001900643<br>
Mac OS install MySQL:<br>
Mysql:<br>
azlg?mk)L6kZ</p>
<p><a href="https://dev.mysql.com/doc/refman/5.6/en/osx-installation-pkg.html">https://dev.mysql.com/doc/refman/5.6/en/osx-installation-pkg.html</a><a href="http://stackoverflow.com/questions/6474775/setting-the-mysql-root-user-password-on-os-x">http://stackoverflow.com/questions/6474775/setting-the-mysql-root-user-password-on-os-x</a></p>
<p>sudo mysqld_safe --skip-grant-tables</p>
<p>SET PASSWORD = PASSWORD(‘your_new_password’);</p>
<p><a href="http://community.jaspersoft.com/wiki/uninstall-mysql-mac-os-x">http://community.jaspersoft.com/wiki/uninstall-mysql-mac-os-x</a><br>
<a href="http://dev.mysql.com/doc/mysql-getting-started/en/">http://dev.mysql.com/doc/mysql-getting-started/en/</a><a href="http://stackoverflow.com/questions/21177562/installing-mysql-workbench-but-file-etc-my-cnf-doesnt-exist">http://stackoverflow.com/questions/21177562/installing-mysql-workbench-but-file-etc-my-cnf-doesnt-exist</a></p>
<p>MySQL index</p>
<p><a href="http://talentluke.iteye.com/blog/1843868">http://talentluke.iteye.com/blog/1843868</a></p>
<p><a href="http://imfei.blog.51cto.com/1849649/511689/">http://imfei.blog.51cto.com/1849649/511689/</a></p>
<p><a href="https://www.kancloud.cn/thinkphp/mysql-design-optimalize/39319">https://www.kancloud.cn/thinkphp/mysql-design-optimalize/39319</a></p>
<p>MQTT:</p>
<p>Server logging:</p>
<p>Topic: log/${client_id}</p>
<p>Device -&gt;Clients</p>
<p>Device pub, Clients sub:</p>
<p>Topic: evt/${client_id}</p>
<p>Clients-&gt;Device</p>
<p>Clients pub, Device sub:</p>
<p>Topic: cmd/${client_id}</p>
<p>MySQL run out of memory issue:</p>
<p><a href="http://stackoverflow.com/questions/25965638/mysql-fatal-error-cannot-allocate-memory-for-the-buffer-pool/32932601">http://stackoverflow.com/questions/25965638/mysql-fatal-error-cannot-allocate-memory-for-the-buffer-pool/32932601</a></p>
<p>Change the swap size:</p>
<p><a href="https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04">https://www.digitalocean.com/community/tutorials/how-to-add-swap-on-ubuntu-14-04</a></p>
<p>MySQL delete:</p>
<p>delete FROM test.topnewslist where datediff(NOW(), timestamp) &gt; 30 order by timestamp desc;</p>

