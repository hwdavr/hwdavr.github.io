---


---

<h2 id="duplicated-class">Duplicated Class</h2>
<blockquote>
<p>Class Foo is implemented in both MyApp and MyAppTestCase. One of the two will be used. Which one is undefined.</p>
</blockquote>
<p>The reason that both images (the app and the dynamic library bundle) define the implementation of the class. the class is dynamically loaded into the objc runtime. the objc runtime uses a flat namespace. how this works:</p>
<ul>
<li>the binary is loaded, starting with its dependencies</li>
<li>as each binary is loaded, the objc classes register with the objc runtime</li>
<li>if a class with a specific name is loaded twice, the behaviour is undefined. one implementation of a class (with identical names) can be loaded into the objc runtime.</li>
</ul>
<p>the  <em>typical</em>  problem here is that you will be returned one implementation - your app will likely crash when the type conflicts (when the class does not come from the same source file).<br>
<a href="https://stackoverflow.com/questions/6149673/class-foo-is-implemented-in-both-myapp-and-myapptestcase-one-of-the-two-will-be">https://stackoverflow.com/questions/6149673/class-foo-is-implemented-in-both-myapp-and-myapptestcase-one-of-the-two-will-be</a></p>
<h2 id="section"></h2>

