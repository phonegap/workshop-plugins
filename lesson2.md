---
layout: module
title: Lesson 2&#58; Plugin Scaffolding
---
<!--_approximate duration : 10 minutes_-->

## Plugin Template

The [phonegap-plugin-template](https://github.com/phonegap/phonegap-plugin-template) tool makes it easy to create a new plugin by scaffolding a plugin project template for you.

1. You can install the tool with the following command:

        $ npm install -g phonegap/phonegap-plugin-template

2. To create a new plugin project, type the `phonegap-plugin-create` command along with your desired file path, plugin name and id.

        $ phonegap-plugin-create PATH NAME ID

   For example:<br>

        $ phonegap-plugin-create ~/MyAwesomePlugin MyAwesomePlugin my-awesome-plugin

>The template creates a working plugin called Echo, which takes a String parameter and returns it back to the caller via a "success" callback function.

## Plugin Project Structure

Once you create your plugin project using the **phonegap-plugin-template** tool, you can `cd` into the new project and you will see a structure that looks like the following:

![](images/plugin-structure.png)

### Exercise 

1. Create a new plugin using the **phonegap-plugin-template** tool
2. Open the `plugin.xml` and uncomment the Android and iOS `<platform>` specific sections
3. Add your new plugin to a PhoneGap or Cordova app project

>If you don't have a Cordova or PhoneGap project handy for testing with your new plugin, you can create a new one using the Cordova or PhoneGap CLI respectively: `$ cordova create myAppProject` or `$ phonegap create myAppProject`, then `cd` into `myAppProject` and add your plugin.

>**Tip:** You can use the `--link` flag when you add the plugin locally during developmet and Cordova will create a symbolic link to the plugin folder. This way any native source code updates you make will automatically be available to your project ie: `$ cordova plugin add --link ~/path/to/plugin`. When removing a locally added plugin, specify the plugin id - ie: `my-awesome-plugin`. You can retrieve the list of plugins added to a project by typing `phonegap plugin list`.

<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="lesson1.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="lesson3.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>
