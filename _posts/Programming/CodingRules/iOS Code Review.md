---


---

<p>Code Review:</p>
<h2 id="coding">Coding</h2>
<ol>
<li>Don’t use NSString and NSData for sensitive data</li>
<li>Don’t use HTTPs with cache.</li>
<li>Remove keypad cache data</li>
<li>UITextview for password:</li>
</ol>
<pre><code>textFieldSecure.secureTextEntry = YES;
</code></pre>
<p>And don’t use auto correction, because keyboard will keep the stroke data in one file for auto correction<br>
5. Validate the URL schema source and parameters.<br>
6. Use NSSecureCoding for NSKeyedUnarchiver.</p>
<h2 id="project-setting">Project Setting</h2>
<ol>
<li>
<p>Static framework<br>
If using static framework, use Reallocated Object File, it will compiled into one object file instead of separated object file, and duplicated variables will be stripped.</p>
</li>
<li>
<p>strip<br>
Development Postprocesssing = YES<br>
Static framework = Non-global Symbols<br>
dynamic framework = Non-global Symbols or All Symbols<br>
App = All Symbols<br>
To strip the C functions, need to set the “Symbols Hidden by Default” flag to true, and put <strong>attribute</strong>((visibility(“default”))) before the public functions. <a href="https://stackoverflow.com/a/16492468/5353589">https://stackoverflow.com/a/16492468/5353589</a></p>
</li>
<li>
<p><em>Generate Position</em>-<em>Dependent Code</em><br>
Check the flag is set to default NO</p>
</li>
<li>
<p>finiline-function<br>
Set this flag in Other C/C++ flag. Inline the functions</p>
</li>
</ol>
<h2 id="memory-management">Memory Management</h2>
<ol>
<li>Memory overflow</li>
<li>Memory double free</li>
<li>Memory leak</li>
</ol>
<h2 id="code-hardening">Code Hardening</h2>
<ol>
<li>avoid unsecure system api</li>
<li>Obfuscation: no meaningful name for security related code</li>
<li>No cache for sensitive data</li>
<li>Secure random number</li>
<li>Use keychain for sensitive data, and use access control</li>
</ol>

