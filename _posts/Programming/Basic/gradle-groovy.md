---


---

<p><a href="https://docs.gradle.org/current/userguide/more_about_tasks.html">https://docs.gradle.org/current/userguide/more_about_tasks.html</a></p>
<h3 id="basic-copy-task">Basic Copy Task</h3>
<pre class=" language-groovy"><code class="prism  language-groovy">afterEvaluate <span class="token punctuation">{</span>  
    libraryVariants<span class="token operator">.</span>all <span class="token punctuation">{</span> variant <span class="token operator">-&gt;</span>  
        <span class="token keyword">def</span> varBuildType <span class="token operator">=</span> variant<span class="token operator">.</span>buildType<span class="token operator">.</span>name<span class="token operator">.</span><span class="token function">capitalize</span><span class="token punctuation">(</span><span class="token punctuation">)</span>  
        <span class="token keyword">def</span> dependTask <span class="token operator">=</span> <span class="token string gstring">"transformNativeLibsWithIntermediateJniLibsFor<span class="token expression"><span class="token punctuation">$</span>varBuildType</span>"</span>  
        println <span class="token string gstring">"Task: "</span> <span class="token operator">+</span> dependTask  
  
        tasks<span class="token punctuation">[</span>dependTask<span class="token punctuation">]</span><span class="token operator">.</span>doLast <span class="token punctuation">{</span>  
            copy <span class="token punctuation">{</span>  
                println <span class="token string gstring">"Copying native libs"</span>  
			    from <span class="token string gstring">"../../../OpenCV/libs"</span>  
			    into <span class="token string gstring">"libs"</span>  
			<span class="token punctuation">}</span>  
        <span class="token punctuation">}</span>  
    <span class="token punctuation">}</span>  
<span class="token punctuation">}</span>
</code></pre>
<h3 id="standalone-build-script">Standalone build script</h3>
<pre class=" language-groovy"><code class="prism  language-groovy">
<span class="token keyword">def</span> isLibrary <span class="token operator">=</span> <span class="token punctuation">{</span> module <span class="token operator">-&gt;</span>  
    module<span class="token operator">.</span><span class="token function">hasProperty</span><span class="token punctuation">(</span><span class="token string gstring">"android"</span><span class="token punctuation">)</span> <span class="token operator">&amp;&amp;</span> module<span class="token operator">.</span>android<span class="token operator">.</span><span class="token function">hasProperty</span><span class="token punctuation">(</span><span class="token string gstring">"libraryVariants"</span><span class="token punctuation">)</span>  
<span class="token punctuation">}</span>

gradle<span class="token operator">.</span>projectsEvaluated <span class="token punctuation">{</span>
subprojects <span class="token punctuation">{</span> libProj <span class="token operator">-&gt;</span>  
        libProj<span class="token operator">.</span>android<span class="token operator">.</span>libraryVariants<span class="token operator">.</span>all <span class="token punctuation">{</span> variant <span class="token operator">-&gt;</span>  
            <span class="token keyword">def</span> varNameCap <span class="token operator">=</span> variant<span class="token operator">.</span>name<span class="token operator">.</span><span class="token function">capitalize</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
        <span class="token punctuation">}</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<h3 id="global-variables">Global Variables</h3>
<pre class=" language-groovy"><code class="prism : language-groovy">ext <span class="token punctuation">{</span>
	myTest <span class="token operator">=</span> <span class="token string">'Test String'</span>
	version
<span class="token punctuation">}</span>
</code></pre>
<p>From projectName.gradle:</p>
<pre class=" language-groovy"><code class="prism  language-groovy">apply from<span class="token punctuation">:</span> <span class="token string">'script/properties.gradle'</span>
</code></pre>
<h3 id="get-android-sdk">Get Android SDK</h3>
<pre class=" language-groovy"><code class="prism  language-groovy">android<span class="token operator">.</span><span class="token function">getBootClasspath</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token operator">.</span><span class="token function">join</span><span class="token punctuation">(</span>File<span class="token operator">.</span>pathSeparator<span class="token punctuation">)</span>
</code></pre>
<h3 id="keywords">Keywords</h3>
<p>evaluationDependsOn()</p>

