---


---

<p>EC2 Application deployment<br>
Install MySQL:<br>
sudo yum install mysql55-server</p>
<pre><code>sudo service mysqld start
</code></pre>
<pre><code>sudo mysql_secure_installation
</code></pre>
<pre><code>sudo chkconfig mysqld on
</code></pre>
<p>Deploy at localhost:<br>
ssh -i “topnews.pem” <a href="mailto:ec2-user@ec2-52-192-114-237.ap-northeast-1.compute.amazonaws.com">ec2-user@ec2-52-192-114-237.ap-northeast-1.compute.amazonaws.com</a></p>
<p>Deployment at EC2 machine:<br>
cd /Users/admin/.ec2<br>
cp -f ~/Study/android/AndroidApp/webserver/topnewsweb/topnewsbackend/topnews.war ~/.ec2/war/topnews.war</p>
<p>scp -i “topnews.pem” war/topnews.war <a href="mailto:ec2-user@ec2-52-192-114-237.ap-northeast-1.compute.amazonaws.com">ec2-user@ec2-52-192-114-237.ap-northeast-1.compute.amazonaws.com</a>:~/</p>
<p>sudo cp -f topnews.war /usr/share/tomcat7/webapps/</p>
<p>cd /usr/share/tomcat7/webapps/</p>
<p>sudo service tomcat7 restart</p>

