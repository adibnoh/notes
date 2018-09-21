# Snippet

## Check Internet Connection

```java

public Boolean getConnection() {

    ConnectivityManager connectivityManager = (ConnectivityManager) getSystemService(Context.CONNECTIVITY_SERVICE);
    if (connectivityManager.getNetworkInfo(ConnectivityManager.TYPE_MOBILE).getState() == NetworkInfo.State.CONNECTED ||
        connectivityManager.getNetworkInfo(ConnectivityManager.TYPE_WIFI).getState() == NetworkInfo.State.CONNECTED) {
        //we are connected to a network
        return true;
    } else {
        return false;
    }

}



```

## Detect Device Rotation

```java

@Override
public void onConfigurationChanged(Configuration newConfig) {

    Log.d(TAG, "config changed");
    super.onConfigurationChanged(newConfig);
    int orientation = newConfig.orientation;
    if (orientation == Configuration.ORIENTATION_PORTRAIT) {
        // restore = true;
        Log.d(TAG, "Portrait");
    } else if (orientation == Configuration.ORIENTATION_LANDSCAPE) {
        // restore = true;
        Log.d(TAG, "Landscape");
    }
    else {
        // restore = true;
        Log.w(TAG, "other: " + orientation);
    }

}


```