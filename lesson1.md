---
layout: module
title: Lesson 1&#58; Plugin Discovery and Installation
---

<!--_approximate duration : 10 minutes_-->

<!--
for cordova-plugin-device, I showed the repo, then I explained the contents of plugin.xml
then I showed how each plugin.xml element mapped to an output project
then I explained how the device.js file was able to send/receive messages from the native layer via exec
then I created a new project, installed the plugin and step debugged the native parts in xcode
-->

## Plugin Discovery
Plugins are used to extend the native functionality exposed by the PhoneGap native app container. Examples of plugins include those that allow to access the Camera, Battery Status, Push Notifications, Geolocation, 
Barcode Scanning, Native Social Sharing and many more. The [npm registry](http://nmpjs.org) is used to find plugins currently available to the community. You can discover the latest by searching `ecosystem:cordova`.

>Plugins may often be prefixed with a naming convention depending on the goal of the plugin. All of the core supported Cordova plugins are prefixed 
with `cordova-*`, while those specifically created by the PhoneGap team are prefixed with `phonegap-*`. Ionic has a [marketplace for Ionic specific Cordova plugins](https://market.ionic.io/plugins), with most of those
prefixed with `ionic-*`. Telerik also has a [plugin marketplace](http://plugins.telerik.com/cordova) to be aware of with their verified Cordova plugins that may or may not be found in the official npm plugin registry. 

Navigate to [npmjs.org](http://npmjs.org) and do your own search for Cordova plugins now to see what you can find. Does it look like the picture below? Scroll through and take a look at all of the different plugins already available. 

![](images/npm-plugin-search.png)


## Plugin Command Review 
Add, remove and list plugins using the following commands from the [Cordova](https://www.npmjs.com/package/cordova-cli) or [PhoneGap CLI](https://www.npmjs.com/package/phonegap).

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

## Exercise

1. Create a folder called `MyPlugin` and `cd` into it

        $ mkdir MyPlugin
        $ cd MyPlugin/

2. Create a file called `plugin.xml` 

        $ touch plugin.xml

3. Open `plugin.xml` and enter the following:

        <?xml version="1.0" encoding="UTF-8"?>
        <plugin xmlns="http://apache.org/cordova/ns/plugins/1.0"
            xmlns:android="http://schemas.android.com/apk/res/android"
            id="org-me-myplugin"
            version="0.0.1">
            <name>myplugin</name>
        </plugin>

4. Create a basic Cordova project if you don't have one already

        $ cordova create ../MyApp

5. `cd` into the new app project

        $ cd ../MyApp/

2. Add your plugin 

        $ cordova plugin add ../MyPlugin

3. List the plugins to ensure it's been added

        $ cordova plugin list

4. **You must remove the plugin before moving on to the next step**

        $ cordova plugin remove org-me-myplugin

**Add plugin dependencies**

1. Now go back into your plugin and edit the `plugin.xml` to add the following dependencies

        <dependency id="cordova-plugin-device"/>
        <dependency id="cordova-plugin-console"/>

2. `cd` into your app project and **add your plugin again**

        $ cordova plugin add ../MyPlugin

3. If no platforms were installed, you will need to add your platform to see them installed




<!--
### Exercise 

1. Create a simple plugin using an existing plugin's `plugin.xml` file as a resource (for instance [cordova-plugin-device](https://github.com/apache/cordova-plugin-device))
2. Add dependencies to two additional plugins
3. Add your new plugin to a PhoneGap or Cordova app project 

>Tip: You can use the --link flag when you add the plugin locally during developmet and Cordova will create a symbolic link to it. This way any source updates will automatically be available to your project. 

        `$ cordova plugin add --link ~/path/to/plugin`

>If you need to create a project first with the CLI, do so with the following commands, from the Cordova or PhoneGap CLI respectively: `$ cordova create myAppProject` or `$ phonegap create myAppProject`, then `cd` into `myAppProject` and run the plugin commands listed above.
-->
<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="index.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="lesson2.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>
