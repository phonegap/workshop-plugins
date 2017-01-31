---
layout: module
title: Module 4&#58; Plugin Definition
---
_approximate duration : 15 minutes_

## Plugin XML Definition

Plugins are defined using a top-level metadata file named `plugin.xml` within your plugin project. Open the `plugin.xml` file created in your template project and note the sections described below. 

- **Plugin Metadata** - the attributes defined on the plugin element are the `id` and `version` with the 1st child element defining the plugin name.   

      <plugin xmlns="http://cordova.apache.org/ns/plugins/1.0"
            id="org.devgirl.testplugin" version="0.0.1">
      <name>MyAwesomePlugin</name>

- **JavaScript code** - the JavaScript interface is defined in the `<js-module>` element. This is the interface called by the app developer to invoke the native platform code for the plugin. The name specified in the target is used to access the plugin functions from your Cordova app (ie: `Template.echo()`)

      <js-module src="www/template.js" name="Template">
          <clobbers target="Template" />
      </js-module>


- **Platform Code Definition** - a `<platform`> element is defined for each platform supported by a plugin. The `<feature>` element specifies the name to use for the plugin service and maps it to the
  class name for each platform. In the case of Android it will need to be prefixed with the package id as shown below. This mapping is used to 
  locate the code to run when the service is called. 

  **Android** <br>

      <platform name="android">
          <config-file target="res/xml/config.xml" parent="/*">
              <feature name="Echo" >
                  <param name="android-package" value="org.apache.cordova.test.Echo"/>
              </feature>
          </config-file>
          <source-file src="src/android/Echo.java" target-dir="src/org/apache/cordova/test" />
      </platform>

  **iOS** <br>

      <platform name="ios">
        <config-file target="config.xml" parent="/*">
            <feature name="Echo">
                <param name="ios-package" value="CDVEcho"/>
            </feature>
        </config-file>
        <source-file src="src/ios/CDVEcho.m"/>
      </platform>


- **Dependencies** - the `<dependency>` tag allows you to specify other plugins on which the current plugin depends. The plugins are referenced by their unique npm ids or by github url.

      <dependency id="cordova-plugin-someplugin" url="https://github.com/myuser/someplugin" />
      <dependency id="cordova-plugin-someplugin" version="1.0.1">

>See [the cordova-plugin-file-transfer plugin](https://github.com/apache/cordova-plugin-file-transfer/blob/master/plugin.xml) for an example

### Resources
Check out the complete [plugin.xml specification](http://cordova.apache.org/docs/en/latest/plugin_ref/spec.html) for a complete list of supported values. 


<!-- Add plugin validation? -->


<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="lesson3.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="lesson5.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>
