---


---

<h2 id="c">C</h2>
<ol>
<li>Remove sensitive data after usage, set all 0 or random.</li>
<li>Prevent memory leakage</li>
</ol>
<ul>
<li>Put string buffer array to the last element of structure, even it overflow, it will not destroy the other data.</li>
</ul>
<ol start="3">
<li>Avoid to use memcpy… or strcpy… kinds of function, try to implement your own functions.</li>
<li>Use safe snprint, strlcat,  strncat, strnstr.</li>
<li>Use static <strong>attribute</strong>((always_inline)) as much as possible</li>
<li>strip as much symbol as possible</li>
<li>Use internal syscal</li>
<li>Use static inline function instead of macro like function, the side effect can refer to <a href="https://wiki.sei.cmu.edu/confluence/display/c/PRE31-C.+Avoid+side+effects+in+arguments+to+unsafe+macros">https://wiki.sei.cmu.edu/confluence/display/c/PRE31-C.+Avoid+side+effects+in+arguments+to+unsafe+macros</a></li>
<li></li>
</ol>

