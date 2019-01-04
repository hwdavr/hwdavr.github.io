---


---

<p>Unit test of data-binding in XAML:</p>
<p><a href="http://csharperimage.jeremylikness.com/2010/08/unit-testing-xaml-data-bindings-in.html">http://csharperimage.jeremylikness.com/2010/08/unit-testing-xaml-data-bindings-in.html</a></p>
<p>PresentationTraceSources Class</p>
<p>Moles - Isolation framework for .NET</p>
<p><strong>Replace any .NET method with your own delegate!</strong></p>
<p><a href="http://research.microsoft.com/en-us/projects/moles/">http://research.microsoft.com/en-us/projects/moles/</a></p>
<p>DI</p>
<p><a href="http://www.objc.io/issues/11-android/dependency-injection-in-java/">http://www.objc.io/issues/11-android/dependency-injection-in-java/</a></p>
<p><a href="http://huan-lin.blogspot.com/2011/10/dependency-injection-3.html">http://huan-lin.blogspot.com/2011/10/dependency-injection-3.html</a></p>
<p>Rules for unit testable class:</p>
<ol>
<li>
<p>The class testable should be loosely decoupled by other classes. Can not new or create another object in side the constructor or even in the class, including not using any static service inside the class.</p>
</li>
<li>
<p>Any new object should be created in side the main, and pass them from constructor (Necessary) or setter method. If they can not create at program startup, need to use factory pattern or builder pattern to generate them.</p>
</li>
<li>
<p>Any service should be passed from constructor or setter method.</p>
</li>
</ol>
<p>Unit test with ServiceLocator:</p>
<p><a href="http://taswar.zeytinsoft.com/2010/06/30/stubbing-out-servicelocator-for-unit-testing/">http://taswar.zeytinsoft.com/2010/06/30/stubbing-out-servicelocator-for-unit-testing/</a></p>
<h3 id="junit">Junit</h3>
<p>Robolectric is running on Single Thread only.</p>

