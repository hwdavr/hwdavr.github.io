---


---

<h2 id="useful-commands">Useful commands</h2>
<h3 id="check-environment-variable">Check Environment Variable</h3>
<pre class=" language-script"><code class="prism  language-script">env
env | more
set 
set | more
</code></pre>
<h3 id="cron-job">Cron Job</h3>
<p>Execute every Friday 1AM</p>
<pre><code>0 0 1,15 * * ~/script.sh
</code></pre>
<p>To list all the cron job</p>
<p>crontab -l</p>
<p>Edit cron job:</p>
<p>crontab -eUseful command:</p>
<h3 id="search">Search</h3>
<p><strong>Search file with name in current directory</strong></p>
<pre><code>find . -name 'filename'
</code></pre>
<p><strong>Search file content with text recursively in current directory</strong></p>
<pre><code>grep -r 'text' .
</code></pre>
<h3 id="monitor-server-log">Monitor Server log</h3>
<pre><code>tail -f /logs/catalina.out
</code></pre>

