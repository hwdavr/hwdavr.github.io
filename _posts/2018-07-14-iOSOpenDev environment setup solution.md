---
title:  "iOSOpenDev environment setup solution"
date:   2018-07-14 16:10:33 +0800
categories: MoblieSecurity
classes:
  - landing
header:
  teaser: /assets/img/frida.png
---


## The step of setup basically can follow the article below
<https://github.com/535064094/iosOpenDevInstallTools/wiki/iOSOpenDev-install-solution>

The only issue is to build ldid, you will encounter an error below,
```
ld: library not found for -lcrypto
```

Instead of using official release of ldid, you can use the unofficial release from below github repo,
https://github.com/xerub/ldid

May after that you will still have issue while installing iOSOpenDev.
Suggest to use [MonkeyDev](http://www.alonemonkey.com/2017/06/28/monkeydev/) instead.
