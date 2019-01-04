---


---

<p>SSL self signed cert:</p>
<p><a href="http://ogrelab.ikratko.com/using-android-volley-with-self-signed-certificate/">http://ogrelab.ikratko.com/using-android-volley-with-self-signed-certificate/</a></p>
<p>ssh -i “topnews.pem” <a href="mailto:ec2-user@ec2-52-192-114-237.ap-northeast-1.compute.amazonaws.com">ec2-user@ec2-52-192-114-237.ap-northeast-1.compute.amazonaws.com</a></p>
<p>Lets encrypt<br>
Certificate renew<br>
sudo ./certbot-auto renew --pre-hook “service nginx stop” --post-hook "service nginx start”</p>
<pre><code>2018-02-24:
</code></pre>
<p>wget <a href="https://dl.eff.org/certbot-auto">https://dl.eff.org/certbot-auto</a><br>
chmod a+x certbot-auto</p>
<p>If met this error,</p>
<p>rm -rf ~/.local/share/letsencrypt</p>
<p>Try this as root:</p>
<pre><code>rm -rf ~/.local/share/letsencrypt
rm -rf /opt/eff.org/certbot/
</code></pre>

