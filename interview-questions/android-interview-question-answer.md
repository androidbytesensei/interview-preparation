---
description: >-
  Originally posted on Medium here -
  https://medium.com/@harshitabambure/android-interview-question-answer-8d4857c4bc82
---

# Android Interview Question Answer

### What is the Intent?

The intent is used to navigate from one activity to another activity and is also used to get user input. The intent is the message that is passed between components such as activities, content providers, broadcast receivers, services, etc.

### What is manifest?

The AndroidManifest.xml file contains information about your package, including components of the application such as activities, services, broadcast receivers, content providers, etc.

### What is an adapter?

The adapter is used to bind data and show listings to the screen.

### What are services?

A Service is an application component that can perform long-running operations in the background. It does not provide a user interface. … For example, a service can handle network transactions, play music, perform file I/O, or interact with a content provider, all from the background.

### What is an abstract class?

An abstract class is a class that is declared abstract — it may or may not include abstract methods. Abstract classes cannot be instantiated, but they can be subclassed.

An abstract method is a method that is declared without an implementation (without braces, and followed by a semicolon)

### What is encapsulation?

Encapsulation is an attribute of an object, and it contains all data which is hidden. That hidden data can be restricted to the members of that class.

Levels are Public, Protected, Private, Internal, and Protected Internal.

### What is polymorphism?

Polymorphism in Java is a concept by which we can perform a single action in different ways. Polymorphism is derived from 2 greek words: poly and morphs. The word “poly” means many and “morphs” means forms. So polymorphism means many forms.

There are two types of polymorphism in Java: compile-time polymorphism and runtime polymorphism. We can perform polymorphism in Java by method overloading and method overriding.

E.g operator overloading

### What is the room database?

Room is a persistent library that is part of the Android Jetpack. It is built on top of SQLite. The room persistent library has many advantages over raw SQLite

### What are the guidelines in constraint layout?

Guidelines in Constraint Layout are invisible lines that are not visible to users but help developers to design the layout easily and constrain views to these guidelines, so that design can be more clear and interactive. But guidelines only work in Constraint Layout as guidelines require something to be constrained to them.

There are two types of guidelines:

Horizontal Guidelines: These guidelines have a height of zero and their width is equal to its parent Constraint Layout.

Vertical Guidelines: These guidelines have a width of zero and its height is equal to its parent Constraint Layout.

### What is a barrier in constraint layout?

a barrier is an invisible line that you can constrain views to. A barrier does not define its position; instead, the barrier position moves based on the position of views contained within it. This is useful when you want to constrain a view to a set of views rather than to one specific view.

### activity lifecycle

onCreate()

onStart()

onResume()

onPause()

onStop()

onRestart()

onDestroy()

### Fragment lifecycle.

onAttach(): This method will be called first, even before onCreate(), letting us know that your fragment has been attached to an activity. You are passed the Activity that will host your fragment

onCreateView(): The system calls this callback when it’s time for the fragment to draw its UI for the first time. To draw a UI for the fragment, a View component must be returned from this method which is the root of the fragment’s layout. We can return null if the fragment does not provide a UI

onViewCreated() : This will be called after onCreateView(). This is particularly useful when inheriting the onCreateView() implementation but we need to configure the resulting views, such as with a ListFragment and when to set up an adapter

onActivityCreated() :This will be called after onCreate() and onCreateView(), to indicate that the activity’s onCreate() has completed. If there is something that needs to be initialized in the fragment that depends upon the activity’s onCreate() having completed its work then onActivityCreated() can be used for that initialization work

onStart(): The onStart() method is called once the fragment gets visible

onPause(): The system calls this method as the first indication that the user is leaving the fragment. This is usually where you should commit any changes that should persist beyond the current user session

onStop(): Fragment going to be stopped by calling onStop()

onDestroyView() : It’s called before onDestroy(). This is the counterpart to onCreateView() where we set up the UI. If there are things that need to be cleaned up specific to the UI, then that logic can be put up in onDestroyView()

onDestroy(): onDestroy() is called to do the final clean-up of the fragment’s state but Not guaranteed to be called by the Android platform.

