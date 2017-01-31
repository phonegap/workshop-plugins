---
layout: module
title: Lesson 3&#58; Plugin Implementation
---

_approximate duration : 15 minutes_

## Plugin Components
A plugin is made up of the following components:

1. A **JavaScript interface** - (called by app developers)

1. A **native interface** written in Obj-C/Swift, Java or C# for each supported platform - (where the native work is done)

1. Built-in **Cordova bridge** that provides:
  - the plumbing to get your JavaScript arguments mapped to the native interfaces
  - callback handling to ensure the native code routes back the result to the proper callback depending on success or failure

## Plugin Workflow

#### JavaScript Bridge
The `cordova exec` function is used to call the native interface and pass the required parameters to invoke the native interface with optional arguments needed. 

    cordova.exec(successFunction(result) {}, // function to call with success result
                 failFunction(error) {}, // function to call with error result
                 strServiceName, // Name of service to invoke native code (maps to a native Class name)
                 strActionName,  // Name of action to invoke in the native class
                 ["firstArgument", "secondArgument", 42, false]); // Array of any args needed by native functions

<br>

#### Cordova Bridge Mapping for iOS

1. Cordova will locate the ios platform interface matching `strServiceName` (based on configured mapping)
1. Cordova will look for a method matching `strActionName` in the ios plugin interface and call it, passing in an object containing the necessary arguments and callback info

   **Example method signature**<br>
   `- (void)strActionName:(CDVInvokedUrlCommand*)command {...}`

<br>

#### Cordova Bridge Mapping for Android

1. Cordova will locate the android platform interface matching `strServiceName` (based on configured mapping)
1. Cordova will locate the `execute()` method in the android plugin code and pass in the `strActionName`, optional arguments and callback info

   **Example method signature**<br> 
   `public boolean execute(String action, JSONArray args, CallbackContext callbackContext) throws JSONException {...}`

### Visual Example
The picture below illustrates how the JavaScript interface specifically maps to each native Class:

![](images/plugin-mapping.png)

### Examine your Plugin
Open the JavaScript interface for your plugin (in `www/template.js`) and find the `exec()` function, then open each of the native interfaces (in `src/ios` and `src/android`) and notice how the parameters are mapped for each:

    echo: function(successCallback, errorCallback, message, forceAsync) {
        var action = 'echo';
        if (forceAsync) {
            action += 'Async';
        }
        exec(successCallback, errorCallback, 'Echo', action, [message]);
    }

  - The first and second parameters are the _success_ and _error_ callback functions
  - The third parameter calls the `Echo` service in the native platform for the plugin
  - The fourth parameter requests the _action_ to execute (`echo`) within the service class. On iOS this maps directly to a method name, for Android it is passed in as the 1st parameter in the `execute()` method
  - The last specifies an array of arguments to pass to the `echo()` method. In this case it's just a _string_ 

>Note: The `plugin.xml` defines a feature definition within each platform as well as the location of the source file for it. This name must match the name passed in as the _service_ name which maps to the native source class name and location specified.

###### plugin.xml snippet
 ![](images/plugin-xml-feature.png)

<!--## Demo - Data Passing
TODO: are we showing this plugin - https://github.com/purplecabbage/phonegap-plugin-sidebar -->

### Bonus Exercise 
Update your plugin signature to pass additional parameters using the information learned thus far. 

### Resources
Check out the official [Apache Cordova Plugin Development Guide](http://cordova.apache.org/docs/en/latest/guide/hybrid/plugins/index.html) for more details on all of the above. 


<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="lesson2.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="lesson4.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>
