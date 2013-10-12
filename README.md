# Android Donations Lib

Android Donations Lib supports donations by Google Play Store, PayPal, and Flattr.

It is used in my projects AdAway, FasterGPS, and NTP-Sync.

## NEWS

* Now uses Gradle Build System (http://tools.android.com/tech-docs/new-build-system)
* No xml configuration needed anymore!
* Fragment can be instantiated and used in any Activity.
* You can build "product flavors" defined by the ExampleApp: One version with Google Play Donation capability and one with Paypal and Flattr! (Google mailed me to remove PayPal donation capability when publishing on Google Play!)

## Contribute

Fork Android Donations Lib and do a pull request. I will merge your changes back into the main project.

## Screenshot

![Screenshot](http://github.com/dschuermann/android-donations-lib/raw/master/screenshot.png)

## Build Example App with Gradle

1. Have Android SDK "tools", "platform-tools", and "build-tools" directories in your PATH (http://developer.android.com/sdk/index.html)
2. Export ANDROID_HOME pointing to your Android SDK
3. Install gradle
4. Download Android Support Repository, and Google Repository using Android SDK Manager
5. Execute ``gradle wrapper`` (http://www.gradle.org/docs/current/userguide/gradle_wrapper.html)
6. Execute ``./gradlew assemble``

## Add the lib to your project

* The ExampleApp depends on "libraries/Donations" and has two product flavors defined in its gradle configuration.
* See [ExampleApp/build.gradle](https://github.com/dschuermann/android-donations-lib/blob/master/ExampleApp/build.gradle) how to build different product flavors. The build script adds ``DONATIONS_GOOGLE`` to the auto generated BuildConfig.java.
* See [DonationsActivity.java](https://github.com/dschuermann/android-donations-lib/blob/master/ExampleApp/src/main/java/org/sufficientlysecure/donations/example/DonationsActivity.java) how to instantiate the Fragment based on ``DONATIONS_GOOGLE``.
* When publishing the app you have to create _unmanaged_ in-app products for your app in the Google Play Store that matches the ones you defined in ``private static final String[] GOOGLE_CATALOG``
* Add ``<uses-permission android:name="android.permission.INTERNET" />`` to product flavors that use Flattr
* Add ``<uses-permission android:name="com.android.vending.BILLING" />`` to product flavors that use Google Play In-app billing