onDetach(): It’s called after onDestroy(), to notify that the fragment has been disassociated from its hosting activity

### How do we send data from one activity to another?

We can send the data using the putExtra() method from one activity and get the data from the second activity using the getStringExtra() method.

### What is MVVM?

MVVM architecture facilitates a separation of development of the graphical user interface with the help of mark-up language or GUI code. The full form of MVVM is Model–View–ViewModel.

The view model of MVVM is a value converter which means that it is the view model’s responsibility to expose the data objects from the Model in such a way that objects are easily managed and presented.

### What is JSON?

JSON (Javascript Object Notation) is a programming language. It is minimal, textual, and a subset of JavaScript. It is an alternative to XML.

Android provides support to parse the JSON object and array.

### What is JSON parsing?

Getting an object from a JSON string and converting an object into a JSON string is called JSON parsing

### Why do we use kotlin?

Kotlin is an Android-compatible language that is concise, expressive, and designed to be type- and null-safe. It works with the Java language seamlessly, so it makes it easy for developers who love the Java language to keep using it but also incrementally add Kotlin code and leverage Kotlin libraries.

### What is the difference between Val and Var?

var is like a general variable and can be assigned multiple times and is known as the mutable variable in Kotlin. Whereas val is a constant variable and can not be assigned multiple times and can be Initialized only a single time and is known as the immutable variable in Kotlin.

### Why we use lateinit?

lateinit is used when you are sure a variable won’t be null or empty and will be initialized before you use it -e.g. in the onResume() method for Android- and so you don’t want to declare it as a nullable type

### What are coroutines?

A coroutine is a concurrency design pattern that you can use on Android to simplify code that executes asynchronously. On Android, coroutines help to manage long-running tasks that might otherwise block the main thread and cause your app to become unresponsive. Over 50% of professional developers who use coroutines have reported seeing increased productivity. This topic describes how you can use Kotlin coroutines to address these problems, enabling you to write cleaner and more concise app code.

OR

It’s the lightweight thread that will provide line-by-line execution of the asynchronous task

### What is the suspend keyword or suspend function?

The suspend function is a function that can be started, paused, and resumed. One of the most important points to remember about the suspend functions is that they are only allowed to be called from a coroutine or another suspend function

### What is a lazy keyword?

It means lazy initialization. Your variable will not be initialized unless you use that variable in your code. It will be initialized only once after that we always use the same value. lazy() is a function that takes a lambda and returns an instance of lazy which can serve as a delegate for implementing a lazy property: the first call to get() executes the lambda passed to lazy() and remembers the result, subsequent calls to get() simply return the remembered result.

### What is const?

The const keyword is used to declare properties that are immutable, i.e. read-only properties. … No custom getter So, you can’t assign a const variable to a function or a class because the variable will be initialized at runtime rather than compile-time.

### Difference between array and list.

Array is mutable (it can be changed through any reference to it), but List doesn’t have modifying methods (it is either a read-only view of MutableList or an immutable list implementation). Arrays have fixed size and cannot expand or shrink retaining identity (you need to copy an array to resize it).

### What is the dispatcher?

The coroutine context includes a coroutine dispatcher that determines what thread or threads the corresponding coroutine uses for its execution. The coroutine dispatcher can confine coroutine execution to a specific thread, dispatch it to a thread pool, or let it run unconfined

Types of Dispatchers

There are majorly 4 types of Dispatchers.

Main Dispatcher

IO Dispatcher

Default Dispatcher

Unconfined Dispatcher

### What is the latest version of Android?

The latest version of Android OS is 15, released in October 2024. API level 35.

### What is the target SDK?

The target SDK version is the version of Android that your app was created to run on. The compile SDK version is the version of Android that the build tools use to compile and build the application in order to release, run, or debug. Usually, the compiled SDK version and the target SDK version are the same.

### What is the minimum SDK?

minSdkVersion is the minimum version of the Android operating system required to run your application

### What is bundled in APK?

