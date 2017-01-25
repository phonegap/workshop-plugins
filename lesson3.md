---
layout: module
title: Module 3&#58; Plugin Implementation
---

_approximate duration : 30 minutes_

## Overview
- what domain knowledge is required?
- what can plugin code do?

## Demo - Sidebar Plugin
<!-- TODO: are we showing this plugin - https://github.com/purplecabbage/phonegap-plugin-sidebar -->


## Plugin Parts

1. JavaScript interface (what developers call)
1. A native interface (ie: ObjC or Java) (where the work is done)
1. Cordova provides:
  - the plumbing to get your js arguments into native
  - the callbacks so native code is run asynchronously
1. App developer provided *callback* functions are called to get the result

## Passing Data 
How do we pass data from `js->objc js->java java->js objc->js` ?

    cordova.exec(successCallback, // function to call with results on success
             errorCallback,   // function to call with error
             strClassName,    // String name of class in native code
             strMethodName,   // String name of function
             ["a","b",... ] ); // array of string args, possibly empty


## iOS

1. Cordova will look for a cordova plugin interface matching `strClassName`
1. Cordova will look for a method matching `strMethodName` on the interface above, and call it, passing in an object which 
contains the arguments as well as a `callback_id` which can be used to signal success of failure.  This `callback_id` will then be routed to the correct callback.

  `- (void)strMethodName:(CDVInvokedUrlCommand*)command`

## Android

1. Cordova will look for cordova plugin interface matching strClassName
1. Cordova android code will call the plugin's `execute` method and pass an action of 'strMethodName' plus the arguments

  `public boolean execute(String action, JSONArray args, CallbackContext callbackContext) throws JSONException`

### Exercise 4

Now write a plugin that passes data round trip using the echo plugin template, using the information learned in the above walk-thru. 


<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="lesson2.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="lesson4.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>
