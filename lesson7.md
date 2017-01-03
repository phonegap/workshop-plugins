---
layout: module
title: Module 7&#58; Making Your App Feel Native
---

## Overview
In this module we're going to discuss ways to make your app feel and act native. Many of the tips included here are built into Framework7 so you
will not need to implement them in this particular app but it's important to be aware of them when building hybrid apps.

1. **Remove tap highlight**
    - Remove the highlight effect when tapping on a link if you're not handling it properly:

    <img class="screenshot-md" src="images/webkit-tap-highlight.png"/>
        
    Fix with:
    
         -webkit-tap-highlight-color: rgba(0,0,0,0);
         -webkit-tap-highlight-color: transparent;
            
    Hold tap on a list item or other element and notice how it's affected when the above is not set..                         

1. **Disable user selections** on actionable elements (for instance a select on a long tap)

    <img class="screenshot-md" src="images/webkit-user-select.png"/>

    Fix with:

	    -webkit-user-select: none;		 

    Use the following `<meta>` tag in your `index.html` for Microsoft platform support:

        <meta name="msapplication-tap-highlight" content="no">

   >Keep `-webkit-user-select: text;` for text input fields or you won't be able to edit your text.

1. **Remove the glossy appearance** from controls on iOS   

   <img class="screenshot-md" src="images/ios-glossy.png"/>

   Fix it with:

        -webkit-appearance: none;


3. **Disable touch callout** (default callout that displays when you hold down on a link)

   <img class="screenshot-md" src="images/webkit-touch-callout.png"/>

        -webkit-touch-callout: none

   >See this article: [Touch callout disabled](http://phonegap-tips.com/articles/essential-phonegap-css-webkit-touch-callout.html)

3. **Use Native Scrolling** - if the UI framework you're using doesn't have this set on the classes you're using for your containers you should
 set it.

    <img class="screenshot-full" src="images/native-scroll-fix.png"/>

        -webkit-overflow-scrolling: touch;

   >On Android 4+ every scrollable container has momentum scrolling.

4. **Use System Fonts**

   Ensure you're using the fonts native to the platform. Here's some general rules:
    
    - iOS: `font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;`

    - Android: `font-family: 'RobotoRegular', 'Droid Sans', sans-serif;`

    - Windows Phone: `font-family: 'Segoe UI', Segoe, Tahoma, Geneva, sans-serif;`
  
5. **Manage Click Delay** - ensure you're using [FastClick](https://github.com/ftlabs/fastclick) or something similar to handle tap delay on mobile.

>All of the tips in the above list are already built into Framework7 but important to understand when building hybrid apps.

## Optional
If you're running an app through the CLI on a native simulator or device (outside of PhoneGap Developer), you can test out some of these CSS tricks
 using the Safari Developer tools while remote debugging on your iOS device or the Chrome Developer tools remote debugging your Android device.

>See [this guide](lesson10.html) for remote debugging details

Open up to inspect and modify some of the CSS properties applied from the Framework7 CSS.

1. Change tap highlight to a color instead of transparent, such as `-webkit-tap-highlight-color: green;`. Then try clicking on one of the links on the side panel
menu to see what happens. 
2. Comment out `-webkit-touch-callout: none;` or change it to another value. Then hold down (long tap) on a link.
3. Comment out `-webkit-appearance: none;`
4. While in the results view of the app, comment out the `-webkit-overflow-scrolling: touch;` property in the `.page-content` definition and notice the
 impact on the scrolling feel.
5. Try holding down on one of the titles. You will see it get selected and a menu shown to copy etc. Deselect it,
then add `-webkit-user-select: none;` to the `.body` definition in the CSS and try it again to see what happens.

## Performance Tips

3. **Lazy load** - images and virtual lists (delay loading of images while outside of viewport until user scrolls to them)

    <img class="screenshot-md" src="images/without-lazy-load.png"/>
    <img class="screenshot-md" src="images/lazy-load-class.png"/>
    <img class="screenshot-md" src="images/with-lazy-load.png"/>
    
    In Framework7 you can easiy use lazy loading by specifying `class="lazy"` on an `<img>` tag and ensuring you're using `data-src`
    not just `src`. For example:
    
        <img width="80" data-src="{{this.album.images[0].url}}" class="lazy">
        
   **BONUS STEP**
   - Update your app to use lazy loading on images where you feel necessary and check to see the difference. You should see a grey box load
   initially until the image is loaded indicating there is indeed an image there.      

1. Use Progressive Enhancement - check the [Can I Use]() website and provide polyfills for platforms without support

2. Use Hardware Accelerated animations and view transitions (trick to force them to use the GPU - faster than CPU)

        .page-on-left {
            opacity: .9;
            -webkit-transform: translate3d(-20%, 0, 0);
            transform: translate3d(-20%, 0, 0)
        }

        .page-on-center .swipeback-page-shadow {
            opacity: 1
        }

        .page-on-right {
            -webkit-transform: translate3d(100%, 0, 0);
            transform: translate3d(100%, 0, 0)
        }


1. Serve properly sized images for all different resolutions. Resolution-independent images (SVG) are a great option and scale well.

   >The [Native Transitions Plugin](http://plugins.telerik.com/cordova/plugin/native-page-transitions) is a Cordova plugin to help increase the speed of your transitions.  The plugin immediately grabs a screenshot
   of your webview (making a more lightweight view), then waits for the new content to load, and then performs the transition by animating out the
   screenshot and in the new view.

4. **HTML Caching** - attempt to load pages from memory first where possible

5. Add the plugin to use the super fast WKWebView on iOS - [guide here](http://devgirl.org/2016/01/11/a-faster-hybrid-app-for-the-new-year/)

<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="lesson6.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="lesson8.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>
