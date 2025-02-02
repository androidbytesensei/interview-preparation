---
description: >-
  Originally posted on Medium here -
  https://medium.com/@harshitabambure/android-interview-questions-series-with-basic-to-advance-part-i-646be098afe0
---

# Android Interview Questions - P1

Prepare for your Android developer interview with this in-depth guide on **Android Architecture Components**. Covers **LiveData, and ViewModel**— from basics to advanced concepts. (Part 1)

As Android developers, we know how challenging it can be to prepare for an interview, especially when it feels like one important topic might be missing from our preparation. No matter how thorough the study, there’s always a question that slips through the cracks. To help address this challenge, we’re starting a series of interview questions that will ensure no topic is left uncovered.

This series will cover interview questions in **specific categories** of Android development, ensuring you have a comprehensive understanding of all possible areas that may be tested. By the end of the series, you’ll be able to confidently approach interviews, knowing you’ve covered all potential questions in each category.

(づ｡◕‿‿◕｡)づ

Let’s dive into the world of Android development and get ready to ace your next interview!

> Let’s Start with the most Focused Topics in the interview

## Android Architecture Components <a href="#id-9242" id="id-9242"></a>

### **1. What are Android Architecture Components, and why are they important in modern Android development?** <a href="#id-9242" id="id-9242"></a>

Android Architecture Components are part of Android Jetpack. They help developers manage UI component lifecycles and handle data persistence effectively. These components promote clean architecture and reduce boilerplate code.

Key components include:

* **Data Binding**
* **Lifecycles**
* **LiveData**
* **Navigation**
* **Paging**
* **Room**
* **ViewModel**
* **WorkManager**

### &#x32;**. What are the primary benefits of using Android Architecture Components in your app development?**

Android Architecture Components offer many benefits, including:

* **Reusability**: Components can be used multiple times in different applications
* **Modularity**: Components can be broken down into smaller, more manageable units
* **Scalability**: Components can be scaled up or down to meet the needs of the app
* **Reduced development time**: Components can help developers build apps faster
* **Reduced testing time**: Components can make it easier to test code
* **Enhanced reliability**: Components can help make apps more reliable
* **Flexibility**: Components can be used in a variety of ways to meet the needs of the app

## **ViewModel** <a href="#db18" id="db18"></a>

### **3. What is a ViewModel in Android, and how does it help manage UI-related data?**

A ViewModel is a component that manages and stores data for the user interface (UI). It’s used to handle business logic, events, and interactions between controls. ViewModels are also responsible for maintaining the separation of concerns and addressing configuration changes.

It helps in,

* Handle business logic in the UI layer
* Handle events and delegate them to other layers
* Provide data from the model to the view
* Handle interactions between fragments on Activities
* Maintain the separation of concerns
* Ensure data persistence on configuration changes

Code:

```
class ListUserViewmodel : ViewModel() {
 init {
  fetchUsers() // any initilization or anymethod which need to be called in first
 }
//code for business logic ,methods,will come here
}
```

### **4. How do ViewModels survive configuration changes like screen rotations?**

When an activity undergoes a configuration change, the Android system destroys the old instance and creates a new one. The ComponentActivity class uses the NonConfigurationInstance mechanism to retain the ViewModelStore. The new activity that is created will call the NonConfigurationInstance and retrieve the ViewModel which is stored.

### **5. Can we share data between different fragments or activities using ViewModel?(Imp)**

Yes, We can create ViewModel on the activity level and share the same ViewModel with the fragment using ViewModelProvider.

### **6. How would you handle long-running operations inside a ViewModel without blocking the UI thread?**

To Run long running method in ViewModel we can use Coroutines, and Thread for doing the operation on the background thread.

### **7. What is ViewModelProvider and how is it used in Android?**

The ViewModelProvider is a utility class provided by Android Architecture Components. It is used to create and retrieve instances of ViewModel. This class simplifies managing the lifecycle of ViewModel instances by ensuring that the same instance is reused across configuration changes, such as screen rotations.

**Code**

```
val myViewModel = ViewModelProvider(this).get(MyViewModel::class.java)
```

### **8. What is ViewModel Factory and where it is used in ViewModel?(IMP)**

ViewModelFactory is used to create instances of ViewModel objects\
that may require additional parameters, it is used when ViewModel\
requires something that cannot be automatically provided by the default ViewModelProvider, such as data repositories or other external resources.

**Code:**

**ViewModel:**

