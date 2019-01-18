# RxJava

## Install

add this line `implementation "io.reactivex.rxjava2:rxjava:2.x.y"` in your gradle and sync

[RxJava on Github](https://github.com/ReactiveX/RxJava)

## Convert AsyncTask to RxJava

```java

Observable.fromCallable(() -> {
    Request request = new Request.Builder()
            .url(url)
            .build();
    try {
        Response response = sHttpClient.newCall(request).execute();
        return response.isSuccessful();
    } catch (IOException e) {
        Log.e("Network request", "Failure", e);
    }

    return false;
})
.subscribeOn(Schedulers.io())
.observeOn(AndroidSchedulers.mainThread())
.subscribe((result) -> {
    //Use result for something
});

```

## Reference

* [How to convert an AsyncTask to RxJava](https://android.jlelse.eu/how-to-convert-an-asynctask-to-rxjava-80e5d777a40)
