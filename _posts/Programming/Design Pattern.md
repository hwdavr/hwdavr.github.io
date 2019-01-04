---


---

<p>&lt;![endif]–&gt;</p>
<h3 id="mvp-design-pattern">MVP design pattern</h3>
<p>The big difference between MVP and MVC is how to handle the view.</p>
<ul>
<li>
<p>In MVC, the Controller manipulates the view, taking care of how to render in the view parts of the user actions and model. That means that the Controller and View have ‘tight coupling’.</p>
</li>
<li>
<p>In MVP, the Presenter takes care of the user tasks, the model is shared between the Presenter and View. So the view renders UI according to the model, sometimes the view can have actions to be called from the Presenter. The Presenter and View can have a defined interface contracts to make them ‘loose coupling’. For example you can create a View for Java Swing UI and another for JavaFX UI. Or if the connection to the data source changes, then you just need update the presenter.</p>
</li>
</ul>
<p>There are many styles to program the MVP.</p>
<p>In a formal way, consists in create interfaces for each element of the design pattern.</p>
<p><a href="MVP.java">MVP.java</a></p>
<pre class=" language-java"><code class="prism  language-java">C#<span class="token operator">:</span> Use delegate to isolate the view and presenter<span class="token punctuation">.</span>
<span class="token keyword">public</span> partial <span class="token keyword">class</span> <span class="token class-name">ClientsForm</span> <span class="token operator">:</span> Form<span class="token punctuation">,</span> IClientsView
<span class="token punctuation">{</span>
	<span class="token keyword">public</span> event Action ClientSelected<span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre>
<p><img src="https://picasaweb.google.com/109606753991119733140/6572701338169173521#6572701341756408274" alt="enter image description here" title="MVP"></p>
<h3 id="filter-pattern">Filter Pattern</h3>
<p>Create an interface for Criteria.</p>
<p><em>Criteria.java</em></p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">import</span> java<span class="token punctuation">.</span>util<span class="token punctuation">.</span>List<span class="token punctuation">;</span>

<span class="token keyword">public</span>  <span class="token keyword">interface</span>  <span class="token class-name">Criteria</span>  <span class="token punctuation">{</span>
	<span class="token keyword">public</span>  List<span class="token operator">&lt;</span>Person<span class="token operator">&gt;</span> <span class="token function">meetCriteria</span><span class="token punctuation">(</span>List<span class="token operator">&lt;</span>Person<span class="token operator">&gt;</span> persons<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token punctuation">}</span>
</code></pre>
<p>Step 3</p>
<p>Create concrete classes implementing the <em>Criteria</em> interface.</p>
<p><em>CriteriaMale.java</em></p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">import</span> java<span class="token punctuation">.</span>util<span class="token punctuation">.</span>ArrayList<span class="token punctuation">;</span>

<span class="token keyword">import</span> java<span class="token punctuation">.</span>util<span class="token punctuation">.</span>List<span class="token punctuation">;</span>

<span class="token keyword">public</span>  <span class="token keyword">class</span>  <span class="token class-name">CriteriaMale</span>  <span class="token keyword">implements</span>  <span class="token class-name">Criteria</span>  <span class="token punctuation">{</span>

<span class="token annotation punctuation">@Override</span>

<span class="token keyword">public</span>  List<span class="token operator">&lt;</span>Person<span class="token operator">&gt;</span> <span class="token function">meetCriteria</span><span class="token punctuation">(</span>List<span class="token operator">&lt;</span>Person<span class="token operator">&gt;</span> persons<span class="token punctuation">)</span>  <span class="token punctuation">{</span>

	List<span class="token operator">&lt;</span>Person<span class="token operator">&gt;</span> malePersons <span class="token operator">=</span>  <span class="token keyword">new</span>  <span class="token class-name">ArrayList</span><span class="token operator">&lt;</span>Person<span class="token operator">&gt;</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

	<span class="token keyword">for</span>  <span class="token punctuation">(</span>Person person <span class="token operator">:</span> persons<span class="token punctuation">)</span>  <span class="token punctuation">{</span>
		<span class="token keyword">if</span><span class="token punctuation">(</span>person<span class="token punctuation">.</span><span class="token function">getGender</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">equalsIgnoreCase</span><span class="token punctuation">(</span><span class="token string">"MALE"</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">{</span>
			malePersons<span class="token punctuation">.</span><span class="token function">add</span><span class="token punctuation">(</span>person<span class="token punctuation">)</span><span class="token punctuation">;</span>
		<span class="token punctuation">}</span>
	<span class="token punctuation">}</span>
	<span class="token keyword">return</span> malePersons<span class="token punctuation">;</span>
<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<p><em>CriteriaFemale.java</em></p>
<h3 id="factory-pattern-and-dependency-injection">Factory Pattern and Dependency Injection</h3>
<p>The purpose of the factory patterns is to separate the  use  of a certain component, from the  choice of implementation  +  instance management  of that component.</p>
<p>In any time, use another class without logic to create new object.</p>
<p><a href="http://tutorials.jenkov.com/dependency-injection/dependency-injection-replacing-factory-patterns.html">http://tutorials.jenkov.com/dependency-injection/dependency-injection-replacing-factory-patterns.html</a></p>
<p><a href="http://misko.hevery.com/2008/07/08/how-to-think-about-the-new-operator/">http://misko.hevery.com/2008/07/08/how-to-think-about-the-new-operator/</a></p>
<h6 id="static-factory-one-factory-only">Static factory (One factory only)</h6>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">MyClass</span> <span class="token punctuation">{</span>

IMyComponent component <span class="token operator">=</span> MyComponentFactory<span class="token punctuation">.</span><span class="token function">instance</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">public</span> <span class="token keyword">void</span> <span class="token function">myMethod</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">{</span>

	component<span class="token punctuation">.</span><span class="token function">doSomething</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<h6 id="abstract-factory-multiple-factories">Abstract factory (Multiple factories)</h6>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">MyClass</span> <span class="token punctuation">{</span>

IMyComponent component <span class="token operator">=</span> null<span class="token punctuation">;</span>

<span class="token keyword">public</span> <span class="token function">MyClass</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
	IMyComponentFactory factory <span class="token operator">=</span>
	MyComponentFactoryManager<span class="token punctuation">.</span><span class="token function">getFactory</span><span class="token punctuation">(</span><span class="token string">"A"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	component <span class="token operator">=</span> factory<span class="token punctuation">.</span><span class="token function">instance</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token keyword">public</span> <span class="token keyword">void</span> <span class="token function">myMethod</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">{</span>
	component<span class="token punctuation">.</span><span class="token function">doSomething</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

<span class="token punctuation">}</span>
</code></pre>
<p>Unit testable factory</p>
<pre class=" language-java"><code class="prism  language-java">Pass a factory instance in as <span class="token keyword">new</span> <span class="token class-name">parameter</span>

Create a settable field in the <span class="token keyword">class</span> <span class="token class-name">for</span> the <span class="token keyword">new</span> <span class="token class-name">factory</span>

<span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">CustomGameFactory</span> <span class="token keyword">implements</span> <span class="token class-name">GameFactory</span>
<span class="token punctuation">{</span>
<span class="token keyword">private</span> Dice mDice<span class="token punctuation">;</span>

<span class="token keyword">public</span> <span class="token function">CustomGameFactory</span><span class="token punctuation">(</span>Dice dice<span class="token punctuation">)</span>
<span class="token punctuation">{</span>
	mDice <span class="token operator">=</span> dice<span class="token punctuation">;</span>
<span class="token punctuation">}</span>

Dice <span class="token function">createDice</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
<span class="token punctuation">{</span>
	mDice <span class="token operator">=</span> （mDice <span class="token operator">==</span> null） <span class="token keyword">new</span> <span class="token class-name">Dice</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">?</span> mDice<span class="token punctuation">;</span>
	<span class="token keyword">return</span> mDice<span class="token punctuation">;</span>
<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<h3 id="builder-pattern">Builder Pattern</h3>
<p><strong>Simple builder with one builder only:</strong></p>
<p><a href="http://www.javacodegeeks.com/2013/01/the-builder-pattern-in-practice.html">http://www.javacodegeeks.com/2013/01/the-builder-pattern-in-practice.html</a></p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span> <span class="token keyword">static</span> <span class="token keyword">class</span> <span class="token class-name">ComponentBuilder</span> <span class="token punctuation">{</span>
	<span class="token keyword">private</span> string name<span class="token punctuation">;</span>
	<span class="token keyword">private</span> string peripheral <span class="token operator">=</span> “Undecided”<span class="token punctuation">;</span>
	<span class="token keyword">private</span> List<span class="token operator">&lt;</span>string<span class="token operator">&gt;</span> channels<span class="token punctuation">;</span>
	<span class="token keyword">public</span> <span class="token function">ComponentBuilder</span> <span class="token punctuation">(</span>string name<span class="token punctuation">,</span> string periph<span class="token punctuation">)</span>
	<span class="token punctuation">{</span>
		<span class="token keyword">this</span><span class="token punctuation">.</span>name <span class="token operator">=</span> name<span class="token punctuation">;</span>
		<span class="token keyword">this</span><span class="token punctuation">.</span>peripheral <span class="token operator">=</span> periph<span class="token punctuation">;</span>
	<span class="token punctuation">}</span>

	<span class="token keyword">public</span> Component <span class="token function">build</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
	<span class="token punctuation">{</span>
		<span class="token keyword">new</span> <span class="token class-name">Component</span><span class="token punctuation">(</span><span class="token keyword">this</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>

<span class="token keyword">public</span> <span class="token keyword">class</span> <span class="token class-name">Component</span> <span class="token punctuation">{</span>
	<span class="token keyword">private</span> string name<span class="token punctuation">;</span>
	<span class="token keyword">private</span> string peripheral <span class="token operator">=</span> “Undecided”<span class="token punctuation">;</span>
	<span class="token keyword">private</span> List<span class="token operator">&lt;</span>string<span class="token operator">&gt;</span> channels<span class="token punctuation">;</span>

	<span class="token keyword">public</span> <span class="token function">Component</span> <span class="token punctuation">(</span>ComponentBuilder component<span class="token punctuation">)</span>
	<span class="token punctuation">{</span>
		<span class="token keyword">this</span><span class="token punctuation">.</span>name <span class="token operator">=</span> component<span class="token punctuation">.</span>name<span class="token punctuation">;</span>
		<span class="token keyword">this</span><span class="token punctuation">.</span>peripheral <span class="token operator">=</span> component<span class="token punctuation">.</span>peripheral<span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<p><strong>If there are multiple builders, need the directory to cooperate.</strong></p>
<p><a href="https://en.wikipedia.org/wiki/Builder_pattern">https://en.wikipedia.org/wiki/Builder_pattern</a></p>
<pre class=" language-java"><code class="prism  language-java"><span class="token keyword">public</span>  <span class="token keyword">class</span> <span class="token class-name">Director</span>
<span class="token punctuation">{</span>
	<span class="token keyword">public</span> IBuilder <span class="token function">CreateBuilder</span><span class="token punctuation">(</span><span class="token keyword">int</span> type<span class="token punctuation">)</span>
	<span class="token punctuation">{</span>
		IBuilder builder <span class="token operator">=</span>  null<span class="token punctuation">;</span>
		<span class="token keyword">if</span>  <span class="token punctuation">(</span>type <span class="token operator">==</span>  <span class="token number">1</span><span class="token punctuation">)</span>
			builder <span class="token operator">=</span>  <span class="token keyword">new</span> <span class="token class-name">Builder1</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
		<span class="token keyword">else</span>
			builder <span class="token operator">=</span>  <span class="token keyword">new</span> <span class="token class-name">Builder2</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
		builder<span class="token punctuation">.</span><span class="token function">RunBuilderTask1</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
		builder<span class="token punctuation">.</span><span class="token function">RunBuilderTask2</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
		<span class="token keyword">return</span> builder<span class="token punctuation">;</span>
	<span class="token punctuation">}</span>
<span class="token punctuation">}</span>
</code></pre>
<p><img src="https://picasaweb.google.com/109606753991119733140/6572700798631275457#6572700802292667858" alt="enter image description here" title="builder diagram"></p>
<h6 id="factory-vs.-builder">Factory vs. Builder</h6>
<p>&lt;![if !supportLists]&gt;• &lt;![endif]&gt;Builder focuses on constructing a complex object step by step. Abstract Factory emphasizes a family of product objects (either simple or complex). Builder returns the product as a final step (product is built step by step, and call build to return in the final), but as far as the Abstract Factory is concerned, the product gets returned immediately.</p>
<ul>
<li>
<p>Builder often builds a Composite.</p>
</li>
<li>
<p>Often, designs start out using Factory Method (less complicated, more customizable, subclasses proliferate) and evolve toward Abstract Factory, Prototype, or Builder (more flexible, more complex) as the designer discovers where more flexibility is needed.</p>
</li>
</ul>
<p>Sometimes creational patterns are complementary: Builder can use one of the other patterns to implement which components get built. Abstract Factory, Builder, and Prototype can use Singleton in their implementations.</p>
<h3 id="prototype-pattern">Prototype Pattern</h3>
<p>The Prototype pattern creates a new object by cloning an existing object. The client using the prototype object does not need to know what kind of object it is dealing with as long as the concrete prototype extends or implements the prototype interface/class. The concrete prototype object is responsible for cloning itself and returning the cloned object.</p>
<p>This pattern involves implementing a prototype interface which tells to create a clone of the current object. This pattern is used when creation of object directly is costly. For example, an object is to be created after a costly database operation. We can cache the object, returns its clone on next request and update the database as and when needed thus reducing database calls.</p>
<p>SDA:</p>
<p>Create New Copy of Component. If creating from scratch is troublesome, need to load the list of channel and signals. Creating a copy is easy.</p>
<h3 id="observer-pattern-listener-pattern">Observer Pattern (Listener Pattern)</h3>
<p><a href="http://www.oodesign.com/observer-pattern.html">http://www.oodesign.com/observer-pattern.html</a></p>
<p>GUIs that auto-update their values when the underlying model/data they represent changes is one of the classic examples of using the Observer pattern.</p>
<p>Data binding is a generic term and it can be implemented using either Observer or Pub/Sub method</p>
<p>If you need presenters and views to be notified of changes to the model, you can implement the Observer pattern. For more information, see Related Patterns.</p>
<p>If the View and Model are can be binding one to one directly, data binding is the choice. If the Model change will affect a lot in view, use observer pattern to notify the presenter and update the view maybe better.</p>
<h3 id="composite-pattern">Composite Pattern</h3>
<p>链表式设计。每个链表的节点都是一个object。</p>
<p><a href="http://www.tutorialspoint.com/design_pattern/composite_pattern.htm">http://www.tutorialspoint.com/design_pattern/composite_pattern.htm</a></p>
<h3 id="adapter-pattern">Adapter Pattern:</h3>
<p>Provide a common interface for different implementations.</p>
<p><a href="https://sourcemaking.com/design_patterns/adapter/java/1">https://sourcemaking.com/design_patterns/adapter/java/1</a></p>
<p>For a particular object to contribute to the Properties view, adapters are used display the objects data. The view itself doesn’t need to know anything about the object the it is displaying properties for.</p>
<h3 id="interpreter-pattern">Interpreter Pattern</h3>
<p>SDA design: Signal name matching rules.</p>

