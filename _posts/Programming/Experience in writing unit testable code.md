---


---

<p><strong>1. Test with database</strong><br>
<a href="http://stackoverflow.com/questions/145131/whats-the-best-strategy-for-unit-testing-database-driven-applications">http://stackoverflow.com/questions/145131/whats-the-best-strategy-for-unit-testing-database-driven-applications</a></p>
<p>1.1 Create test data as a test target</p>
<p>1.2 Set up Jenkins build to check every time commit</p>
<p><strong>2. How to test with complicated class</strong></p>
<p><a href="http://programmers.stackexchange.com/questions/198453/is-there-a-point-to-unit-tests-that-stub-and-mock-everything-public">http://programmers.stackexchange.com/questions/198453/is-there-a-point-to-unit-tests-that-stub-and-mock-everything-public</a></p>
<p>Create a class for actual “business logic”, it has no call or few calls to other classes, just pass the other object from method arguments, so it’s easy to do unit test. Which means the class methods can be written as static methods.</p>
<p><strong>3. Constructor design</strong></p>
<p><a href="http://misko.hevery.com/code-reviewers-guide/flaw-constructor-does-real-work/">http://misko.hevery.com/code-reviewers-guide/flaw-constructor-does-real-work/</a></p>
<p>3.1 Don’t do any logic in constructors.<br>
3.2 Check your design if the class if violates the Single Responsibility Principle.<br>
3.3 Don’t pass every arguments from constructor, unless want to use dependency injection to do unit test. Pass only the necessary class, use getter and setter for other arguments, or use another method to init all the thing.</p>
<p><strong>4. Avoid instantiating or creating new instances inside methods with logic directly, use factory method to get the instances and later you can easily mock the factory.</strong></p>
<p>But remember every time you use these instances, you need to get directly from factory.</p>
<p><strong>5. Separate the framework call or OSGi event call to another class, then you can mock the class and use normal unit test, not the plugin unit test.</strong></p>
<p>Also you can capture the arguments of the method to check the results by using mockito,</p>
<p><a href="http://stackoverflow.com/questions/5981605/can-mockito-capture-arguments-of-a-method-called-multiple-times">http://stackoverflow.com/questions/5981605/can-mockito-capture-arguments-of-a-method-called-multiple-times</a></p>
<p><strong>6. Don’t use Singleton pattern, use singleton instance only.</strong></p>
<p><a href="http://puredanger.github.io/tech.puredanger.com/2007/07/03/pattern-hate-singleton/">http://puredanger.github.io/tech.puredanger.com/2007/07/03/pattern-hate-singleton/</a></p>
<p><a href="http://geekswithblogs.net/AngelEyes/archive/2013/09/08/singleton-i-love-you-but-youre-bringing-me-down-re-uploaded.aspx">http://geekswithblogs.net/AngelEyes/archive/2013/09/08/singleton-i-love-you-but-youre-bringing-me-down-re-uploaded.aspx</a></p>
<p><a href="http://programmers.stackexchange.com/questions/40373/so-singletons-are-bad-then-what">http://programmers.stackexchange.com/questions/40373/so-singletons-are-bad-then-what</a></p>

