---


---

<h2 id="sei-rules">SEI Rules</h2>
<ul>
<li><a href="https://wiki.sei.cmu.edu/confluence/display/android/DRD11.+Ensure+that+sensitive+data+is+kept+secure">DRD11. Ensure that sensitive data is kept secure</a><br>
<code>MODE_PRIVATE</code> is a constant defined by the class <code>android.content.Context</code>. It may be used as the mode parameter in the methods <code>openFileOutput()</code>, <code>getSharedPreferences()</code>, and <code>openOrCreateDatabase()</code>.<br>
As of API 17, the <code>MODE_WORLD_READABLE</code> and <code>MODE_WORLD_WRITEABLE</code> are deprecated. Do not use them to share the content between Apps.</li>
<li>df</li>
</ul>

