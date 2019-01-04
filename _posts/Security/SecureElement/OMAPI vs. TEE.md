---


---

<h2 id="omapi-vs.-tee-client-api">OMAPI vs. TEE Client API</h2>

<table>
<thead>
<tr>
<th>OMAPI</th>
<th>TEE Client API</th>
</tr>
</thead>
<tbody>
<tr>
<td>Reader.openSession()</td>
<td>TEEC_InitializeContext(name, TEEC_Context)</td>
</tr>
<tr>
<td>Session.openLogicalChannel(AID)</td>
<td>TEEC_OpenSession(Context, Session, uuid, …)</td>
</tr>
<tr>
<td>Channel.transmit()</td>
<td>TEEC_InvokeCommand(Session, commandId, Operation, resturn)</td>
</tr>
<tr>
<td>Channel.close()</td>
<td>TEEC_CloseSession(Session)</td>
</tr>
<tr>
<td>Session.close()</td>
<td>TEEC_FinalizeContext(Context)</td>
</tr>
<tr>
<td><strong>Service</strong>.shutdown()</td>
<td></td>
</tr>
</tbody>
</table><h3 id="create-a-seservice">Create a SEService</h3>
<pre class=" language-java"><code class="prism  language-java">SEService seService <span class="token operator">=</span>  <span class="token keyword">new</span>  <span class="token class-name">SEService</span><span class="token punctuation">(</span><span class="token keyword">this</span><span class="token punctuation">,</span> <span class="token keyword">this</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token comment">/**
* Callback interface if informs that this SEService is connected to the SmartCardService
*/</span>
<span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">SEServiceCallback</span> <span class="token keyword">implements</span> <span class="token class-name">CallBack</span> <span class="token punctuation">{</span>
	<span class="token keyword">public</span> <span class="token keyword">void</span> <span class="token function">serviceConnected</span><span class="token punctuation">(</span>SEService service<span class="token punctuation">)</span> <span class="token punctuation">{</span>
		_service <span class="token operator">=</span> service<span class="token punctuation">;</span>
		<span class="token function">performTest</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<h3 id="basic-channel-vs.-logical-channel">Basic Channel vs. Logical Channel</h3>
<ol>
<li>you can occupy a logical channel as long as your application<br>
requires it but it’s recommended to release the channel as soon as<br>
possible, e.g. transaction done, onPause/onStop called, … as typical<br>
Secure Elements support up to three logical channels</li>
<li>you have the channel 0 for APDU communication which is always open<br>
when the Secure Element is powered, also called basic channel. This<br>
channel cannot be closed. Channel 1-3 (and above according to<br>
ISO-7816) are logical channels<br>
<a href="https://groups.google.com/forum/#!topic/seek-for-android/cR60V3yBwpI">https://groups.google.com/forum/#!topic/seek-for-android/cR60V3yBwpI</a></li>
</ol>
<p>How many channels?<br>
Refer to GPCS: 11.7 MANAGE CHANNEL Command<br>
What is Answer to Reset?</p>

