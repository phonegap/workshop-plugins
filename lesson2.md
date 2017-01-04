---
layout: module
title: Module 2&#58; Plugin Implementation
---

_approximate duration : 30 minutes_

## Overview
- what domain knowledge is required?
- what can plugin code do?

## Passing Data 
- how do we pass data from js->objc? js->java? java->js? objc->js?

## Plugin Parts

1. A js interface - what app developers call)
1. A native interface (ie: ObjC or Java) - where the work is done
1. Cordova provides:

  - the plumbing to get your js arguments into native
  - the callbacks so native code is run asynchronously
1. The app developer provides callback functions to be called from cordova with the results


    cordova.exec(successCallback, // function to call with results on success
             errorCallback,   // function to call with error
             strClassName,    // String name of class in native code
             strMethodName,   // String name of function
             ["a","b",... ] ); // array of string args, possibly empty


## iOS

1. cordova will look for a cordova plugin interface matching strClassName
1. cordova will look for a method matching strMethodName on the interface above, and call it, passing in an object which contains the arguments as well as a callback id which can be used to signal success of failure.  This callback id will then be routed to the correct callback.

  `- (void)strMethodName:(CDVInvokedUrlCommand*)command`

## Android

1. cordova will look for cordova plugin interface matching strClassName
1. cordova android code will call the plugin's `execute` method and pass an action of 'strMethodName' plus the arguments

  `public boolean execute(String action, JSONArray args, CallbackContext callbackContext) throws JSONException`

## Exercise:

>Implement a round trip data passing echo plugin


<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="lesson1.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="lesson3.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>