An Android App Bundle is a publishing format that includes all your app’s compiled code and resources and defers APK generation and signing to Google Play. … You no longer have to build, sign, and manage multiple APKs to optimize support for different devices, and users get smaller, more optimized downloads.

### What are bundles?

We use bundles to pass the required data to various subfolders.

### What are background services?

Background services do not require any user intervention. These services do not notify the user about ongoing background tasks and users also cannot access them. The process like schedule syncing of data or storing of data falls under this service.

### What are foreground services?

Services that notify the user about its ongoing operations are termed Foreground Services. Users can interact with the service by the notifications provided about the ongoing task. Such as in downloading a file, the user can keep track of the progress in downloading and can also pause and resume the process.

### What is a broadcast receiver?

A broadcast receiver is an Android component that allows you to send or receive Android system or application events. … For example, applications can register for various system events like boot complete or battery low, and the Android system sends a broadcast when specific events occur.

### What is toast?

An Android Toast is a small message displayed on the screen, similar to a tooltip or other similar popup notification. A Toast is displayed on top of the main content of an activity and only remains visible for a short time period.

### How many types of visibility in Android?

VISIBLE (0) — The View is visible to the user. INVISIBLE (4) — The View is invisible to the user, but still takes up space in the layout. GONE (8) — The View is invisible, and it does not take up space in the layout.

### What is a content provider?

A content provider is used to share information between Android applications. Ex. sq lite, contacts.

### What is the context?

This is an abstract class whose implementation is provided by the Android system. It allows access to application-specific resources and classes, as well as up-calls for application-level operations such as launching activities, broadcasting and receiving intents, etc.

### What are Explicit intents?

Explicit intents specify which application will satisfy the intent, by supplying either the target app’s package name or a fully-qualified component class name. You’ll typically use an explicit intent to start a component in your app because you know the class name of the activity or service you want to start. For example, you might start a new activity within your app in response to a user action, or start a service to download a file in the background.

### What are Implicit intents?

Implicit Intent invokes the component of another app to handle the request. It does not specify the component name specifically.

For example, if we want to share data using Intent, it invokes the relevant application to fulfill the request.

Q . What is the constructor?

A constructor is a special member function that is invoked when an object of the class is created primarily to initialize variables or properties. A class needs to have a constructor and if we do not declare a constructor, then the compiler generates a default constructor.

Kotlin has two types of constructors –

Primary Constructor

Secondary Constructor

### What is overloading?

Overloading is static Binding, whereas Overriding is dynamic Binding. Overloading is nothing but the same method with different arguments, and it may or may not return an equal value in the same class itself.

### What is overriding?

Overriding is the same method names with the same arguments and return types associated with the class and its child class.

### What is an inline function?

An inline function is a technique used by the compilers and instructs to insert the complete body of the function wherever that function is used in the program source code.

### What is null safety?

Kotlin null safety is a procedure to eliminate the risk of null reference from the code. Kotlin compiler throws NullPointerException immediately if it finds any null argument is passed without executing any other statements. Kotlin’s type system is aimed to eliminate NullPointerException from the code.

### What is the difference between “==” and “===”?

the == operator is generally used to compare the values stored in variables, and the === operator is used to check if the reference of the variables is equal or not.

In the case of primitive types, the === operator is also used to check for the value and not reference.

### What is a sealed class?

Sealed classes and interfaces represent restricted class hierarchies that provide more control over the inheritance. All direct subclasses of a sealed class are known at compile time. No other subclasses may appear after a module with the sealed class is compiled.

### What is shared preferences?

Shared Preferences is how we can store and retrieve small amounts of primitive data as key/value pairs to a file on the device storage such as String, int, float, Boolean that make up your preferences in an XML file inside the app on the device storage

### How many exceptions are in Android?

AccountsException, AclNotFoundException, AndroidException, AppSearchException, BackingStoreException, BrokenBarrierException, CertificateException, CloneNotSupportedException, ConfirmationAlreadyPresentingException, ConfirmationNotAvailableException, DataFormatException, DatatypeConfigurationException, DestroyFailedException, DnsResolver.DnsException, ErrnoException, and 36 others.

### How to handle exceptions in Android?

