# Android Donations Lib

Android Donations Lib supports donations by Google Play Store, PayPal, and Flattr.

It is used in my projects AdAway, FasterGPS, and NTP-Sync.

# Contribute

Fork Android Donations Lib and do a pull request. I will merge your changes back into the main project.

# Screenshot

![Screenshot](http://github.com/dschuermann/android-donations-lib/raw/master/screenshot.png)

# Add the lib to your project

* New -> Android Project -> Create project from existing source, choose org_donations 
* Add org_donations as Android Lib (Properties of your project -> Android -> Library -> add org_donations as android library)
* Add the following lines to your AndroidManifest for permissions:

```xml
<uses-permission android:name="android.permission.INTERNET" />
<!-- Required permission to use Google Play Store donations -->
<uses-permission android:name="com.android.vending.BILLING" />
```

* Add the following lines to your AndroidManifest the activity:

```xml
<activity
    android:name="org.donations.DonationsActivity"
    android:excludeFromRecents="true"
    android:label="Donations"
    android:launchMode="singleTask"
    android:theme="@style/Theme.Dialog" />

<!-- - Google Play Store donations -->
<service android:name="org.donations.google.BillingService" />

<receiver android:name="org.donations.google.BillingReceiver" >
    <intent-filter>
        <action android:name="com.android.vending.billing.IN_APP_NOTIFY" />
        <action android:name="com.android.vending.billing.RESPONSE_CODE" />
        <action android:name="com.android.vending.billing.PURCHASE_STATE_CHANGED" />
    </intent-filter>
</receiver>
```

* Configure the Donations Lib by altering the file src/org/donations/DonationsConfiguration.java
* Integrate this activity in your app by opening it as an intent:

```java
startActivity(new Intent(this, DonationsActivity.class));
```

* When publishing the app you have to create in-app products for your app in the Google Play Store that matches the ones you defined in DonationsConfiguration.java