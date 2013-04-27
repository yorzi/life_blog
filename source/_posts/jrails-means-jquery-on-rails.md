title: jRails means jQuery on Rails
link: http://blog.wangyaodi.com/2010/01/19/jrails-means-jquery-on-rails/
creator: yorzi
description: 
post_id: 361
post_date: 2010-01-19 23:22:22
post_date_gmt: 2010-01-19 15:22:22
comment_status: open
post_name: jrails-means-jquery-on-rails
status: publish
post_type: post

# jRails means jQuery on Rails

_**Note: This introduction post to jRails is copied(mirrored) form [this link](http://mirror.ozdiy.com/assets/b8/2f96a12bc919b37e09d303b86ea1b9_1251811910.html#install), so that I can bakeup this for advanced learning.**_

## Intro

jRails is a drop-in [jQuery](http://jquery.com/) replacement for [Prototype](http://www.prototypejs.org/)/[script.aculo.us](http://script.aculo.us/) on Rails. Using jRails, you can get all of the same default Rails helpers for javascript functionality using the lighter jQuery library.

## News

### jRails 0.4 : jQuery 1.5!

jQuery-UI has just gotten a major update to version 1.5 which stabilizes most of the controls and incorporates the Enchant effects library. jRails follows suit with a single js file for jquery-ui that includes both the modules and effects. The default jRails installation includes a compressed jquery-ui js file that includes the basic modules and effects supported by Prototype/Scriptaculous. There are no modifications to this file, so if you'd like to generate your own with additional modules or effects, just pop on over to the jQuery UI site and [customize your own](http://ui.jquery.com/download_builder/). This release of jRails also adds support for jQuery.noConflict(). Just uncomment the line in the init.rb file and set it to whatever you like. Now you can use jRails with other libraries without causing problems.

## Features

jRails provides drop-in functionality for these existing Rails methods. 

  *     * **Prototype**
    * form_remote_for
    * form_remote_tag
    * link_to_remote
    * observe_field
    * observe_form
    * periodically_call_remote
    * remote_form_for
    * submit_to_remote
  *     * **Scriptaculous**
    * draggable_element
    * drop_receiving_element
    * sortable_element
    * visual_effect
  *     * **RJS**
    * hide
    * insert_html
    * remove
    * replace
    * replace_html
    * show
    * toggle

## Visual Effects

These are the current effects that are included by default in jRails. 

Appear

Fade

Puff

BlindDown

BlindUp

BlindRight

BlindLeft

SwitchOff

SwitchOn

SlideDown

SlideUp

DropIn

DropOut

Shake

Pulsate

Squish

Fold

FoldOut

Grow

Shrink

Highlight

## How to use

Just install and go! Once installed, the previous Prototype/script.aculo.us helpers will be replaced by jQuery ones. In order for them to function correctly, just include the appropriate javascript files in the head of your page. 
    
    <script src="/javascripts/jquery.js" type="text/javascript"></script>
    <script src="/javascripts/jquery-ui.js" type="text/javascript"></script>
    <script src="/javascripts/jrails.js" type="text/javascript"></script>

You can also use the Rails javascript_include_tag helper with :default to load them automagically. 
    
    <%= javascript_include_tag :defaults %>

## Install

To install the jRails plugin: 
    
    ./script/plugin install git://github.com/aaronchi/jrails.git

Then copy the javascript files in the plugin folder to your javascripts directory.

## Changelog

  * 0.1.0 : Initial Release
  * 0.2.0 : Major Effects Updates
  * 0.3.0 : jQuery Enchant
  * 0.4.0 : jQuery-ui 1.5 and jQuery.noConflict support

## Contact

You can post to the [jRails group forum](http://groups.google.com/group/jrails) and I'll get back to you as soon as I can Comments, bug reports and feedback are welcomed. I'm also considering developing a similar library for [MooTools](http://mootools.net/) so if you are interested, please let me know.