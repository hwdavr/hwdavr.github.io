---


---

<p>Crypto in right way:<br>
<a href="http://www.daemonology.net/blog/2009-06-11-cryptographic-right-answers.html">http://www.daemonology.net/blog/2009-06-11-cryptographic-right-answers.html</a></p>
<p><a href="https://wiki.sei.cmu.edu/confluence/collector/pages.action?key=c">https://wiki.sei.cmu.edu/confluence/collector/pages.action?key=c</a></p>
<p>Code Review<br>
22. Project Setting: strip, fJava:</p>
<ol>
<li>String is not safe, use byte[] or char</li>
<li>Use reflection to use important API and System API and use string obfuscation on the reflection string.</li>
<li>Certificate pinning also can avoid someone use BurpSuite to inject the fake certificate to the device.</li>
<li>For public APIC, finiline-function.</li>
<li>Memory: overflow, override</li>
<li>Code hardening:<br>
avoid unsecure system api,<br>
no meaningful name for security related code<br>
No cache for sensitive data<br>
Secure random number<br>
Use keychain for sensitive data, and use access controlput the implementation in another private method, so dexguard can obfuscate the name.</li>
</ol>
<p>C:<br>
5. Remove sensitive data after usage, set all 0 or random.<br>
6. Prevent memory leakage</p>
<ul>
<li>Put string buffer array to the last element of structure, even it overflow, it will not destroy the other data.</li>
</ul>
<ol start="7">
<li>Avoid to use memcpy… or strcpy… kinds of function, try to implement.</li>
<li>Use safe snprint, strlcat,  strncat, strnstr.</li>
<li>Use static <strong>attribute</strong>((always_inline)) as much as possible</li>
<li>strip as much symbol as possible</li>
<li>Use internal syscal</li>
<li>Use static inline function instead of macro like function</li>
</ol>
<p>iOS<br>
13. Don’t use NSString and NSData for sensitive data<br>
14. Don’t use HTTPs with cache.<br>
15. Remove keypad cache data<br>
16. If using static framework, use Reallocated Object File, it will compiled into one object file instead of separated object file, and duplicated variables will be stripped.<br>
17. strip<br>
Development Postprocesssing = YES<br>
Static framework = Non-global Symbols<br>
dynamic framework = Non-global Symbols or All Symbols<br>
App = All Symbols<br>
18. UITextview for password:</p>
<pre><code>textFieldSecure.secureTextEntry = YES;
</code></pre>
<p>And don’t use auto correction, because keyboard will keep the stroke data in one file for auto correction<br>
19. Validate the URL schema source and parameters.<br>
20. Use NSSecureCoding for NSKeyedUnarchiver.<br>
21.</p>

