---
title:  "Clutch and Dumpdecrypted Usage"
date:   2018-03-29 19:00:33 +0800
categories: Mobile Programming
classes:
  - landing
header:
  teaser: /assets/img/frida.png
---


Clutch Usage
	•	Dump the installed app
```
	Clutch -i
```
	•	Dump app with number
```
	Clutch -d 63
```

dumpdecrypted Usage
	•	Check the process Id
```
	ps -e | grep Aplipay
```
	•	Use cycript check app documents directory
```
	cycript -p 10854
	[[NSFileManager defaultManager] URLsForDirectory:NSDocumentDirectory
                                              inDomains:NSUserDomainMask][0]

	#"file:///var/mobile/Containers/Data/Application/DB840722-C37B-47F7-AAAB-E3C4C7616220/Documents/"
```
	•	将dumpdecrypted.dylib拷贝到documents目录，可以使用scp命令或者iFunbox工具
```
	scp dumpdecrypted.dylib root@ip: /var/mobile/Containers/Data/Application/371430E9-C2EE-4888-849C-6A51CF32867C/Documents/

	cd /var/mobile/Containers/Data/Application/DB840722-C37B-47F7-AAAB-E3C4C7616220/Documents/
	put dumpdecrypted.dylib
```
	•	cd到documents目录执行, 切换到mobile用户
```
	su mobile
	cd /var/mobile/Containers/Data/Application/DB840722-C37B-47F7-AAAB-E3C4C7616220/Documents/
	DYLD_INSERT_LIBRARIES=dumpdecrypted.dylib /var/containers/Bundle/Application/0C32538D-939A-4E15-9509-04AC67A290FD/yweather.app/yweather
```
	使用class dump就可以dump出来class了
```
	class-dump -S -s -H weather.decrypted -o /to/dir
```
