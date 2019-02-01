# Local Authentication ANE for Android+iOS
With a 100% identical AS3 API, you can easily use local authentication on Android and iOS devices which support this feature.

**Main Features:**

* Supports fingerprint API on Android and iOS.
* On iOS devices with the Face ID feature, it will use Face ID instead.
* gracefuly takes care of error messages and you can customize the messages in dialogs.

[find the latest **asdoc** for this ANE here.](http://myflashlab.github.io/asdoc/com/myflashlab/air/extensions/localAuth/package-detail.html)

# AIR Usage
For the complete AS3 code usage, see the [demo project here](https://github.com/myflashlab/LocalAuth-ANE/blob/master/AIR/src/Main.as).

```actionscript
import com.myflashlab.air.extensions.localAuth.*;

// this is the first thing you should do to initialize the ANE
LocalAuth.init();

// add listeners to know the authentication result
LocalAuth.listener.addEventListener(LocalAuthEvents.AUTHENTICATION, onAuthentication);
LocalAuth.listener.addEventListener(LocalAuthEvents.ERROR, onAuthError);

function onAuthentication(e:LocalAuthEvents):void
{
	trace("success: " + e.success);
}

function onAuthError(e:LocalAuthEvents):void
{
	trace("error: " + e.error.name + " - " + e.error.message);
}

// check if the current device supports any kind of biometrics
var result:Boolen = LocalAuth.canCheckBiometrics;

// get an Array of supported Biometrics
var list:Array = LocalAuth.getAvailableBiometrics();

// finally call this method to start the authentication
// read the details of the optional parameters to know how you can customize the default messages in dialogs
// http://myflashlab.github.io/asdoc/com/myflashlab/air/extensions/localAuth/LocalAuth.html#authenticateWithBiometrics()
LocalAuth.authenticateWithBiometrics("Security check!");
```

# Air .xml manifest
```xml
<!--
FOR ANDROID:
-->
<uses-permission android:name="android.permission.USE_FINGERPRINT"/>
<uses-sdk android:targetSdkVersion="26"/>






<!--
FOR iOS:
-->
<key>NSFaceIDUsageDescription</key>
<string>Why is my app authenticating using face id?</string>
	
	
	
	
	
<!--
Embedding the ANE:
-->
  <extensions>
	<extensionID>com.myflashlab.air.extensions.localAuth</extensionID>
	
	<!-- dependency ANEs https://github.com/myflashlab/common-dependencies-ANE -->
	<extensionID>com.myflashlab.air.extensions.dependency.overrideAir</extensionID>
	<extensionID>com.myflashlab.air.extensions.dependency.androidSupport.core</extensionID>
	<extensionID>com.myflashlab.air.extensions.dependency.androidSupport.v4</extensionID>
  </extensions>
-->
```

# Requirements
* Android API 19+
* iOS SDK 8.0+
* AIR SDK 31.0+

# Tutorials
[How to embed ANEs into **FlashBuilder**, **FlashCC** and **FlashDevelop**](https://www.youtube.com/watch?v=Oubsb_3F3ec&list=PL_mmSjScdnxnSDTMYb1iDX4LemhIJrt1O)  

# Premium Support #
[![Premium Support package](https://www.myflashlabs.com/wp-content/uploads/2016/06/professional-support.jpg)](https://www.myflashlabs.com/product/myflashlabs-support/)
If you are an [active MyFlashLabs club member](https://www.myflashlabs.com/product/myflashlabs-club-membership/), you will have access to our private and secure support ticket system for all our ANEs. Even if you are not a member, you can still receive premium help if you purchase the [premium support package](https://www.myflashlabs.com/product/myflashlabs-support/).