An exception is an event that occurs during the execution of a program. Exceptions can be of any type — Runtime exceptions, Error exceptions. Those exceptions are adequately handled through exception-handling mechanisms like try, catch, and throw keywords.

### How many types of storage are in Android?

Android provides two types of physical storage locations: internal storage and external storage. On most devices, internal storage is smaller than external storage. However, internal storage is always available on all devices, making it a more reliable place to put data on which your app depends

### What is the internal storage?

Internal storage is the storage of the private data on the device’s memory. By default, these files are private and are accessed by only your application and get deleted when the user deletes your application.

### What is an external storage?

External Storage is one that is accessible by the user but still part of the built-in memory. All your media files, documents, and pictures are stored on this primary storage and this is when you don’t have a physical external storage device such as an SD Card.

### What is frame layout?

FrameLayout is designed to block out an area on the screen to display a single item. Generally, FrameLayout should be used to hold a single child view, because it can be difficult to organize child views in a way that’s scalable to different screen sizes without the children overlapping each other. You can, however, add multiple children to a FrameLayout and control their position within the FrameLayout by assigning gravity to each child, using the android:layout\_gravity attribute.

### What is the relative layout?

RelativeLayout is a view group that displays child views in relative positions. The position of each view can be specified as relative to sibling elements (such as to the left-of or below another view) or in positions relative to the parent RelativeLayout area (such as aligned to the bottom, left, or center).

### What is the linear layout?

LinearLayout is a view group that aligns all children in a single direction, vertically or horizontally. You can specify the layout direction with the android: orientation attribute.

### What is constraint layout?

A ConstraintLayout is a ViewGroup that allows you to position and size widgets in a flexible way. Note: ConstraintLayout is available as a support library that you can use on Android systems starting with API level 9 (Gingerbread)

### What is an activity?

Activity is like a frame or window in Java that represents GUI. It represents one screen of Android.

### What is Android?

It is an open-sourced operating system that is used primarily on mobile devices, such as cell phones and tablets. It is a Linux kernel-based system that’s been equipped with rich components that allow developers to create and run apps that can perform both basic and advanced functions.

### What is ANR?

ANR stands for Application Not Responding. It is a dialog box that appears if the application is no longer responding.

### What is the function of the intent filter?

Because every component needs to indicate which intents they can respond to, intent filters are used to filter out intents that these components are willing to receive. One or more intent filters are possible, depending on the services and activities that are going to make use of it.

### What is a fragment?

The fragment is a part of the activity by which we can display multiple screens during one activity.

### What is a data class?

a data class is a class whose main purpose is to hold data. It is marked as “data”.

The primary constructor must have at least one parameter, and all primary constructor parameters need to be marked as val or var.

Data classes cannot be abstract, open, sealed, or inner.

### Difference between Global scope, lifecycle scope, and ViewModel scope

Global scope is used to launch top-level coroutines that operate during the whole application lifetime and are not canceled prematurely. Active coroutines launched in GlobalScope do not keep the process alive. They are like daemon threads.

A LifecycleScope is defined for each Lifecycle object. Any coroutine launched in this scope is canceled when the Lifecycle is destroyed. You can access the CoroutineScope of the Lifecycle either via lifecycle.

ViewModelScope. A ViewModelScope is defined for each ViewModel in your app. Any coroutine launched in this scope is automatically canceled if the ViewModel is cleared. Coroutines are useful here for when you have work that needs to be done only if the ViewModel is active.

### What is Interface?

An interface is a collection of abstract methods. If the class implements an interface, it thereby inherits all the abstract methods of an interface.

### What is the let keyword?

let is one of Kotlin’s Scope functions that allow you to execute a code block within the context of an object

### Difference between View binding and data binding.

View binding is a feature that allows you to write code that interacts with views. Once view binding is enabled in a module, it generates a binding class for each XML layout file present in that module.

Data binding is about connecting views in the XML layout with data objects: In this case, Kotlin code. The Data Binding Library generates the classes needed for this process.

### Link list basic definition.

