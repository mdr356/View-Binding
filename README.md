# View-Binding

```kotlin
findViewById<>
```
is the source of many user-facing bugs in Android. It’s easy to pass an id that’s not in the current layout 

- View binding replaces findViewById

- View Binding auto generate a class that maps to an xml layout file.
```kotlin
activity_main.xml -> ActivityMainBinding.java
```

View Binding allows you to access only the ids of view that are in the current layout. Creating a safe view lookup.


## Enable View Binding

*build.gradle* file
```kotlin
// Android Studio 4.0
android {
  buildFeatures {
    viewBinding = true
  }
}
```

### Activity
Normally, we would override onCreate and call the setContentView() to provide a UI, in this case *activity_main*.

```kotlin
override fun onCreate(savedInstanceState:Bundle?){
super.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main)
}
```
### Activity & ViewBinding
With ViewBinding, **setContextView()** would be replace.
As stated above, the View Binding framework auto generate a class that maps to an xml layout file.
```kotlin
...
private lateinit var binding: ActivityMainBinding
    
override fun onCreate(savedInstanceState:Bundle?){
    super.onCreate(savedInstanceState)

    binding = ActivityMainBinding.inflate(layoutInflater)
    setContentView(binding.root)
}
    ...
```
You can now use the instance of the binding class to reference any of the views within the current layout.

### Fragment

### Fragment & ViewBinding
