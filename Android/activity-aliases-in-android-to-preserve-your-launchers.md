### Introduction:-
If you create your app shortcut on luncher and then changed to another activity as a LAUNCHER activity then shortcut gets destroyed. To preserve that we can use activity-alias in AndroidManifest to preserve the state.

```
<activity android:name=".OldActivity"/>
<activity android:name=".NewActivity"/>
<activity-alias
        android:name=".MainActivity"
        android:targetActivity=".OldActivity">
    <intent-filter>
        <action android:name="android.intent.action.MAIN" />

        <category android:name="android.intent.category.LAUNCHER" />
    </intent-filter>
</activity-alias>
```

### Other features provided by <activity-alias>
```
<activity-alias android:enabled=["true" | "false"]
                android:exported=["true" | "false"]
                android:icon="drawable resource"
                android:label="string resource"
                android:name="string"
                android:permission="string"
                android:targetActivity="string" >
    . . .
</activity-alias>
```

Happy learning :)