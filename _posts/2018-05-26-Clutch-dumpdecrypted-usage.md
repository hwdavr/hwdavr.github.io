---
title:  "Clutch and Dumpdecrypted Usage"
date:   2018-03-29 19:00:33 +0800
categories: Mobile Programming
classes:
  - landing
header:
  teaser: /assets/img/frida.png
---


### Clutch Usage
Dump the installed app
```
Clutch -i
```
Dump app with number
```
Clutch -d 63
```

### dumpdecrypted Usage
Check the process Id
```
ps -e | grep Aplipay
```
Use cycript check app documents directory
```
cycript -p 10854
[[NSFileManager defaultManager] URLsForDirectory:NSDocumentDirectory
                                              inDomains:NSUserDomainMask][0]

#"file:///var/mobile/Containers/Data/Application/DB840722-C37B-47F7-AAAB-E3C4C7616220/Documents/"
```
Copy dumpdecrypted.dylib to documents directory，you can use scp command or use iFunbox tool
```
scp dumpdecrypted.dylib root@ip: /var/mobile/Containers/Data/Application/371430E9-C2EE-4888-849C-6A51CF32867C/Documents/

cd /var/mobile/Containers/Data/Application/DB840722-C37B-47F7-AAAB-E3C4C7616220/Documents/
put dumpdecrypted.dylib
```
Switch to mobile user, go to documents directory and execute
```
su mobile
cd /var/mobile/Containers/Data/Application/DB840722-C37B-47F7-AAAB-E3C4C7616220/Documents/
DYLD_INSERT_LIBRARIES=dumpdecrypted.dylib /var/containers/Bundle/Application/0C32538D-939A-4E15-9509-04AC67A290FD/yweather.app/yweather
```
Now you can use class-dump to dump the classes
```
class-dump -S -s -H weather.decrypted -o /to/dir
```
