# Android Donations Lib

Android Donations Lib supports donations by Google Play Store, Flattr, PayPal, and Bitcoin.

It is used in projects, such as OpenKeychain, AdAway, FasterGPS, and NTPSync.

**NOTE: Google mailed me to remove PayPal donation capability when publishing on Google Play! Thus, you should build "product flavors" defined by the example: One version with Google Play donation capability and one with Paypal, Flattr, and Bitcoin!**

## How to use

1. Add dependency to your build.gradle:
    ```
    repositories {
        jcenter()
    }

    dependencies {
        compile 'org.sufficientlysecure:donations:2.6'
    }
    ```
2. Instantiate the fragment where you want to use it. Check out the example app for this: [DonationsActivity.java](https://github.com/sufficientlysecure/donations/blob/master/example/src/main/java/org/sufficientlysecure/donations/example/DonationsActivity.java)
3. Don't forget to pass through results in ``onActivityResult()`` back to the fragment as shown in [DonationsActivity.java](https://github.com/sufficientlysecure/donations/blob/master/example/src/main/java/org/sufficientlysecure/donations/example/DonationsActivity.java).
4. When publishing the app you must create managed in-app products for your app in the Google Play Store that matches the ones you defined in ``private static final String[] GOOGLE_CATALOG``

## Build flavors
1. Keep in mind that Google forbits other payment methods besides Google Play. Thus, in the example, two build flavors are used. Check out [ExampleApp/build.gradle](https://github.com/sufficientlysecure/donations/blob/master/example/build.gradle). The build script adds ``DONATIONS_GOOGLE`` to the auto generated BuildConfig.java.
2. Add ``<uses-permission android:name="android.permission.INTERNET" />`` to product flavors that use Flattr
3. Add ``<uses-permission android:name="com.android.vending.BILLING" />`` to product flavors that use Google Play In-app billing


## Screenshots

| Product Flavor: Google | Product Flavor: Fdroid |
|------------------------|------------------------|
| ![Screenshot](https://github.com/sufficientlysecure/donations/raw/master/screenshot-google.png) | ![Screenshot](https://github.com/sufficientlysecure/donations/raw/master/screenshot-fdroid.png) |

## Translations

Help translating on [Transifex](https://www.transifex.com/sufficientlysecure/donations/).

## Build Example App with Gradle

1. Have Android SDK "tools", "platform-tools", and "build-tools" directories in your PATH (http://developer.android.com/sdk/index.html)
2. Export ANDROID_HOME pointing to your Android SDK
3. Download Android Support Repository, and Google Repository using Android SDK Manager
4. Execute ``./gradlew build``

## Add the lib to your project

## Changelog
### 2.6
* Force Intent chooser for PayPal
* Min SDK 14

### 2.5
* Sync translations

### 2.4
* Fix NPE without billing service

### 2.3
* Publish to JCenter

### 2.2
* Updated build files
* Added bitcoin support (thanks to Oleg Vaskevich)

### 2.1
* Permissions are now defined per product flavor, they were removed from library's AndroidManifest

### 2.0
* Now uses Gradle Build System (http://tools.android.com/tech-docs/new-build-system)
* No xml configuration needed anymore!
* Fragment can be instantiated and used in any Activity.
* You can build "product flavors" defined by the ExampleApp: One version with Google Play Donation capability and one with Paypal and Flattr! (Google mailed me to remove PayPal donation capability when publishing on Google Play!)

## Contribute

Fork Android Donations Lib and do a pull request. I will merge your changes back into the main project.

