---


---

<h2 id="safety-check">Safety Check</h2>
<h3 id="optional-language">Optional Language</h3>
<p>If the parameter is required, put it as non-optional.<br>
If the parameter is optional, put it as optional.</p>
<h3 id="non-optional-language">Non-optional Language</h3>
<p>For the language without optional, the parameter checking is important. We need to check the null pointer of the parameters and throw exception and return error when the parameters is required for the function.</p>
<h2 id="late-init-vs.-optional-vs.-lazy">Late init vs. optional vs. lazy</h2>
<p>If the variable assignment is later than it can be used, use optional.<br>
If the variable assignment can be null when it failed, use optional.</p>
<pre class=" language-swift"><code class="prism  language-swift"><span class="token keyword">var</span> cursor<span class="token punctuation">:</span> <span class="token builtin">Cursor</span><span class="token operator">?</span> <span class="token operator">=</span> null
<span class="token keyword">try</span> <span class="token punctuation">{</span>
    cursor <span class="token operator">=</span> sqliteDB<span class="token punctuation">.</span><span class="token function">query</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span> <span class="token keyword">catch</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
	cursor<span class="token operator">?</span><span class="token punctuation">.</span><span class="token function">close</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
<span class="token punctuation">}</span>
</code></pre>

