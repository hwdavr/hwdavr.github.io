---


---

<h2 id="boolean">Boolean</h2>
<p>Boolean is some simple configuration to configure the <strong>process</strong>.<br>
But it is a global setting,  for example, if you turn on <strong>ftp_home_dir</strong>, it will allow ftp to access to <strong>all home directories</strong>. It cannot control to individual file.<br>
If you want to control the access to individual file, you need to change the context.</p>
<h2 id="domain-and-context">Domain and Context</h2>
<p>在SELinux当中针对这两样东西定义了两个基本概念：域(domain)和上下文(context)。</p>
<p><strong>域就是用来对进行进程限制，而上下文就是对系统资源进行限制</strong>。<br>
<strong>Domain is for process. Context is for resource.</strong></p>
<p>我们可以通过  <strong>ps -Z</strong>  这命令来查看当前进程的域的信息，也就是进程的SELinux信息：</p>
<pre><code>[root@xiaoluo ~]# ps -eZ |grep httpd
LABEL                                                    PID  TTY          TIME CMD
system_u:system_r:**httpd_t**:s0     1304 ?        00:00:00 httpd
</code></pre>
<p>通过  <strong>ls -Z</strong>  命令我们可以查看文件上下文信息，也就是文件的SELinux信息：</p>
<pre><code>[root@xiaoluo ~]# ls -Z /content
-rwxr-xr-x. root root system_u:object_r:**httpd_sys_content_t**:s0 index.html
</code></pre>
<h3 id="check-access">Check access</h3>
<p>To check if a process can access the resource, you can use below command.</p>
<pre><code>sesearch --allow --source httpd_t --target httpd_sys_content_t
</code></pre>
<p>If you cannot find below result, means you don’t have access from the process.</p>
<pre><code>Found 25 semantic av rules:
   allow httpd_t httpd_sys_content_t : dir { ioctl read getattr lock search open } ;
   allow httpd_t httpd_sys_content_t : lnk_file { read getattr } ;
   allow httpd_t httpd_sys_content_t : file { ioctl read getattr lock open } ;
   allow httpd_t httpd_sys_content_t : dir { ioctl read write getattr lock add_name remove_name search open } ;
</code></pre>
<h3 id="change-context-for-the-resource">Change context for the resource</h3>
<p>通过  <strong>restorecon</strong>  或者  <strong>chcon</strong>  命令来修复我们的文件上下文信息</p>
<p>命令  <strong>restorecon</strong>  可以用来恢复文件默认的上下文：</p>
<pre><code>restorecon -R -v /var/www/html/index.html　　//-R 表示递归，如果是目录，则该目录下的所有子目录、文件都会得到修复　　
</code></pre>
<p>命令  <strong>chcon</strong>  可以改变文件的上下文信息，通常我们使用一个参照文件来进行修改：</p>
<p>chcon --reference=/var/www/html/index.html /var/www/html/test.html</p>
<p>这里我们通过使用  <strong>restorecon</strong>  命令来恢复我们文件默认的上下文：</p>
<pre><code>[root@xiaoluo html]# restorecon -v index.html 
restorecon reset /var/www/html/index.html context 
unconfined_u:object_r:home_root_t:s0-&gt;unconfined_u:object_r:httpd_sys_content_t:s0

[root@xiaoluo html]# ls -Z 
-rw-r--r--. root root unconfined_u:object_r:**httpd_sys_content_t**:s0 index.html
</code></pre>
<h2 id="audit2allow">audit2allow</h2>
<p>The third way to fix the issue to use to audit2allow.</p>
<p>First, check why is the issue happened.</p>
<pre><code>ausearch -m avc | audit2why
</code></pre>
<p>Then you should see “Missing type enforcement allow(te) rule”.<br>
Use audit2allow to generate a module od allow rule.</p>
<pre><code>ausearch -m avc | audit2allow -a -M allowhttpd
</code></pre>
<p>It will generate 2 files at current directory, allowhttpd.pp and allowhttpd.te. After that,</p>
<pre><code>semodule -i allowhttpd.p
</code></pre>
<p>Use</p>
<pre><code>semodule -l | grep allowhttpd
</code></pre>
<p>You should see a module that we created.</p>

