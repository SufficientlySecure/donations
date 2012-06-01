# Android Donations Lib

Android Donations Lib supports donations by Google Play Store, PayPal, and Flattr.

It is used in my projects AdAway, FasterGPS, and NTP-Sync.

# Contribute

Fork Android Donations Lib and do a pull request. I will merge your changes back into the main project.

# Screenshot

![Screenshot](http://github.com/dschuermann/android-donations-lib/raw/master/screenshot.png)

# Add the lib to your project

1. New -> Android Project -> Create project from existing source, choose org_donations 
2. Add org_donations as Android Lib (Properties of your project -> Android -> Library -> add org_donations as android library)
3. Add the following lines to your AndroidManifest for permissions:

```xml
<uses-permission android:name="android.permission.INTERNET" />
<!-- Required permission to use Google Android Market donations -->
<uses-permission android:name="com.android.vending.BILLING" />
```

4. Add the following lines to your AndroidManifest the activity:

```xml
<activity
    android:name="org.donations.DonationsActivity"
    android:excludeFromRecents="true"
    android:label="Donations"
    android:launchMode="singleTask"
    android:theme="@style/Theme.Dialog" />

<!-- - Google Android Market donations -->
<service android:name="org.donations.google.BillingService" />

<receiver android:name="org.donations.google.BillingReceiver" >
    <intent-filter>
        <action android:name="com.android.vending.billing.IN_APP_NOTIFY" />
        <action android:name="com.android.vending.billing.RESPONSE_CODE" />
        <action android:name="com.android.vending.billing.PURCHASE_STATE_CHANGED" />
    </intent-filter>
</receiver>
```

5. Configure the Donations Lib by altering the file src/org/donations/DonationsConfiguration.java
6. Open the activity in your app:

```java
startActivity(new Intent(this, DonationsActivity.class));
```