## What's the deal with this app?

The main focus of this application is to address **development strategies** related to native development on Android, such as important concepts such as **engagement**, **user experience** and good practices adopted in the **life cycle** developing an application with **quality** and **maturity**.

## User Experience


**UX** (User Experience) is a concept about how the user feels in each interaction with the solution, it goes beyond the building of beautiful interfaces. To have a good UX it is necessary (at least) to be concerned with elements of usability, components interactions, response time and feedback for the actions performed by the user, be assertive about the major application features, know the user profiles and understand the visual identity and sensations that the user is used to in their environment, e.g., Android mobile users have similar experiences and sensations even while navigating between different apps on their devices, because the applications tend to follow the Material UX Design, **launched by Google** at Google I/O 2014.

### Material Design

This application follows the UX concepts of *Material Design* which roughly speaking is a concept based on layers of paper sheets with "flat" colors and transitions with elegant effects closer to reality. Very efficient on mobile devices, also developed to adapt to different resolutions such as tablets and desktops.

Material Design was initially launched for the Lollipop version (and later), but it is now possible to use libraries that support the Material even for much older versions.
> To learn more about working with Material on pre-Lollipop devices, visit: [Android Material Design for Pre-Lollipop devices](https://goo.gl/Ubb09l)

[![Firebase Analytics](./analytics_lockups_horz_light.png)](https://firebase.google.com/features/analytics/)

UX is a process of continuous improvement, you need to create the [Personas](https://brasil.uxdesign.cc/por-que-criar-personas-bc796a1ffc7e) of your application, plus **understand how your users interact with it**. To help us in a practical and agile way through this evolutionary process, firebase provides an analysis tool, which allows us to have a **Heat Map** of our entire application, capturing the user's actions automatically, helping us to identify which ones are the most relevant actions/content to him, which can already be a "hook" also to work the **Retention** of users in your application.
> In the context of this app, for example, when a user adds a Marvel movie at their favorites, they become "categorized" as a Marvel movie fan and be notified when a trailer for any new Marvel movie is released and reopen the application (which may not have been accessed by the user in a while).

## Marketing

As the _Jelly Bean_ version still has a large share of the [market](https://developer.android.com/about/dashboards/index.html) the goal was to ensure that even users with this version of Android have the same experience as users with newer versions, which required extra development effort.

Another important factor to be considered in the development of applications is the **distribution**, in Android, the effort to have translations in different languages is minimal which makes it possible, in an easy way to distribute applications globally.

> For this application, two languages are being used, _English_ as the "default" option and _Portuguese_.

 
<img align="left" src=./proguard-snippets.png>In addition to preventing malicious users does reverse engineering in your code and have **access to sensitive data from your solution**, [Proguard](http://www.thiengo.com.br/proguard-android) also removes all unused code and other resources such as images, plus unused codes from third party libraries referenced in your app. Therefore, you have an application where no _hacker_ will have access to your information and will have an extremely light installation _apk_ file with **up to 70% of download size reduction** - _the case with this app_, what will avoid that old "I'll download it at home, on WiFi".
> For a starting point in the _Proguard_ study, two excellent videos from the _Android Performance Patterns_ channel helps a lot, one about [removing unused codes](https://www.youtube.com/watch?v=5frxLkO4oTM&index=17&list=PLWz5rJ2EKKc9CBxr3BVjPTPoDPLdPIFCE) and the other on how to [remove unused resources](https://www.youtube.com/watch?v=HxeW6DHEDQU&index=18&list=PLWz5rJ2EKKc9CBxr3BVjPTPoDPLdPIFCE).


## Ensuring application quality

Testing routines and error catching should be part of the daily-basis in the development cycle of an Android application, mainly due to the wide variety of devices available on the market, and to help with testing, some concepts/tools are widely used by experienced development teams:

- [**Crash Reporting**](https://www.youtube.com/watch?v=B7mlLVAkcfU) - Service/tool that captures untreated application errors and displays device details when the error has occurred, such as available memory, connection type, device model and so on.

- [**Automated Test Lab**](https://www.youtube.com/watch?v=4_ZEEX1x17k) - Service normally offered in the "cloud" that runs automated tests (created by the developer), plus automated tests - where crazy clicks are made on your app, using physical devices of different models.

- [**Remote access testing**](https://www.browserstack.com/) - Service also offered in the "cloud" where it is possible to choose between different types of physical devices and perform tests as if you have it in your hands.

> Other important elements are the maintenance of the _Alfa_ and _Beta_ versions for approval before publishing the applications to the official store.

<img align="left" src=./aws-device-farm.png> To automated testing and remote access testing, Amazon Web Services offers a very powerful suite of solutions, [AWS Device Farm](https://aws.amazon.com/en/device-farm/), where you can test and interact with Android, iOS and web apps on multiple devices at the same time.

> Since you only pay for use on AWS, _Device Farm_ becomes a very interesting option - compared to _browserstack_ $29/month, as automated tests are done in minutes, and are made via remote access, even that manual tests that do not take too long because their focus is to enable tests to **ensure that the app works as expected on devices that the developer(s) or tester(s) do not have**.


## Strategies for a safe and optimized development

During app development, you need to be aware of **memory management** - how much RAM your app requires, when (and how) it allocates and frees memory, to avoid undue memory allocation, which can negatively impact the user experience, causing **slowness and "crashes"** - the annoying [ANRs](https://developer.android.com/training/articles/perf-anr.html) - those "sickening" messages "displayed by the Operating System if the app takes too long to respond to a user's action.

An app developed without a focus on doing good memory management may cause what in the development world we call of _Memory Leaks_, something that usually causes errors in the application, ending it abruptly and unexpectedly, and these errors may vary depending on the device and the User Operating System.

<img align="left" src=./android-dev-pattern.png>Some design patterns apply in the world of Android development to avoid undesirable _Memory Leaks_, mainly in the use of _Inner Classes_, _AsyncTaks_ and _Runnables_ related to visualization elements that need to be updated after an asynchronous operation where _Context_ is passed for this class family, there is a lot information on this subject, but a good start, mainly to **avoid errors in "runtime"** is to understand how to reference _Context_ through [WeakReferences](http://www.androiddesignpatterns.com/2013/01/inner- class-handler-memory-leak.html).

<img align="left" src=./leakcanary.png>
 Even following the most diverse standards and best practices, the wide variety of Android devices it is **difficult for the developer to predict all scenarios** where a "memory leak" may occur and to assist *a lot* in this task it is recommended to use [LeakCanary](https://medium.com/square-corner-blog/leakcanary-detect-all-memory-leaks-875ff8360745) - a plugin that automatically detects _memory leaks_ in your development phase.


Another standard worth studying is the [Retained Fragments](http://www.androiddesignpatterns.com/2013/04/retaining-objects-across-config-changes.html), because in addition to helping to avoid _ANRs_, the UX improvement, in terms of response time, makes asynchronous data continue to be "loaded" even if the user navigates to another application functionality.
> For devs: Whenever a new _Activity_ is added to the _Foreground_ of the _Back Stack_, the previous _Activity_ is destroyed only on some special occasions, e.g. if the OS needs more resources and when it is not destroyed, even if it is not in _foreground_ (being used by the user). With _Retained Fragments_ it's possible to capture the data after a response from an _AsyncTask_ in a _Listener_ and, when the user returns to that _Activity_ the data will already be loaded. _Cool huh?_


We cannot forget the good old _ViewHolder_ standard that **must** be used when it is necessary to display a list of items so that there is **better memory reuse**. Without using this pattern, each item in the list allocates a _X_ memory space to "assemble" its view and if the list the user is browsing has 200 items, by example, the total space allocated will be _X_ * 200! With this pattern, only the items that are initially displayed on the user's device screen allocate a memory space to create the visualization, that is, for a device where five items are displayed on the screen, even if it has 200 items, the total space allocated will be _X_ * 5!
> Facebook, WhatsApp, and Snapchat can use as many memory they want on the user's cell phone, but your not-so-glamorous app cannot... If the user sees your app among the most memory-consuming (which is pretty easy to verify) you may lost this user forever.


## And what else?

There are some cool things that have not yet been done in this app (_a day who knows ..._) but I believe that I'm working with essential items/strategies to have a professional application, which makes it possible to maintain the source code without headaches and achieve good retention rates and user engagement.

### Strategically speaking...

Before "getting your hands dirty", how about prototyping? Choosing a good tool for creating _Wireframes_ and _Mockups_ will help you create proofs of concept for your app before starting its implementation, and with that you can do **A/B Tests** with some [mapped user segments](http://startupsorocaba.com/tag/value-proposition-canvas/), for example, collecting feedbacks and making improvements to the UX of your app before starting the expensive ($$$) development process.

Drawing up plans for user engagement, understanding a little about **bounce rates** and **conversion** are fundamental to your app's marketing - _you don't want to develop an app with a monstrous performance, that has no errors, but that is only installed by friends and family_. Take a look at [the main Digital Marketing metrics for your application](http://resultadosdigitais.com.br/blog/metricas-de-marketing-digital-for-mobile-apps /)


### Technically speaking...

Working with some **MVP standard** on Android is essential for good maintainability of the app, the articles [MVP on Android - Tin Megali](http://www.tinmegali.com/en/model-view-presenter-mvp-no-android-introducao/) and [MVP Android - Vinícius Thiengo](http://www.thiengo.com.br/mvp-android) are excellent references about this topic.

There are many libraries that assist in Android development, in this app some were not used that are worth the study:
- [Retrofit](http://square.github.io/retrofit/) - It is extremely simple, fast, and efficient to perform HTTP requests from your app and has excellent documentation, widely used for communication with REST APIs.
- [Dagger 2](https://github.com/google/dagger) - Library that allows Dependency Injection on Android. To learn more about Dagger 2 and the concepts of Dependency Inversion and Dependency Injection, I recommend a read in this [Introduction to Dagger 2](https://medium.com/android-dev-br/introdu%C3%A7%C3%A3o-ao-dagger-2-56d193118a6c) article.
- [Butter Knife](http://jakewharton.github.io/butterknife/) - Focused on productivity, this library makes use of *Annotations* to inject *Views* into Android components, which makes it possible to write code in a way much more succinct in various scenarios, avoiding several *Boiler Plate* codes, such as `activity.subtitle = (android.widget.TextView) activity.findViewById(R.id.subtitle);` for example.

<img align="left" src=./Kotlin-logo.png> The Android team, at the Google I/O 2017 keynote announced [official support for Kotlin](https://blog.jetbrains.com/kotlin/2017/05/kotlin-on-android-now-official/), which is a huge motivation for anyone interested in this new, modern, and powerful development language. Kotlin has many advantages over Java's verbose syntax and avoids several errors that happen at *runtime* in Java (like the famous *NullPointerExceptions*). Kotlin is *Null Safety* (less bugs in your app), **extremely productive* *and has a very short learning curve, in addition to having excellent (and interactive) documentation on the [official website](http://kotlinlang.org/docs/reference/).