A linked List can be defined as a collection of objects called nodes that are randomly stored in the memory. A node contains two fields i.e. data stored at that particular address and the pointer which contains the address of the next node in the memory. The last node of the list contains a pointer to the null.

### What is Typecasting?

Typecasting is a process of converting one data type to another type, for example — converting int to long, long to double, etc.

### How to read a file text file?

Kotlin reads the File using InputStream

retrieves InputStream from the File, and then gets BufferedReader using the bufferedReader() method.

use Closeable. use() method along with Reader. readText() method inside block. Closeable. use(Reader. readText())

### What is Serialization?

Serialization is the process of converting data used by an application to a format that can be transferred over a network or stored in a database or a file.

### What is a File provider?

FileProvider is a special subclass of ContentProvider that facilitates secure sharing of files associated with an app by creating content:// Uri for a file instead of a file:/// Uri.

A content URI allows you to grant read and write access using temporary access permissions. When you create an Intent containing a content URI, to send the content URI to a client app, you can also call Intent.setFlags() to add permissions. These permissions are available to the client app for as long as the stack for a receiving Activity is active. For an Intent going to a Service, the permissions are available as long as the Service is running.

### Scope storage (for file access)

Apps that run on Android 11 but target Android 10 (API level 29) can still request the requestLegacyExternalStorage attribute. This flag allows apps to temporarily opt out of the changes associated with scoped storage, such as granting access to different directories and different types of media files. After you update your app to target Android 11, the system ignores the requestLegacyExternalStorage flag.

### What is glide?

Glide is an Image Loader Library for Android developed by Bumptech and is a library that is recommended by Google. It has been used in many Google open source projects including Google I/O 2014 official application. It provides animated GIF support and handles image loading/caching

### What is animation?

Animation is a method in which a collection of images are combined in a specific way and processed then they appear as moving images. Building animations makes on-screen objects seem to be alive. Android has quite a few tools to help you create animations with relative ease. so in this article, we will learn to create animations using Kotlin. below are some attributes that we are using while writing the code in XML.

### What is a lifecycle observer?

LifecycleObserever Observer is one of the Jetpack Architecture components and is an interface that observes and performs the specified task depending upon the Lifecycle owner’s Lifecycle changes.

### What is live data?

LiveData is an observable data holder class. Unlike a regular observable, LiveData is lifecycle-aware, meaning it respects the lifecycle of other app components, such as activities, fragments, or services. This awareness ensures LiveData only updates app component observers that are in an active lifecycle state.

### Telephone manager?

The android. telephony.TelephonyManager class provides information about the telephony services such as subscriber ID, sim serial number, phone network type, etc. Moreover, you can determine the phone state, etc.

### Work manager

WorkManager is an Android library that runs deferrable background work when the work’s constraints are satisfied. WorkManager is intended for tasks that require a guarantee that the system will run them even if the app exits. … This is critical for Android applications that need to execute background tasks

### What is a Handler?

A Handler allows you to send and process Message and Runnable objects associated with a thread’s MessageQueue. Each Handler instance is associated with a single thread and that thread’s message queue. When you create a new Handler it is bound to a Looper. It will deliver messages and runnables to Looper’s message queue and execute them on Looper’s thread.

### What is Thread?

A thread is a thread of execution in a program. The Java Virtual Machine allows an application to have multiple threads of execution running concurrently. Every thread has a priority. … One is to declare a class to be a subclass of Thread. This subclass should override the run method of the class Thread

### What is a job scheduler?

This is an API for scheduling various types of jobs against the framework that will be executed in your application’s process. The framework will be intelligent about when it executes jobs, and attempts to batch and defer them as much as possible. Typically if you don’t specify a deadline on a job, it can be run at any moment depending on the current state of the JobScheduler’s internal queue.

While a job is running, the system holds a wake lock on behalf of your app. For this reason, you do not need to take any action to guarantee that the device stays awake for the duration of the job.

### What is an Alarm manager?

AlarmManager in android, you can schedule your application to run at a specific time in the future. It works whether your phone is running or not.

The Android AlarmManager holds a CPU wake lock that provides a guarantee not to sleep the phone until the broadcast is handled.

