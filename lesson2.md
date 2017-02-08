---
layout: module
title: Lesson 2&#58; Plugin Template
---
<!--_approximate duration : 10 minutes_-->

## Plugin Template

The [phonegap-plugin-template](https://github.com/phonegap/phonegap-plugin-template) tool makes it easy to create a new plugin by scaffolding a plugin project template for you.

1. You can install the tool with the following command:

        $ npm install -g phonegap/phonegap-plugin-template

2. To create a new plugin project, type the `phonegap-plugin-create` command along with your desired file path, plugin name and id.

        $ phonegap-plugin-create PATH NAME ID

>The template creates a working plugin called Echo, which takes a String parameter and returns it back to the caller via a "success" callback function.

## Plugin Project Structure

Once you create your plugin project using the **phonegap-plugin-template** tool, you can `cd` into the new project and you will see a structure that looks like the following:

![](images/plugin-structure.png)

### Exercise 

1. Create a **new plugin** using the `phonegap-plugin-create` command. 

   >**NOTE:** Use a different plugin name and id like below and create your plugin at the same directory level as your `myApp` project but not within it.


        $ phonegap-plugin-create MyEchoPlugin myechoplugin my-echo-plugin

2. Now open the `plugin.xml` and uncomment these Android and iOS `<platform>` specific sections (we will need this to test with later):

        <platform name="android">
            <config-file target="res/xml/config.xml" parent="/*">
                <feature name="Echo" >
                    <param name="android-package" value="org.apache.cordova.test.Echo"/>
                </feature>
            </config-file>
            <source-file src="src/android/Echo.java" target-dir="src/org/apache/cordova/test" />
        </platform>

        <platform name="ios">
            <config-file target="config.xml" parent="/*">
                <feature name="Echo">
                    <param name="ios-package" value="CDVEcho"/>
                </feature>
            </config-file>
            <source-file src="src/ios/CDVEcho.m" />
        </platform>

3. `cd` into your Cordova app and add your new plugin

       $ cd myApp
       $ cordova plugin add --link ../MyEchoPlugin

4. Verify the plugin has been added

       $ cordova plugin list

   >**Tip:** You can use the `--link` flag when you add the plugin locally during developmet and Cordova will create a symbolic link to the plugin folder. This way any native source code updates you make will automatically be available to your project ie: `$ cordova plugin add --link ~/path/to/plugin`. Note that this does not include changes made to your JavaScript interface. You will need to remove and re-add your plugin for those updates. 

   >When removing a locally added plugin, specify the plugin id - ie: `my-echo-plugin`. You can retrieve the list of plugins added to a project by typing `phonegap plugin list`.

5. If you ran the app now, it wouldn't actually do anything with our plugin yet since we haven't added any code to invoke it from our app.

<!--
##### Creating a Project for Testing
If you don't have a Cordova or PhoneGap project handy for testing with your new plugin, you can simply create a new one using the Cordova or PhoneGap CLI: `$ cordova create myAppProject` or `$ phonegap create myAppProject`, then `cd` into `myAppProject` and add your plugin.-->


<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="lesson1.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="lesson3.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>
