---
title:  "How to resolve Tomcat Error - java.lang.OutOfMemoryError: PermGen in Amazon Linux AMI"
date:   2018-03-29 19:00:33 +0800
categories: Server&Cloud
classes:
  - landing
header:
  teaser: /assets/img/tomcat.png
---

Tomcat web server often suffers from java.lang.OutOfMemoryError: PermGen space whenever you deploy and un-deploy your web application couple of time. 
In this article, we will see how to fix java.lang.OutOfMemoryError: PermGen Space in tomcat server.

1. Goto Tomcat startup script file location, for Amazon Linux AMI. It locates at "/etc/rc.d/init.d/"

2. Edit the script file by "sudo nano tomcat7"

3. Add the following JAVA_OPTS at the beginning of the file after "NAME="$(basename $0)""
export JAVA_OPTS="-Xms1024m -Xmx10246m -XX:NewSize=256m -XX:MaxNewSize=356m -XX:PermSize=256m -XX:MaxPermSize=356m"

You can change the actual heap size and PermGen Space as per your requirement.

4. Restart Tomcat.
Increasing PermGen space can prevent java.lang.OutOfMemoryError: PermGen in tomcat only for some time and it will eventually occur based on how many times you redeploy your web application, its best to find the offending class which is causing a memory leak in tomcat and fix it.
