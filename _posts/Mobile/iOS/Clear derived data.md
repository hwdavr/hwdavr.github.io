---


---

<p><a href="https://stackoverflow.com/questions/25133039/xcode-6-isnt-autocompleting-in-swift">https://stackoverflow.com/questions/25133039/xcode-6-isnt-autocompleting-in-swift</a></p>
<pre><code>#!/bin/bash

echo "Start fixing xCode"
echo "Closing xCode"
osascript -e 'tell app "Xcode" to quit'
sleep 2
echo "Clearing DerivedData..."
rm -rf "$HOME/Library/Developer/Xcode/DerivedData"
sleep 2
echo "Launch xCode again"
osascript -e 'tell app "Xcode" to run'
echo "Finish fixing xCode"
</code></pre>

