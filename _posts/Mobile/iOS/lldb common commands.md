---


---

<h3 id="print-nsdata-in-bytes">Print NSData in Bytes</h3>
<p>po encrypted<br>
Or</p>
<pre><code>me read `[encrypted bytes]` -c`[encrypted length]`
me read `[myData bytes]` -c`[myData length]` -t int
</code></pre>
<h3 id="set-watch-point">Set watch point</h3>
<p>In addition to breakpoints, you can use  <code>help watchpoint</code>  to see all the commands for watchpoint manipulations. For instance, we might do the following to watch a variable called ‘global’ for write operation, but only stop if the condition ‘(global==5)’ is true:</p>
<pre><code>(lldb) watch set var global
Watchpoint created: Watchpoint 1: addr = 0x100001018 size = 4 state = enabled type = w
    declare @ '/Volumes/data/lldb/svn/ToT/test/functionalities/watchpoint/watchpoint_commands/condition/main.cpp:12'
(lldb) watch modify -c '(global==5)'
(lldb) watch list
</code></pre>
<h3 id="print-message-from-address-crypto_data-padded_message">Print message from address crypto_data-&gt;padded_message:</h3>
<p>memory read -s1 -fx -c40 crypto_data-&gt;padded_message</p>
<ol>
<li>-s for bytes grouping so use 1 for uint8 for example and 4 for int</li>
<li>-f for format. I inherently forget the right symbol. Just put the statement with -f and it will snap back at you and give you the list of all the options</li>
<li>-c is for count of bytes</li>
<li>if you are printing more than 1024 bytes, append with --force</li>
</ol>

