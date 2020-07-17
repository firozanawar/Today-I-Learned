Android R, we can log the exit reason of Android App using ActivityManager. Below id the code snippts..

```
val am = applicationContext.getSystemService(Context.ACTIVITY_SERVICE) as ActivityManager
        val exitList = am.getHistoricalProcessExitReasons(applicationContext.packageName, 0, 1)

        if (exitList.isNotEmpty()) {
            val lastExitInformation: ApplicationExitInfo = exitList.first()
            Log.d(TAG, "Reason: ${lastExitInformation.reason}")

            Log.d(TAG, "Timestamp: ${lastExitInformation.timestamp}")

            lastExitInformation.description?.let {
                Log.d(TAG, "Description: ${it}")
            }

            textView.text = lastExitInformation.reason.toString()
        }
```

```
Output:-

- MainActivity: Reason: 14
- MainActivity: Timestamp: 1589627622761
- MainActivity: Description: crash
```

### The reason code and its meaning are,

```
const val REASON_ANR = 6
const val REASON_CRASH = 4
const val REASON_CRASH_NATIVE = 5
const val REASON_DEPENDENCY_DIED = 12
const val REASON_EXCESSIVE_RESOURCE_USAGE = 9
const val REASON_EXIT_SELF = 1
const val REASON_INITIALIZATION_FAILURE = 7
const val REASON_LOW_MEMORY = 3
const val REASON_OTHER = 13
const val REASON_PERMISSION_CHANGE = 8
const val REASON_SIGNALED = 2
const val REASON_UNKNOWN = 0
const val REASON_USER_REQUESTED = 10
const val REASON_USER_STOPPED = 11
```

Happy learning.