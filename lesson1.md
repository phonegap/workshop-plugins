---
layout: module
title: Module 1&#58; Plugin Discovery and Installation
---

_approximate duration : 5 minutes_

<!--
for cordova-plugin-device, I showed the repo, then I explained the contents of plugin.xml
then I showed how each plugin.xml element mapped to an output project
then I explained how the device.js file was able to send/receive messages from the native layer via exec
then I created a new project, installed the plugin and step debugged the native parts in xcode
-->

## Plugin Discovery
You can discover Cordova plugins directly in [npm](http://nmpjs.org) by searching `ecosystem:cordova`.

<!--Demo using npm as a cordova plugin registry-->

### Exercise 1

Navigate to [npmjs.org](http://npmjs.org) and do your own search for Cordova plugins now to see what you can find. Does it look like the picture below? Scroll through and take a look at all of the different plugins already available. 

![](images/npm-plugin-search.png)


## Plugin Installation 
Plugins are added and removed using the [Cordova](https://www.npmjs.com/package/cordova-cli) or [PhoneGap CLI](https://www.npmjs.com/package/phonegap).

  - **Add a Plugin**

      - `$ phonegap plugin add cordova-plugin-device`
      - `$ cordova plugin add cordova-plugin-device`

  - **Remove a Plugin**

      - `$ phonegap plugin remove cordova-plugin-device`
      - `$ cordova plugin remove cordova-plugin-device`

  - **List all Plugins**

     - `$ phonegap plugin list`
     - `$ cordova plugin list`

>The platform specific plugin code will be copied into the target platform when a `prepare`, `build` or `run` command is specified using one of the CLI's. 
>If the plugin supports the `browser` platform, it will be copied to that target when the `phonegap serve` command is run. 

### Exercise 2

Take a moment and try out some plugin commands with one of your Cordova or PhoneGap projects now to see how you can add, remove and list plugins.

>If you need to create a project first with the CLI, do so with the following commands, from the Cordova or PhoneGap CLI respectively: `$ cordova create myAppProject` or `$ phonegap create myAppProject`, then `cd` into `myAppProject` and run the plugin commands listed above.

<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="index.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="lesson2.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>
