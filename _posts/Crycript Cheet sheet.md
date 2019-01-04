---


---

<p><a href="http://iphonedevwiki.net/index.php/Cycript_Tricks">http://iphonedevwiki.net/index.php/Cycript_Tricks</a></p>
<h3 id="how-to-attach-to-a-process">How to attach to a process</h3>
<p><code>cypriot -p pid</code></p>
<h3 id="print-methods-of-classs">Print methods of classs</h3>
<pre class=" language-javascript"><code class="prism  language-javascript"><span class="token keyword">function</span> <span class="token function">printMethods</span><span class="token punctuation">(</span>className<span class="token punctuation">,</span> isa<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">var</span> count <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">new</span> <span class="token function">Type</span><span class="token punctuation">(</span><span class="token string">"I"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token keyword">var</span> classObj <span class="token operator">=</span> <span class="token punctuation">(</span>isa <span class="token operator">!=</span> undefined<span class="token punctuation">)</span> <span class="token operator">?</span> <span class="token function">objc_getClass</span><span class="token punctuation">(</span>className<span class="token punctuation">)</span><span class="token punctuation">.</span>constructor <span class="token punctuation">:</span> <span class="token function">objc_getClass</span><span class="token punctuation">(</span>className<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token keyword">var</span> methods <span class="token operator">=</span> <span class="token function">class_copyMethodList</span><span class="token punctuation">(</span>classObj<span class="token punctuation">,</span> count<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token keyword">var</span> methodsArray <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">]</span><span class="token punctuation">;</span>
  <span class="token keyword">for</span><span class="token punctuation">(</span><span class="token keyword">var</span> i <span class="token operator">=</span> <span class="token number">0</span><span class="token punctuation">;</span> i <span class="token operator">&lt;</span> <span class="token operator">*</span>count<span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">var</span> method <span class="token operator">=</span> methods<span class="token punctuation">[</span>i<span class="token punctuation">]</span><span class="token punctuation">;</span>
    methodsArray<span class="token punctuation">.</span><span class="token function">push</span><span class="token punctuation">(</span><span class="token punctuation">{</span>selector<span class="token punctuation">:</span><span class="token function">method_getName</span><span class="token punctuation">(</span>method<span class="token punctuation">)</span><span class="token punctuation">,</span> implementation<span class="token punctuation">:</span><span class="token function">method_getImplementation</span><span class="token punctuation">(</span>method<span class="token punctuation">)</span><span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
  <span class="token function">free</span><span class="token punctuation">(</span>methods<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token keyword">return</span> methodsArray<span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<h3 id="get-the-viewcontroller-from-a-tabbarview-step-by-step">Get the ViewController from a TabBarView step by step</h3>
<pre class=" language-javascript"><code class="prism  language-javascript">cy# <span class="token keyword">var</span> window <span class="token operator">=</span> <span class="token punctuation">[</span><span class="token punctuation">[</span>UIApplication sharedApplication<span class="token punctuation">]</span> keyWindow<span class="token punctuation">]</span><span class="token punctuation">;</span>
#<span class="token string">"&lt;UIWindow: 0x17863d20; frame = (0 0; 768 1024); tintColor = UIDeviceWhiteColorSpace 1 1; gestureRecognizers = &lt;NSArray: 0x16505b80&gt;; layer = &lt;UIWindowLayer: 0x1650a180&gt;&gt;"</span>
cy# <span class="token keyword">var</span> tabBarCtr <span class="token operator">=</span> window<span class="token punctuation">.</span>rootViewController
#<span class="token string">"&lt;UITabBarController: 0x169ab200&gt;"</span>
cy# <span class="token keyword">var</span> tab0vc <span class="token operator">=</span> tabBarCtr<span class="token punctuation">.</span>viewControllers<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span>
#<span class="token string">"&lt;UINavigationController: 0x169af200&gt;"</span>
cy# <span class="token keyword">var</span> tab0vc0 <span class="token operator">=</span> tab0vc<span class="token punctuation">.</span>viewControllers<span class="token punctuation">[</span><span class="token number">0</span><span class="token punctuation">]</span>
#<span class="token string">"&lt;SectionsViewController: 0x1660d040&gt;"</span>
</code></pre>
<p>###Hook NSLog and print to syslog<br>
Type to console:</p>
<pre><code>NSLog_ = dlsym(RTLD_DEFAULT, "NSLog")
NSLog = function() { var types = 'v', args = [], count = arguments.length; for (var i = 0; i != count; ++i) { types += '@'; args.push(arguments[i]); } new Functor(NSLog_, types).apply(null, args); }
</code></pre>

