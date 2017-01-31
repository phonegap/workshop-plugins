---
layout: module
title: Module 6&#58; Plugin Publishing
---

_approximate duration : 5 minutes_

## Plugin Searchability

You can add keywords to your plugin's `package.json` file at the root of the project to ensure it is found in the list of all cordova plugins and for the specific platforms supported. 

1. All published plugins to be shared should specify the `ecosystem:cordova` keyword to ensure it's always returned in the cordova plugins search results.
2. Cordova platform keywords can be specified to indicate which are supported with a `cordova-<platform>` syntax.

For instance, a `package.json` may have the following keywords specified:

    "keywords": [
        "ecosystem:cordova",
        "cordova-android",
        "cordova-ios",
        "cordova-windows"
    ]

> **Note:** Plugman's `createpackagejson` will do step #2 for you but if you didn't use that method, you can simply edit your `package.json` manually.

## Plugin Dependencies

Specify the Cordova-related dependencies for your plugin in the `package.json` file to provide guidance to the Cordova CLI when fetching from npm.
To specify dependencies for a plugin, alter the `engines` element in `package.json` to include a `cordovaDependencies` object with the following structure:

    "engines": {
        "cordovaDependencies": {
            "1.0.0": { "cordova-android": "<3.0.0"},
            "2.1.0": { "cordova-android": ">4.0.0"}
        }
    }


## Publishing your Plugin
When you are ready to share your plugin with the community, you can do so using either npm or the plugman tool. 

### Using npm
You must have a user on the npm registry to publish, if you don't already have one you can create one using the `adduser` command as shown below:    

    $ npm adduser # (only if you don't have an account in the npm registry yet)
    $ npm publish /path/to/your/plugin

Or from within the top-level of the plugin project you can simply run:

    $ npm publish . 

### Using Plugman
While the `npm` method is the preferred way to publish your plugins, you should be aware that you could also use the plugman tool to do so as well.

    $ plugman publish myPluginDirectoryPath



<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="lesson5.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="lesson7.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>
