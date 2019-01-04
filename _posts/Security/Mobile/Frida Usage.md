---


---

<h1 id="frida-usage">Frida usage:</h1>
<h2 id="android">Android</h2>
<h3 id="make-sure-mode-is-permissive">make sure mode is Permissive</h3>
<p>setenforce 0</p>
<h3 id="must-run-the-server-in-root-user-first-then-start-the-server-in-separated-commands">Must run the server in root user first, then start the server in separated commands:</h3>
<p>$ su<br>
$ ./frida-server &amp;<br>
$./data/local/tmp/frida-server &amp;</p>
<p>cannot run in one command, $ su ./frida-server &amp;</p>
<p>adb forward tcp:13236 tcp:13236</p>
<h2 id="to">To</h2>
<p>setenforce 0<br>
make sure mode is Permissive</p>
<p>IOS:</p>
<p>$ ssh root@your-iphone<br>
$ frida-server &amp;</p>