### What is an application class?

The Application class in Android is the base class within an Android app that contains all other components such as activities and services. The Application class, or any subclass of the Application class, is instantiated before any other class when the process for your application/package is created.

### How many design patterns are present in kotlin or Java?

Creational patterns: How you create objects.

Builder

Dependency Injection

Singleton

Factory

Structural patterns: How you compose objects.

Adapter

Facade

Decorator

Composite

Behavioral patterns: How you coordinate object interactions.

Command

Observer

Strategy

State

### What is an interceptor?

Interceptors are a powerful mechanism that can monitor, rewrite, and retry calls. simple interceptor that logs the outgoing request and the incoming response.

### What is MVP?

MVP pattern overcomes these challenges of MVC and provides an easy way to structure the project codes. The reason why MVP is widely accepted is that it provides modularity, testability, and a more clean and maintainable codebase. It is composed of the following three components:

Model: Layer for storing data. It is responsible for handling the domain logic(real-world business rules) and communication with the database and network layers.

View: UI(User Interface) layer. It provides the visualization of the data and keeps track of the user’s actions to notify the Presenter.

Presenter: Fetch the data from the model and applies the UI logic to decide what to display. It manages the state of the View and takes actions according to the user’s input notification from the View.

### What is MVC?

The MVC framework is an architectural pattern that separates an application into three main logical components Model, View, and Controller. Hence the abbreviation MVC. The full form MVC is Model View Controller.

### What is final, finally and finalize?

The final keyword can be used with class method and variable. A final class cannot be inherited, a final method cannot be overridden and a final variable cannot be reassigned.

The finally keyword is used to create a block of code that follows a try block. A finally block of code always executes, whether or not an exception has occurred. Using a finally block allows you to run any cleanup-type statements that you just wish to execute, despite what happens within the protected code.

The finalize() method is used just before an object is destroyed and can be called just before object creation.

### What is the recycler view?

A RecyclerView is a container used to display a list or grid of data, like text or photos. When a list scrolls, only a handful of views are displayed on the screen. When a view scrolls off-screen, RecyclerView reuses it and fills it with new data.

### What is an array adapter?

ArrayAdapter is the most commonly used adapter in Android. When you have a list of single-type items which are stored in an array you can use ArrayAdapter. Likewise, if you have a list of phone numbers, names, or cities. ArrayAdapter has a layout with a single TextView.

### What is a cursor?

The cursor is the Interface that represents a 2-dimensional table of any database. When you try to retrieve some data using the SELECT statement, then the database will first create a CURSOR object and return its reference to you.

The pointer of this returned reference is pointing to the 0th location which is otherwise called before the first location of the Cursor, so when you want to retrieve data from the cursor, you have to first move to the first record so we have to use moveToFirst

When you invoke the moveToFirst() method on the Cursor, it takes the cursor pointer to the first location. Now you can access the data present in the first record.

### Difference between listview and recycler view?

RecyclerView was created as a ListView improvement, so yes, you can create an attached list with ListView control, but using RecyclerView is easier as it:

Reuses cells while scrolling up/down — this is possible with implementing View Holder in the ListView adapter, but it was an optional thing, while in the RecycleView it’s the default way of writing adapter.

Decouples list from its container — so you can put list items easily at run time in the different containers (linear layout, grid layout) with setting LayoutManager.

### What is a static keyword?

The static keyword in Java is used to share the same variable or method of a given class. The users can apply static keywords with variables, methods, blocks, and nested classes. The static keyword belongs to the class rather than an instance of the class.

### What are bound services?

This type of Android service allows the components of the application like activity to bind themselves with it. Bound services perform their task as long as any application component is bound to it. More than one component is allowed to bind themselves with a service at a time. In order to bind an application component with a service bindService() method is used.

### What is the use of animation?

Animation is used to create models that are essential for research and study. Animation allows you to create 3D, realistic models that allow diagrams, etc. to show accurate representations of an object. An example of this is an X-ray. Doctors use this to get an accurate look at bones etc.

### Scenario for get application context?

We used to get applications in Toast and services.

