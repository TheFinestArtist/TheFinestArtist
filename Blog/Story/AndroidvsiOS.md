# Android vs iOS

I do not know how many developers in the world have ability to build proper Android and iOS applications at the same time. Since I have experience in developing and publishing both Android and iOS applications, I would like to compare these two platforms.

To tell more about me, I have experience in developing Android applications for 5 years and iOS applications for 4 years. You would probably find more about my experience at my [portfolio page](http://thefinestartist.com/projects/). Some of my projects are open sourced: [BTTENDANCE](https://github.com/orgs/Bttendance/dashboard).

Due to the fact that most of people living in my country uses Android phone, I have more strength in developing Android applications. But I found developing iOS applications is twice easier than building Android applications because of following reasons.



## Android phone and iPhone phone version distribution
As you may already know, [Android version distribution](http://developer.android.com/about/dashboards/index.html#Platform) is dirtier than [iOS version distribution](https://developer.apple.com/support/app-store/). The latest version of Android which is Marshmallow (API 23) takes 0.3% of whole platform version while the latest version if iOS which is iOS9 takes 70% of whole platform versions. I don't know why Google made this new version called Marshmallow if 0.3% of users are using it! While I live in a country which most people uses Android, I have never seen anyone updates their Android OS and it seems [Apple is winning Samsung](http://pocketnow.com/2015/01/22/apple-samsung-market-share-korea) in South Korea. Even though Google releases new version of Android, you can not update the OS right away because the vender such as Samsung, LG, Sony, Huawei, Xiaomi have to update their customized OS with newly released version of Android for each devices they made. This updating process usually takes months and vender even decide not to update their OS for most of their devices because in this way they can make people to buy new phone if they want to use new OS.

Due to these reasons, Android developers including Android SDK developers who works for Google, Android application developers and Android open source library developers have to make their applications and API to work from the version Eclair (API 7) or Ice Cream Sandwich (API 15). For your information, [Eclair was released at Oct, 2009](https://en.wikipedia.org/wiki/Android_Eclair) and [Ice Cream Sandwich was released at Oct, 2011](https://en.wikipedia.org/wiki/Android_Ice_Cream_Sandwich). This fact makes Android development really difficult because you have to support device which is almost 6 years old.



## Android phone and iPhone screen size
This website shows the [list of Android devices and their sceen sizes](http://www.emirweb.com/ScreenDeviceStatistics.php). This shows [iPhone screen sizes](http://www.paintcodeapp.com/news/ultimate-guide-to-iphone-resolutions). I can see there is only 4 kinds of resolutions for iPhone but do you know how many resolutions Android developers have to support? Supporting all kinds of resolutions makes developer really difficult and tricky to develop their application layout properly. Supporting all kinds of resolutions also gives designer more work and they have to be aware of [how to support multiple screens](http://developer.android.com/guide/practices/screens_support.html). This variety in device resolutions probably is good marketing point for Android devices, but at the same time it makes Android design not so perfect:designers can't design every single layout for all kinds of resolutions and developer as well. On the other hand, since iPhone has only 4 kinds of resolutions, designers can design for 4 kinds of resolutions which makes their app beautifully designed.
Android suggest to use many kinds of resources according to device size, orientation, and etc. For example `values-land` is for landscape resources and `values-v21` is for recourses API higher than 21. There can be a lot of combinations such as `values-land-v21` or `values-land-v10`. This looks like very cool feature because you can customize all the recourses for various kinds of devices. But usually, developer use this for only these three `values-v21`, `values-land` and `values-sw600` folders. And the value itself is like CSS, cascading which makes this system confusing.



## Android Studio vs Xcode
Android Studio is [IDE](https://en.wikipedia.org/wiki/Integrated_development_environment) for Android development and Xcode is IDE for iOS development. The first stable version of [Android Studio was released at Dec 2014](https://en.wikipedia.org/wiki/Android_Studio). The current version of Android Studio is 1.5 while the current version of Xcode is 7.1.1. Version 1.5 vs 7.1.1 is huge. Even though Android Studio supports many cool features than Eclipse, it stills has some issues. The biggest issue is Android Studio is pretty slow and it uses huge portion of CPU. It is not stable, sometimes it turns off unexpectedly. Sometimes, the layout rendering doesn't work: Mostly when you use custom views in your layout, it fails to show the preview. If you change single letter in the build.gradle file, Android Studio makes me to sync with newly updated gradle, even though I added new line or just a space. The build time is very slow, I think it is slower than Eclipse. Even though it succeeded in building a project, it somehow stuck in the middle and do nothing for a while: Mostly adb needs more time to send complied APK file to the device. I don't think the adb isn't stable either.

Xcode also have some problems such as xib loading time is too long. It is even takes longer if it has a lot of views in the xib. Sometimes just open a file takes some time. Worst part is they uses main thread to open up a file, which makes you can't do anything while Xcode figure out how to open a file.


## Design Pattern (Model View Controller)
iOS suggest and induce their developer to follow model view controller pattern: sometimes it is called model view presenter. They also distinguished and named their files to follow this pattern. UIViewController for controller, xib or UIView for view and simple object for model. On the other hand, Android is so messy about this pattern. They have Activity and Fragment which works like a controller but actually it it not. Activity is like some kind of mixture between controller, life cycle callbacks, linking the views and extending the application context. Fragment is actually just a view which have life cycle callback of Activity.


## ListView & RecyclerView vs UITableViewController
UITableViewController is one of the most amazing view controller which iOS supports. It is actually just a UIViewController with UITableView in it but it has all kinds of callbacks, usually called delegates or datasource, which allows developer to customize their tableview a lot easier. Android used to have ListView which is similar with TableView. But ListView always needs an Adapter to show some data and view items. There is so many kinds of Adapters in Android which makes Android development confusing. They made a updated version of ListView called RecyclerView, which makes really annoying for developers. You have to know refactor the code using ListView to RecyclerView. RecyclerView has made cool features such as customizing animations, choosing the scroll orientation using Layout Manager, new kinds of adapter which is RecyclerView.Adapter and etc. But it is really hard to understand what kind of features are in the new View and how does it work.

I think Android tried to calculate the view height, animations of each item and separate each features such as handling objects, binding views, animating views, type of the scrollview and etc. Unfortunately, it makes really hard to understand what RecyclerView will doing in the background with all of those informations.

Handling models and views at the same place, calculating the height of view, calculating the number of items or sections and etc makes developer feel like that I am controlling this view and knows what will gonna happen if I change this or that. And it is what exactly UITableViewController do. Awesome.


## Models

#### Getter & Setter
For iOS, getter & setter ends with one line. `@property` automatically creates getter & setter for developer and also can change the name of the method.
```objc
@property (getter=isFinished setter=setFinished) BOOL finished;
```

For Android, it needs 7 lines plus 2 more lines for indenting.
```Java
boolean finished;

public void setFinished(boolean finished) {
   this.finished = finished;
}

public boolean isFinished() {
   return this.finished;
}
```

In Java, you are not recommended to use dot notation. But in Objective-C, dot notation actually calls the getter or setter method for you unlike Java, C, C++, which makes it is safe to use dot notation and also it looks far more simpler.


#### Atomic
You can make all objects in Objective-C atomic simply by adding `atomic` in `@property` setting.
```objc
@property (atomic, retain) NSNumber *count
```

In Java, you have to use `AtomicInteger` which extends `Number` and which made auto-boxing the number.


## EventBus vs Notification
iOS supports `Notification` class which has authority to notify any of the class if something happens. But Java doesn't have these system. There is two major open source libraries for this one is called `EventBus` and another is called `Otto`.
But the problem is it is happens in this case. You get some notification or event from background thread and you updated some UI without awaring this code block is not running UI thread. In this case, Android application actually runs very well which should give you an Exception. And the updated UI itself shows very strange behavior such as some part of view is missing, some part of view doesn't catch events or etc. You need days or weeks to find out this bug because you can't even guess that some code block is updating UI in background thread without causing any exception.


## Emulator & Genymotion vs Simulator
Emulator is an Android virtual device provided by Google. It is pretty slow and I think developers are hardly using it. Genymotion is also and Android virtual device provided by Genymotion. It is better than Android Emulator but it is still slow and you have to pay for the pro version and it is not covering all the APIs from 8 to 23. So, basically you need your own Android devices to test your app or code.

Simulator is an iOS virtual device provided by Apple. When you runs Simulator you would find out you don't need any iPhone because Simulator is fast enough and works like the real iPhone. A few features are missing but it still good enough.


## Android Device Monitor vs Activity Monitor


## Gradle vs CocoaPods


##




* Mostly iOS app is much more beautiful than Android app.
* Many mobile developer in USA are iOS developer. There are many Android developer in other country. But Apple and Google both are based on USA.



* Mostly Android Phone has better hardware than iPhone. But Android OS is so stupid, so people usually think iPhone is way more faster than Android.


* No matter how I code Objective-C it runs beautifully or get crashed.
* No matter how I code Android it runs stupidly or have bugs which I don't know where it comes from.


* Xcode finds most of the errors in it's compile time.
* Android Studio
