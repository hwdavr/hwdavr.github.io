---


---

<p><a href="https://wiki.sei.cmu.edu/confluence/display/java/SEI+CERT+Oracle+Coding+Standard+for+Java">https://wiki.sei.cmu.edu/confluence/display/java/SEI+CERT+Oracle+Coding+Standard+for+Java</a></p>
<p>Java:</p>
<ol>
<li>String is not safe, use byte[] or char</li>
<li>Use reflection to use important API and System API and use string obfuscation on the reflection string.</li>
<li>Certificate pinning also can avoid someone use BurpSuite to inject the fake certificate to the device.</li>
<li>For public API, put the implementation in another private method, so dexguard can obfuscate the name.</li>
<li></li>
</ol>
<h2 id="sei-rules">SEI Rules:</h2>
<ul>
<li><a href="https://wiki.sei.cmu.edu/confluence/display/java/ERR01-J.+Do+not+allow+exceptions+to+expose+sensitive+information">ERR01-J. Do not allow exceptions to expose sensitive information</a><br>
All exceptions reveal information that can assist an attacker’s efforts to carry out a <a href="https://wiki.sei.cmu.edu/confluence/display/java/Rule+BB.+Glossary#RuleBB.Glossary-denial-of-serv">denial of service</a> (DoS) against the system.<br>
Some Server developers will throw the exception message and return to client, which is not a good practice. Attacker can use this message to carry out a DoS.<br>
-Use</li>
</ul>