### What are the jetpack components?

Work manager, Hilt, Foreground service, CameraX.

### What is the use of the view model?

ViewModel will be used to store data of views that will be not erased when the device is rotated and also used for managing business logic.

### What is a debugger?

It will be used to check bugs by checking the flow and associated value to the variables.

### How to upload images to the server?

To upload an image we need to pick it from the gallery by using intent and then we need to use an API like a retrofit to upload it using multipart API.

### How to pass data from one fragment to another?

We can use callback or ViewModel to pass data from one to another.

### How to load images from the file system?

We can load images by getting bitmap from files using the file path.

We can use glide lib. From loading images using the file path.

### All retrofit annotation?

@POST, @GET, @PATCH, @PUT, @DELETE, @OPTION, @HEAD

### List down the Run permission used from this specific feature.

Map-Location permission, course location, fine location, after Android 11 requested for foreground only or background only.

File: Request permission for file read and write permission. After Android 11 scope storage we don’t need to use this permission instead you can request for

Camera: request permission to access the camera.

### Which intent we will use when we pick an image from the gallery or click an image from the camera?

We use ACTION\_IMAGE\_CAPTURE intent for picking images from the camera and ACTION\_PICK intent for picking images from the gallery.

### All list method?

A list is an ordered collection of items. In Kotlin, lists can be either mutable (MutableList) or read-only (List). For list creation, use the standard library functions listOf() for read-only lists and mutableListOf() for mutable lists. To prevent unwanted modifications, obtain read-only views of mutable lists by casting them to List.

```kotlin
val systemUsers: MutableList = mutableListOf(1, 2, 3) // 1
val sudoers: List = systemUsers // 2

​fun addSystemUser(newUser: Int) { // 3
    systemUsers.add(newUser)
}

fun getSysSudoers(): List { // 4 return sudoers

}

​fun main() {
    addSystemUser(4) // 5
    println(“Tot sudoers: ${getSysSudoers().size}”) // 6
    getSysSudoers().forEach { // 7
        i -> println(“Some useful info on user $i”)
    }
    // getSysSudoers().add(5) <- Error! // 8
}
```

Creates a MutableList.

Creates a read-only view of the list.

Adds a new item to the MutableList.

A function that returns an immutable List.

Updates the MutableList. All related read-only views are updated as well since they point to the same object.

Retrieves the size of the read-only list.

Iterates the list and prints its elements.

Attempting to write to the read-only view causes a compilation error.

### What is a string template?

Kotlin has an awesome feature called string templates that allows strings to contain template expressions.

A string template expression starts with a dollar sign $.

### String operation?

Get, length, equals, hashcode, toUpper, toLower, subString, plus, toString.

### Difference between string, string builder, and string buffer?

The String class represents character strings. All string literals in Kotlin programs, such as “ABC”, are implemented as instances of this class.

StringBuilder

StringBuilder is the same as the StringBuffer, that is it stores the object in a heap and it can also be modified. The main difference between the StringBuffer and StringBuilder is that StringBuilder is also not thread-safe. StringBuilder is fast as it is not thread-safe.

StringBuffer

StringBuffer is mutable means one can change the value of the object. The object created through StringBuffer is stored in the heap. StringBuffer has the same methods as the StringBuilder, but each method in StringBuffer is synchronized that is StringBuffer is thread-safe.

because of this, it does not allow two threads to simultaneously access the same method. Each method can be accessed by one thread at a time.

But being thread-safe has disadvantages too as the performance of the StringBuffer hits due to thread-safe property. Thus StringBuilder is faster than the StringBuffer when calling the same methods of each class.

StringBuffer value can be changed, which means it can be assigned to the new value. Nowadays it’s a most common interview question, the differences between the above classes. String Buffer can be converted to a string by using the toString() method.

### Firebase operations.

We use Firebase operations for database management, notification, authentication, and analytics.

### What is memory management and memory leak in Android?

Memory leaks occur when an application allocates memory for an object but then fails to release the memory when the object is no longer being used. Over time, leaked memory accumulates and results in poor app performance and even crashes.

Thank you :)

