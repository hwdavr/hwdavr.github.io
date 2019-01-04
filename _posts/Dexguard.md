---


---

<p><a href="https://www.cnblogs.com/bluestorm/p/6858011.html">https://www.cnblogs.com/bluestorm/p/6858011.html</a></p>
<h3 id="keepclasseswithmembernames-not-working-with-package">keepclasseswithmembernames not working with package</h3>
<p>Use below one</p>
<pre><code>-keep public interface org.xutils.** {
public protected *;
}
</code></pre>
<h3 id="local-private-method-variable-in-thread-obfuscation-wrongly">local private method variable in Thread obfuscation wrongly</h3>
<pre class=" language-java"><code class="prism  language-java"><span class="token function">test</span><span class="token punctuation">(</span><span class="token keyword">final</span> <span class="token keyword">int</span> type<span class="token punctuation">)</span> <span class="token punctuation">{</span>
	<span class="token keyword">new</span> <span class="token class-name">Thread</span><span class="token punctuation">(</span><span class="token keyword">new</span> <span class="token class-name">Runnable</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		<span class="token keyword">if</span> <span class="token punctuation">(</span>type <span class="token operator">==</span> <span class="token number">0</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
		<span class="token punctuation">}</span>
	<span class="token punctuation">}</span><span class="token punctuation">)</span>
<span class="token punctuation">}</span>
</code></pre>
<p>Solution is moving test() to another class and make it public.</p>

