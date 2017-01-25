---
layout: module
title: Module 2&#58; Defining your Plugin
---
_approximate duration : 15 minutes_

## Plugin Creation Tools

- The [phonegap-plugin-template](https://github.com/phonegap/phonegap-plugin-template) tool makes it easy to create a new plugin by scaffolding a plugin project template for you.

    1. If you haven't already installed this tool, do so now with the following command:

        `$ npm install -g phonegap/phonegap-plugin-template`

    2. To create a new plugin project, tyep the following command and specify a file path, plugin name and id 

        `$ phonegap-plugin-create PATH NAME ID`

        For example:<br>

        `$ phonegap-plugin-create ~/MyNewPlugin MyNewPlugin org.mycompany.myplugin`

## Plugin Project Structure 
Once you create your plugin project using the **phonegap-plugin-template** tool, you can `cd` into the new project and you will see a structure that looks like the following:
![](images/plugin-structure.png)

You can open each file in your favorite editor and start modifying with the relevant parts for your plugin. In the next few sections we'll cover each of the pieces that make up a plugin. 

## Plugin XML Definition

Plugins are defined using a top-level file named `plugin.xml` within your plugin project. Open the one in your template project and note the pieces described below. 

  - Plugin Metadata

    <plugin xmlns="http://cordova.apache.org/ns/plugins/1.0"
           id="org.devgirl.testplugin" version="0.0.1">
    <name>MyAwesomePlugin</name>

  - Shared JavaScript code
 
    <js-module src="www/template.js" name="Template">
        <clobbers target="Template" />
    </js-module>

  - **Platform Code* Definition*

    <platform name="android">
        <config-file target="res/xml/config.xml" parent="/*">
            <feature name="Echo" >
                <param name="android-package" value="org.apache.cordova.test.Echo"/>
            </feature>
        </config-file>
        <source-file src="src/android/Echo.java" target-dir="src/org/apache/cordova/test" />
    </platform>

  - Dependencies
  The `<dependency>` tag allows you to specify other plugins on which the current plugin depends. The plugins are referenced by their unique npm ids or by github url.

### Exercise 3

1. Create a plugin using the above tools
2. Add dependencies to use two additional plugins
3. Install your new plugin to a PhoneGap or Cordova app project

<!-- Add plugin validation? -->


<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="lesson1.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="lesson3.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>
