# QUICKSTART

SETUP DEEPLINK IN FLUTTER


## ANDROID
1.  Open the Flutter project with Android Studio or VSCode.
2.  Navigate to  `android/app/src/main/AndroidManifest.xml`  file
3.  Add the following metadata tag and intent filter inside the  `<activity>`  tag with  `.MainActivity`
```
intent-filter android:autoVerify="true">
<action android:name="android.intent.action.MAIN"/>
<category android:name="android.intent.category.LAUNCHER"/>undefined</intent-filter>undefined<meta-data android:name="flutter_deeplinking_enabled" android:value="true" />undefined<intent-filter android:autoVerify="true">
<action android:name="android.intent.action.VIEW" />
<category android:name="android.intent.category.DEFAULT" />
<category android:name="android.intent.category.BROWSABLE" />
<data android:scheme="https"/>
<data android:host="berkah.app"/>undefined</intent-filter    >
```
4.  Get SHA256 Fingerprint
Mac :
	```
	keytool -list -v -keystore ~/.android/debug.keystore -alias androiddebugkey -storepass android -keypass android
	```
	Windows :
	```
	-
	```
	Linux :
	```
	-
	```
5. Config `assetlinks.json`
	The hosted file should look similar to this:
	```
	[
	  {
    "relation": [
      "delegate_permission/common.handle_all_urls"
    ],
    "target": {
      "namespace": "android_app",
      "package_name": "com.example.deeplink_cookbook",
      "sha256_cert_fingerprints": [
        "FF:2A:CF:7B:DD:CC:F1:03:3E:E8:B2:27:7C:A2:E3:3C:DE:13:DB:AC:8E:EB:3A:B9:72:A1:0E:26:8A:F5:EC:AF"
				]  
	        }  
	    }
	]
	```

	  1.  Set the  `package_name`  value to your Android application ID.
    
	2.  Set sha256_cert_fingerprints to the value you got from the previous step.
    
	3.  Host the file at a URL that resembles the following:  `<webdomain>/.well-known/assetlinks.json`
    
	4.  Verify that your browser can access this file.
	
6. Testing
	```
	adb shell 'am start -W -a android.intent.action.VIEW -c android.intent.category.BROWSABLE -d "https://yourdomain.com"'
	```
    

##

	
## IOS
Cooming Soon.


