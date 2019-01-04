---


---

<p>The only difference between  <code>TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384</code>  and  <code>TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384</code>  is the signature algorithm.</p>
<p>Whatever, one will have to generate an ECC key pair on the fly in order to perform an ECDHE. Then, this key pair will be signed using the certificate private key. If the certificate contains a RSA public key, then the generated ECC public key will be signed using RSA. Otherwise (<em>i.e.</em>  if it contains an ECDSA public key) it will be signed using ECDSA. Also note that one will have to verify the peer signature on top of generating his own.</p>
<p><a href="https://blog.cloudflare.com/keyless-ssl-the-nitty-gritty-technical-details/">https://blog.cloudflare.com/keyless-ssl-the-nitty-gritty-technical-details/</a></p>
<p><a href="https://github.com/ssllabs/research/wiki/SSL-and-TLS-Deployment-Best-Practices">https://github.com/ssllabs/research/wiki/SSL-and-TLS-Deployment-Best-Practices</a><br>
Forward Secrecy<br>
ECDH is to resolve private key can be compromised issue. Previous way, certificate private key is used for both authentication and encryption.<br>
<a href="https://vincent.bernat.im/en/blog/2011-ssl-perfect-forward-secrecy">https://vincent.bernat.im/en/blog/2011-ssl-perfect-forward-secrecy</a></p>