In this ViewModel, we will need UserRepository as a parameter so for that, we will be required ViewModelFactory.

```
class ListUserViewmodel(userRepository:UserRepository) : ViewModel() {
 init {
  fetchUsers() // any initilization or anymethod which need to be called in first
 }
//code for business logic ,methods,will come here
}
```

**ViewModelFactory**

```
class UserViewModelFactory(private val userRepository: UserRepository) : ViewModelProvider.Factory {
    
    override fun <T : ViewModel?> create(modelClass: Class<T>): T {
        if (modelClass.isAssignableFrom(ListUserViewmodel::class.java)) {
            return ListUserViewmodel(userRepository) as T
        }
        throw IllegalArgumentException("Unknown ViewModel class")
    }
}
```

**MainActivity**

```
 class UserActivity : AppCompatActivity() {

    private lateinit var userViewModel: UserViewModel

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_user)

        // Assuming userRepository is already available
        val userRepository = UserRepository()

        // Create the ViewModel using the factory
        val viewModelFactory = UserViewModelFactory(userRepository)
        userViewModel = ViewModelProvider(this, viewModelFactory).get(UserViewModel::class.java)
        
        // Now you can access the userViewModel and call its methods
    }
}
```

And if you have a Dependency Injection framework like **Hilt** the factory creation is not needed here

With **Hilt**, you can simply inject the `ViewModel` directly with the below code

```
private val userViewModel: UserViewModel by viewModels()
```

## **LiveData** <a href="#id-68d7" id="id-68d7"></a>

### **9. What is LiveData, and how does it fit into the architecture components in Android?(IMP)**

LiveData is an observable data holder class. LiveData is lifecycle-aware, meaning it respects the lifecycle of other app components, such as activities, fragments, or services. This awareness ensures LiveData only updates app component observers that are in an active lifecycle state.

We are using Livedata to retrieve data from ViewModel to activity or fragment as it is Lifecycle aware it is also helpful in avoiding errors.

**Code:**

```
val userName: MutableLiveData<String> =MutableLiveData()
init{
//To Send data to the observer
username.value="Test Name" //By doing this it will send data to the oberver
}
```

```
//To Receive Data we will be writing this in Activity or in Fragment
listViewModel.currentName.observe(this){ //here this keyword represent context 
 println("Name: $it")
 }
```

### **10. What is the difference between LiveData and Observable data in Android?**

Livedata is a lifecycle-aware component means respects the lifecycle of other app components, such as activities, fragments, or services. this ensures that all ui updates will happen only when the screen is visible and the component is alive. This will prevent crashes and window leak exception

### **11. How do you observe LiveData, and what is the role of an observer in this context?**

To observe any Livedata we will be using the observe method of live data here is an example we can follow considering we have Livedata In ViewModel

```
listViewModel.currentName.observe(this){ //here this keyword represent context 
 println("Name: $it")
 }
```

Here we have passed this as a lifecycle owner and the observer will keep monitoring the Livedata for the update if any change happens in the value of live data it will provide a callback and update the UI.

### **12. What happens when a LiveData object’s value is updated while no observer is active?**

In this case, whatever value we assign to the Livedata will be stored, and whenever any observer starts observing that it will be sent the latest value it has in Livedata.

### **13. What is the difference between Livedata and Mutablelivedata?**

Livedata is read-only observable data while Mutablelivedata allows reading and writing both. we can not modify the value of livedata directly but Mutablelivedata value can be modified using the value property.

### **14**. **What are the use cases where MediatorLiveData is been used ?**

The main usage of this Livedata is in the below operations

1. **Combining Multiple Sources:**\
   MediatorLiveData can monitor changes in multiple LiveData sources and provide the combined output
2. **Transformation Logic:**\
   we can process the result of two live data add a filter and provide the processed result to the observer.

**Code Example:**

```
val firstName = MutableLiveData<String>()
val lastName = MutableLiveData<String>()
val fullName = MediatorLiveData<String>().apply
{
addSource(firstName) { first -> value = "$first ${lastName.value.orEmpty()}" } addSource(lastName) { last -> value = "${firstName.value.orEmpty()} $last" }
}
```

**Here it will update the full name whenever one of the livedata values changes.**

### **15. What is the difference between Livedata.set() and Livedata.post()**

`setValue()` method must be called from the main thread. But if you need to set a value from a background thread, `postValue()` should be used.

### **16. Can we have multiple ViewModel in one Activity?**

Yes, we can use multiple ViewModel in one Activity.
