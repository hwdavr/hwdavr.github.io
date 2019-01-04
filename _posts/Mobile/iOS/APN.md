---


---

<h2 id="apn-setup">APN setup:</h2>
<p><a href="https://mobiforge.com/design-development/programming-apple-push-notification-services">https://mobiforge.com/design-development/programming-apple-push-notification-services</a></p>
<p><a href="http://apns-gcm.bryantan.info/">http://apns-gcm.bryantan.info/</a></p>
<h3 id="push-notification-in-background-mode">Push Notification in Background mode</h3>
<p><a href="https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/pushing_updates_to_your_app_silently">https://developer.apple.com/documentation/usernotifications/setting_up_a_remote_notification_server/pushing_updates_to_your_app_silently</a><br>
<a href="https://medium.com/posts-from-emmerge/ios-push-notification-background-fetch-demystified-7090358bb66e">https://medium.com/posts-from-emmerge/ios-push-notification-background-fetch-demystified-7090358bb66e</a></p>
<ul>
<li>FCM issue<br>
<a href="https://stackoverflow.com/questions/37899712/fcm-background-notifications-not-working-in-ios">https://stackoverflow.com/questions/37899712/fcm-background-notifications-not-working-in-ios</a><br>
I fixed my issue by deleting the  <code>FirebaseAppDelegateProxyEnabled</code>  key from  <code>Info.plist</code>  and updating the APNs certificates.<br>
Now it works perfectly using  <code>"content_available": true</code>to receive messages while application is in background.<br>
<a href="https://stackoverflow.com/questions/49423251/ios-fcm-push-notifications-not-working-in-background-state-in-swift">https://stackoverflow.com/questions/49423251/ios-fcm-push-notifications-not-working-in-background-state-in-swift</a><br>
To receive push notification in background mode there must be “mutable-content” key with value “1” or true is present in you payload format.</li>
</ul>

