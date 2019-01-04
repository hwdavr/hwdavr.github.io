---


---

<p>android</p>
<p>fragment manager<br>
<a href="http://www.javacodegeeks.com/2013/06/android-fragment-transaction-fragmentmanager-and-backstack.html">http://www.javacodegeeks.com/2013/06/android-fragment-transaction-fragmentmanager-and-backstack.html</a></p>
<p><a href="http://stackoverflow.com/questions/7951730/viewpager-and-fragments-whats-the-right-way-to-store-fragments-state">http://stackoverflow.com/questions/7951730/viewpager-and-fragments-whats-the-right-way-to-store-fragments-state</a></p>
<p>Headless fragment<br>
<a href="http://luboganev.github.io/blog/headless-fragments/">http://luboganev.github.io/blog/headless-fragments/</a></p>
<p>Activity lifecycle</p>
<p><a href="http://developer.android.com/reference/android/app/Activity.html">http://developer.android.com/reference/android/app/Activity.html</a></p>
<p><a href="http://developer.android.com/reference/android/app/Activity.html#ProcessLifecycle">Your app will be in the background, onResume and onPause will both be called</a>, provided that the OS have enough memory to keep the new app and all the old apps.</p>
<ul>
<li>
<p>If you have a long running process that you need while the user not looking at it, use a service.</p>
</li>
<li>
<p>If you need the user to return the app in the same state, <a href="http://developer.android.com/reference/android/app/Activity.html#ActivityLifecycle">you need to do the work in onResume and onPause to save the state information and initialize your UI again</a> when the user comes back. If you are really worried that it can get killed (well, it shouldn’t lose the bundle I think), you can store them in SharePreferences for your app.</p>
</li>
<li>
<p>If you want to know when the app returns from that specific share intent, use startActivityForResult</p>
</li>
</ul>
<p>Fragment and activity<br>
<a href="http://www.androiddesignpatterns.com/2013/08/fragment-transaction-commit-state-loss.html">http://www.androiddesignpatterns.com/2013/08/fragment-transaction-commit-state-loss.html</a></p>
<p><a href="http://stackoverflow.com/questions/7992496/how-to-handle-asynctask-onpostexecute-when-paused-to-avoid-illegalstateexception">http://stackoverflow.com/questions/7992496/how-to-handle-asynctask-onpostexecute-when-paused-to-avoid-illegalstateexception</a></p>

