
# Plugins Workshop/Lab Outline

Total time: 60 minutes


## a previous incarnation :
http://purplecabbage.github.io/slides/pgd16Plugins/index.html


Discovery, Installation, Definition of Plugins
===
_approximate duration : 15 minutes_

- what is a plugin and when is it useful
- examples are popular core and community plugins
- npm as a cordova plugin registry
- cordova/phonegap tooling to add|remove|ls plugins
- a walk through the plugin.xml format
    - defining platform code
    - shared js code
    - id/name/version
    - dependencies
    - tools to use to create plugins, plugman, phonegap/phonegap-plugin-template
    - exercise, create a plugin using above tools, make it depend on 2 other plugins, install it
- what's next in plugin definition? package.json

Plugin Implementation
===
_approximate duration : 30 minutes_

- what domain knowledge is required?
- what can plugin code do?
- how do we pass data from js->objc? js->java? java->js? objc->js?
- the various parts of a plugin
    1. a js interface, this is what app developers call
    2. a native interface (ObjC or Java) this is where the work is done
    - cordova provides the plumbing to get your js arguments into native
    - cordova provides callbacks so native code is run asynchronously
    - app developer provided callback functions are called with the result
```
cordova.exec(successCallback, // function to call with results on success
             errorCallback,   // function to call with error
             strClassName,    // String name of class in native code
             strMethodName,   // String name of function
             ["a","b",... ] ); // array of string args, possibly empty
```
### iOS:
1. cordova will look for a cordova plugin interface matching strClassName
2. cordova will look for a method matching strMethodName on the interface above, and call it, passing in an object which contains the arguments as well as a callback id which can be used to signal success of failure.  This callback id will then be routed to the correct callback.

`- (void)strMethodName:(CDVInvokedUrlCommand*)command`

### Android:
1. cordova will look for cordova plugin interface matching strClassName
2. cordova android code will call the plugin's `execute` method and pass an action of 'strMethodName' plus the arguments

`public boolean execute(String action, JSONArray args, CallbackContext callbackContext) throws JSONException`

- exercise: implement a round trip data passing echo plugin

Plugin Publishing
===
_approximate duration : 15 minutes_
- how to share plugins
  - common naming conventions (`cordova-`, `phonegap-`, `ionic-`, `telerik-`)
- publishing with npm
- publishing with plugman
  

Advanced Topics ~ Time permitting

Plugin Testing
===

- how does Apache Cordova test plugins?
- how does PhoneGap test plugins?
- tools to help you, paramedic, jasmine, jshint
- demo paramedic running tests against a plugin
- exercise: write and run some simple tests for a plugin


