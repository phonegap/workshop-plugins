---
layout: module
title: Module 5&#58; Add Swipeout Handling
---

### Overview
In this step we'll add a common mobile UX feature to our app to make it more useful; swipeouts. Swipeouts
allow you to swipe left or right over list elements to reveal further actions.

The iOS Reminders app is a good example of an app using swipeouts:

   <img class="screenshot-md2" src="images/remind2.png"/>

## Steps
1. Take a moment to review the [Framework7 Swipeout Docs](http://framework7.io/docs/swipeout.html)

1. Open `index.html`, locate the `results` template and within the list, add the `swipeout` class to the existing `<li>` tag
such as:

      `<li class="swipeout">`

2. Now add a new `<div>` element with the class of `swipeout-content` just below the `<li>`
and ending `</div>` just before the <`/li`>
{% raw %}
        <div class="swipeout-content">
        <ul>
            {{#each tracks.items}}
            <!-- Workshop - add swipeout-->
            <li class="swipeout">
            <div class="swipeout-content">
                <a href="#" class="item-link item-content"
                data-item="{{@index}}"
                data-context="{{stringify this}}"
                data-template="details">
                <div class="item-media">
                    <img width="80" src="{{this.album.images[0].url}}">
                </div>
                <div class="item-inner">
                    <div class="item-title-row">
                    <div class="item-title">{{this.name}}</div>
                    <div class="item-after">{{durationFromMs this.duration_ms}}</div>
                    </div>
                    <div class="item-subtitle">{{this.artists[0].name}}</div>
                    <div class="item-text">{{this.album.name}}</div>
                </div>
                </a>
            </div>
            </li>
            {{/each}}
        </ul>
    {% endraw %}

2. Add the following snippet just before the closing `</li>`. This code will create the action itself
with a link containing a `share` class that we'll listen to for clicks(taps) and pass along the index of the
item clicked. It also sets a different share icon based on the platform.
 {% raw %}
                <!-- Swipeout actions right -->                
                <div class="swipeout-actions-right">
                    <!-- Swipeout actions links/buttons -->
                    <a href="#" class="share" data-item="{{@index}}">
                    {{#if @global.material}}
                        <i class="icon fa fa-share-alt fa-3x"></i></a>
                    {{else}}
                        <i class="icon fa fa-share fa-3x"></i></a>
                    {{/if}}                      
                </div>

     

     {% endraw %}

2. In the above definition we have an icon which acts as a button in the `swipeout-actions-right` 
but it doesn't actually do anything yet. It requires click handling code to invoke a *share* feature 
that will be added in the next lesson.

4. Run your app to ensure you see the new swipeout action on the right side when you swipe on a list item.

    <img class="screenshot-md2" src="images/ios-swipeout.png"/>
    <img class="screenshot-md2" src="images/android-swipeout.png"/>  

   >IMPORTANT: Based on the Framework7 docs, the swipeout support will not work well in the browser so you should test this feature via the PhoneGap Developer App or the CLI locally.

<div class="row" style="margin-top:40px;">
<div class="col-sm-12">
<a href="lesson4.html" class="btn btn-default"><i class="glyphicon glyphicon-chevron-left"></i> Previous</a>
<a href="lesson6.html" class="btn btn-default pull-right">Next <i class="glyphicon
glyphicon-chevron-right"></i></a>
</div>
</div>
