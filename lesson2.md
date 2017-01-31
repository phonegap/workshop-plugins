---
layout: module
title: Lesson 2&#58; Plugin Template
---
_approximate duration : 10 minutes_

## Plugin Creation Tools

- The [phonegap-plugin-template](https://github.com/phonegap/phonegap-plugin-template) tool makes it easy to create a new plugin by scaffolding a plugin project template for you.

    1. If you haven't already installed this tool, do so now with the following command:

        `$ npm install -g phonegap/phonegap-plugin-template`

    2. To create a new plugin project, type the following command, specifying your desired a file path, plugin name and id 

        `$ phonegap-plugin-create PATH NAME ID`

        For example:<br>

        `$ phonegap-plugin-create ~/MyAwesomePlugin MyAwesomePlugin my-awesome-plugin`

## Plugin Project Structure 

Once you create your plugin project using the **phonegap-plugin-template** tool, you can `cd` into the new project and you will see a structure that looks like the following:

![](images/plugin-structure.png)

You can open each file in your favorite editor and start modifying with the relevant parts for your plugin. In the next few sections we'll cover each of the pieces that make up a plugin. 

### Exercise 3

1. Create a new plugin using the `phonegap-plugin-template`
2. Open the plugin.xml and uncomment the Android and iOS platform specific sections
3. Add your new plugin to a PhoneGap or Cordova app project 

>Tip: Use the --link flag when you add the plugin locally during developmet and Cordova will create a symbolic link to it. This way any source updates will automatically be available to your project ie: `$ cordova plugin add --link ~/path/to/plugin`

>When removing a locally added plugin, specify the plugin id - ie: `my-awesome-plugin`. You can retrieve the list of plugins added to a project by typing `phonegap plugin list`

<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="index1.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="lesson3.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>
