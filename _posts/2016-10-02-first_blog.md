---
layout: post
title: Android&#58 How to use Toast in a background thread
---
In order to show a toast, we need to call the [show()](https://developer.android.com/reference/android/widget/Toast.html#show()) method in the [Toast](https://developer.android.com/reference/android/widget/Toast.html) class. That method actually shows a [View](https://developer.android.com/reference/android/view/View.html), so we need to call it on the main thread.
You can use {% highlight java %}new Handler(Looper.getMainLooper()){% endhighlight %} to generate a main thread handler from any background thread, then use it to post toast to main thread.

The following code can be used to show toast in a background thread:
{% highlight java %}
public static void backgroundToast(final Context context,
        final String msg) {
    if (context != null && msg != null) {
        new Handler(Looper.getMainLooper()).post(new Runnable() {

            @Override
            public void run() {
                Toast.makeText(context, msg, Toast.LENGTH_SHORT).show();
            }
        });
    }
}
{% endhighlight %}