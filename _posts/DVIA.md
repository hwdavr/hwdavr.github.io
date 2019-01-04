---


---

<h2 id="part-2">Part 2:</h2>
<p>Installed Application directory:<br>
/var/containers/Bundle/Application</p>
<p>Use below command can check all the folder and subfolder content:<br>
<code>ls -l *</code></p>
<h3 id="dump-class-usage">Dump class Usage</h3>
<pre><code>•	Dump the classes to a file:
class-dump Maps &gt; class-info-Maps

•	Get the file from devices:
$ sftp root@192.168.0.103
&gt; get /Applications/Maps.app/class-info-Maps
</code></pre>
<h3 id="clutch-usage">Clutch Usage</h3>
<pre><code>•	Dump the installed app
Clutch -i
•	Dump app with number
Clutch -d 63
</code></pre>
<h3 id="dumpdecrypted-usage">dumpdecrypted Usage</h3>
<pre><code>•	Check the process Id
ps -e | grep Aplipay
•	使用cycript查看documents目录
cycript -p 10854
[[NSFileManager defaultManager] URLsForDirectory:NSDocumentDirectory
                                          inDomains:NSUserDomainMask][0]

#"file:///var/mobile/Containers/Data/Application/DB840722-C37B-47F7-AAAB-E3C4C7616220/Documents/"

•	将dumpdecrypted.dylib拷贝到documents目录，可以使用scp命令或者iFunbox工具
scp dumpdecrypted.dylib root@ip: /var/mobile/Containers/Data/Application/371430E9-C2EE-4888-849C-6A51CF32867C/Documents/

cd /var/mobile/Containers/Data/Application/DB840722-C37B-47F7-AAAB-E3C4C7616220/Documents/
put dumpdecrypted.dylib

•	cd到documents目录执行, 切换到mobile用户
su mobile
cd /var/mobile/Containers/Data/Application/DB840722-C37B-47F7-AAAB-E3C4C7616220/Documents/
•	DYLD_INSERT_LIBRARIES=dumpdecrypted.dylib /var/containers/Bundle/Application/0C32538D-939A-4E15-9509-04AC67A290FD/yweather.app/yweather
使用class dump就可以dump出来class了
class-dump -S -s -H weather.decrypted -o /to/dir

•	The location of the application bundle
ps -e
/var/containers/Bundle/Application/DE1FAFD1-B2D9-48F5-A980-004242DC2FC5/AlipayWallet.app/AlipayWallet

•	The location of the application data
/var/mobile/Containers/Data/Application

•	All System frameworks are merged into one large file
/System/Library/Caches/com.apple.dyld
</code></pre>
<h2 id="part-3">Part 3:</h2>
<p>List all the contains of the folders in current directory:<br>
ls *</p>
<p>GNU Debugger (gdb) is used to analyze the run time behavior of an iOS application. In recent iOS versions, GNU Debugger directly downloaded from the Cydia is broken and not functioning properly. Following the Pod 2g blog post also did not help me.<br>
To get rid of this problem, add <a href="http://cydia.radare.org">http://cydia.radare.org</a> to cydia source and download the latest GNU Debugger (build 1708). GDB build 1708 is working for iOS 5.x.</p>
<h2 id="part-4">Part 4:</h2>
<p>How to use dpkg to install app:</p>
<ol>
<li>Use sftp to upload the deb file to device<br>
put iNalyzer_5.5b.deb</li>
<li>Use dpkg to install<br>
dpkg -i iNalyzer_5.5b.deb</li>
</ol>
<h2 id="part-15-inalyzer">Part 15: iNalyzer</h2>
<ol>
<li>Create decrypted IPA file<br>
<code>./iNalyzer ipa bundleUUID</code></li>
<li></li>
</ol>
<h2 id="part-23">Part 23</h2>
<h3 id="debug-check">Debug check:</h3>
<p>Method 1:<br>
<a href="https://github.com/x128/MemeCollector/blob/master/Meme%20Collector/NSObject%2BdebugCheck.h">https://github.com/x128/MemeCollector/blob/master/Meme Collector/NSObject%2BdebugCheck.h</a></p>
<pre class=" language-c"><code class="prism  language-c">SEC_IS_BEING_DEBUGGED_RETURN_NIL
</code></pre>
<p>Method 2:</p>
<pre class=" language-c"><code class="prism  language-c"><span class="token macro property">#<span class="token directive keyword">ifndef</span> DEBUG</span>
    <span class="token function">ptrace</span><span class="token punctuation">(</span>PT_DENY_ATTACH<span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">,</span> <span class="token number">0</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token macro property">#<span class="token directive keyword">endif</span></span>
</code></pre>
<h3 id="false-methods">False Methods</h3>
<p>you can add false methods (Dead method) in your application, something that would get the attention of a hacker. For e.g a method with the name <em>userDidLogin:(BOOL)didLogin;</em> will surely attrack the attacker’s attention. Ofcourse, he will try to execute it using Cycript. In this method’s implementation, you can clear all the important information in the app, and maybe even report to the server that this application is being breaked into.</p>
<h2 id="part-24">Part 24</h2>
<p>Jailbreak Detection implementation:<br>
<a href="http://highaltitudehacks.com/2013/12/17/ios-application-security-part-24-jailbreak-detection-and-evasion/">http://highaltitudehacks.com/2013/12/17/ios-application-security-part-24-jailbreak-detection-and-evasion/</a></p>
<h2 id="part-25">Part 25</h2>
<p>Safe Programming:<br>
<a href="http://highaltitudehacks.com/2013/12/17/ios-application-security-part-25-secure-coding-practices-for-ios-development/">http://highaltitudehacks.com/2013/12/17/ios-application-security-part-25-secure-coding-practices-for-ios-development/</a></p>

