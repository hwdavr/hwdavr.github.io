---


---

<ol>
<li>Read process information</li>
</ol>
<pre class=" language-c"><code class="prism  language-c"><span class="token keyword">int</span> fd <span class="token operator">=</span> <span class="token function">open</span><span class="token punctuation">(</span><span class="token string">"/proc/self/maps"</span><span class="token punctuation">,</span> O_RDONLY<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<ol start="2">
<li>Execute command line</li>
</ol>
<pre class=" language-c"><code class="prism  language-c">  <span class="token keyword">char</span> command<span class="token punctuation">[</span><span class="token number">50</span><span class="token punctuation">]</span><span class="token punctuation">;</span>

  <span class="token function">strcpy</span><span class="token punctuation">(</span>command<span class="token punctuation">,</span> <span class="token string">"ls -l"</span> <span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token function">system</span><span class="token punctuation">(</span>command<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>

