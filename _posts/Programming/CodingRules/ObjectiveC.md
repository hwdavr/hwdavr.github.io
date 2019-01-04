---


---

<h2 id="coding-rules-for-security">Coding Rules for Security</h2>
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
<h2 id="general-coding-rules">General Coding Rules</h2>
<ol>
<li>
<p>Create a string array based on the enum index<br>
NSString *const stringArray[] = {<br>
[ENUM0] = @“String0”,<br>
[ENUM1] = @“String1”,<br>
};</p>
</li>
<li>
<p>Override properties getter and setter<br>
properties must be nonatomic.<br>
must specify @synthesize the ivars.</p>
</li>
<li>
<p>Use NS_ENUM and specify the data type instead of enum only</p>
</li>
</ol>
<pre class=" language-objectivec"><code class="prism  language-objectivec"><span class="token keyword">extern</span> NSString <span class="token operator">*</span><span class="token keyword">const</span> GTLServiceErrorDomain<span class="token punctuation">;</span>

<span class="token keyword">typedef</span> <span class="token function">NS_ENUM</span><span class="token punctuation">(</span>NSInteger<span class="token punctuation">,</span> GTLServiceError<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  GTLServiceErrorQueryResultMissing <span class="token operator">=</span> <span class="token operator">-</span><span class="token number">3000</span><span class="token punctuation">,</span>
  GTLServiceErrorWaitTimedOut       <span class="token operator">=</span> <span class="token operator">-</span><span class="token number">3001</span><span class="token punctuation">,</span>
<span class="token punctuation">}</span><span class="token punctuation">;</span>
</code></pre>
<ol start="4">
<li>
<p>Global and file scope constants should have an appropriate  <a href="http://google.github.io/styleguide/objcguide.html#prefixes">prefix</a>.</p>
</li>
<li>
<p>Do Not Use +new<a href="http://google.github.io/styleguide/objcguide.html#do-not-use-new"></a></p>
</li>
</ol>
<p>Do not invoke the  <code>NSObject</code>  class method  <code>new</code>, nor override it in a subclass.  <code>+new</code>  is rarely used and contrasts greatly with initializer usage. Instead, use  <code>+alloc</code>  and  <code>-init</code>  methods to instantiate retained objects.</p>
<ol start="6">
<li>
<p>NS_ASSUME_NONNULL_BEGIN<br>
NS_ASSUME_NONNULL_BEGIN<br>
NS_ASSUME_NONNULL_END</p>
</li>
<li>
<p>Avoid to use accessor in init and dealloc.1.  Create a string array based on the enum index<br>
NSString *const stringArray[] = {<br>
[ENUM0] = @“String0”,<br>
[ENUM1] = @“String1”,<br>
};</p>
</li>
</ol>

