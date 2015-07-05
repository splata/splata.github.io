---
layout: post
title: How to migrate an old Android Studio project in Gradle
---

The most common issue that affects users is the runProguard property changing names to `minifyEnabled`. If you run into the build error

> Gradle DSL method not found: 'runProguard()'

then this is the cause of your build error.

This crops up a lot because that property was inserted into all projects created by Android Studio prior to version 0.14.0.

To update your project, edit your build.gradle file as follows:

{% highlight js %}
         }
         release {
-            runProguard true
+            minifyEnabled true
             proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.txt'
{% endhighlight %}

[Source:](http://tools.android.com/tech-docs/new-build-system/migrating-to-1-0-0)