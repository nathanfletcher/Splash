# Splash Screens Done right ***:ok_hand:***
An example of a splash screen done the right way on Android

![](art/sample_splash.gif)

## Implementation

1. Create an xml resource file in the Drawable folder. We'll call ours ***backgroud_splash.xml***

```
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android">

    <item
        android:drawable="@color/gray"/>

    <item>
        <bitmap
            android:gravity="center"
            android:src="@mipmap/ic_launcher"/>
    </item>

</layer-list>
```

2. Next, you will set this as your splash activity’s background in the theme. Navigate to your ***styles.xml*** file and add a new theme for your splash activity:

```
<resources>

    <!-- Base application theme. -->
    <style name="AppTheme" parent="Theme.AppCompat.Light.DarkActionBar">
        <!-- Customize your theme here. -->
    </style>
    
    <!-- Splash screen style code is below -->
    <style name="SplashTheme" parent="Theme.AppCompat.NoActionBar">
        <item name="android:windowBackground">@drawable/background_splash</item>
    </style>

</resources>
```

3. Open your Manifest.xml and add this activity bit of code to it.
```
<activity
    android:name=".SplashActivity"
    android:theme="@style/SplashTheme">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />

        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity>
```

4. Finally, your SplashActivity class should just forward you along to your main activity:
*Note: i.e create a SplashActivity.java class and let it start an intent to open your MainActivity.java class when the splash screen is done, as shown below. Also note that SplashActivity.java class is your launcher activity*

```
public class SplashActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        
        Intent intent = new Intent(this, MainActivity.class);
        startActivity(intent);
        finish();
    }
}
```

Reference [Chris Stewart's blog post](https://www.bignerdranch.com/blog/splash-screens-the-right-way/)
