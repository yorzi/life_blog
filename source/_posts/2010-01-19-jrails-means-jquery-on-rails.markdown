---
layout: post
title: jRails means jQuery on Rails
categories:
- Tech Notes
tags:
- jquery
- jrails
- prototype
- ror
- visual-effects
published: true
comments: true
---
<p><em><strong>Note: This introduction post to jRails is copied(mirrored) form <a href="http://mirror.ozdiy.com/assets/b8/2f96a12bc919b37e09d303b86ea1b9_1251811910.html#install">this link</a>, so that I can bakeup this for advanced learning.</strong></em>
<div>
<h2>Intro</h2>
jRails is a drop-in <a href="http://jquery.com/">jQuery</a> replacement for <a href="http://www.prototypejs.org/">Prototype</a>/<a href="http://script.aculo.us/">script.aculo.us</a> on Rails.  		Using jRails, you can get all of the same default Rails helpers for javascript functionality using the lighter jQuery library.</div>
<a name="news"></a>
<div>
<h2>News</h2>
<h3>jRails 0.4 : jQuery 1.5!</h3>
jQuery-UI has just gotten a major update to version 1.5 which stabilizes most of the controls and incorporates the Enchant effects library. jRails follows suit with a single js file for jquery-ui that includes both the modules and effects. The default jRails installation includes a compressed jquery-ui js file that includes the basic modules and effects supported by Prototype/Scriptaculous. There are no modifications to this file, so if you'd like to generate your own with additional modules or effects, just pop on over to the jQuery UI site and <a href="http://ui.jquery.com/download_builder/">customize your own</a>.</div></p>

<p>This release of jRails also adds support for jQuery.noConflict(). Just uncomment the line in the init.rb file and set it to whatever you like. Now you can use jRails with other libraries without causing problems.
<a name="features"></a>
<div>
<h2>Features</h2>
jRails provides drop-in functionality for these existing Rails methods.
<ul>
	<li>
<ul>
	<li><strong>Prototype</strong></li>
	<li>form_remote_for</li>
	<li>form_remote_tag</li>
	<li>link_to_remote</li>
	<li>observe_field</li>
	<li>observe_form</li>
	<li>periodically_call_remote</li>
	<li>remote_form_for</li>
	<li>submit_to_remote</li>
</ul>
</li>
	<li>
<ul>
	<li><strong>Scriptaculous</strong></li>
	<li>draggable_element</li>
	<li>drop_receiving_element</li>
	<li>sortable_element</li>
	<li>visual_effect</li>
</ul>
</li>
	<li>
<ul>
	<li><strong>RJS</strong></li>
	<li>hide</li>
	<li>insert_html</li>
	<li>remove</li>
	<li>replace</li>
	<li>replace_html</li>
	<li>show</li>
	<li>toggle</li>
</ul>
</li>
</ul>
</div>
<a name="effects"></a>
<div>
<h2>Visual Effects</h2>
These are the current effects that are included by default in jRails.
<div>
<div style="display: block;" onclick="$(this).hide().appear()" /></div></div></p>

<p>Appear

<div>
<div style="display: block;" onclick="$(this).fade().pause(1500).appear()" /></div></p>

<p>Fade

<div>
<div style="display: block;" onclick="$(this).puff().pause(1500).appear()" /></div></p>

<p>Puff

<div>
<div onclick="$(this).blindDown()" /></div></p>

<p>BlindDown

<div>
<div onclick="$(this).blindUp().pause(1500).appear()" /></div></p>

<p>BlindUp

<div>
<div onclick="$(this).blindRight()" /></div></p>

<p>BlindRight

<div>
<div style="display: block;" onclick="$(this).blindLeft().pause(1500).appear()" /></div></p>

<p>BlindLeft

<div>
<div style="display: block;" onclick="$(this).switchOff().pause(1500).appear()" /></div></p>

<p>SwitchOff

<div>
<div style="display: block;" onclick="$(this).switchOn()" /></div></p>

<p>SwitchOn

<div>
<div onclick="$(this).slideDown()" /></div></p>

<p>SlideDown

<div>
<div style="display: block;" onclick="$(this).slideUp().pause(1500).appear()" /></div></p>

<p>SlideUp

<div>
<div onclick="$(this).dropIn()" /></div></p>

<p>DropIn

<div>
<div style="display: block;" onclick="$(this).dropOut().pause(1500).appear()" /></div></p>

<p>DropOut

<div>
<div onclick="$(this).shake()" /></div></p>

<p>Shake

<div>
<div style="opacity: 1;" onclick="$(this).pulsate()" /></div></p>

<p>Pulsate

<div>
<div style="display: block;" onclick="$(this).squish().pause(1500).appear()" /></div></p>

<p>Squish

<div>
<div style="display: block;" onclick="$(this).fold().pause(1500).appear()" /></div></p>

<p>Fold

<div>
<div onclick="$(this).foldOut()" /></div></p>

<p>FoldOut

<div>
<div style="display: block;" onclick="$(this).grow()" /></div></p>

<p>Grow

<div>
<div style="display: block;" onclick="$(this).shrink().pause(1500).appear()" /></div></p>

<p>Shrink

<div>
<div onclick="$(this).highlight()" /></div></p>

<p>Highlight


<a name="howto"></a>
<h2>How to use</h2>
Just install and go!  		Once installed, the previous Prototype/script.aculo.us helpers will be replaced by jQuery ones.  		In order for them to function correctly, just include the appropriate javascript files in the head of your page.
<div>
<pre>&lt;script src="/javascripts/jquery.js" type="text/javascript"&gt;&lt;/script&gt;
&lt;script src="/javascripts/jquery-ui.js" type="text/javascript"&gt;&lt;/script&gt;
&lt;script src="/javascripts/jrails.js" type="text/javascript"&gt;&lt;/script&gt;</pre>
</div>
You can also use the Rails javascript_include_tag helper with :default to load them automagically.
<div>
<pre>&lt;%= javascript_include_tag :defaults %&gt;</pre>
</div>
<a name="installation"></a>
<div>
<h2>Install</h2>
To install the jRails plugin:
<div>
<pre>./script/plugin install git://github.com/aaronchi/jrails.git</pre>
</div>
Then copy the javascript files in the plugin folder to your javascripts directory.</div>
<a name="changelog"></a>
<div>
<h2>Changelog</h2>
<ul>
	<li><label>0.1.0 </label>: Initial Release</li>
	<li><label>0.2.0 </label>: Major Effects Updates</li>
	<li><label>0.3.0 </label>: jQuery Enchant</li>
	<li><label>0.4.0 </label>: jQuery-ui 1.5 and jQuery.noConflict support</li>
</ul>
</div>
<a name="contact"></a>
<div>
<h2>Contact</h2>
You can post to the <a href="http://groups.google.com/group/jrails">jRails group forum</a> and I'll get back to you as soon as I can</div></p>

<p>Comments, bug reports and feedback are welcomed.  		I'm also considering developing a similar library for <a href="http://mootools.net/">MooTools</a> so if you are interested, please let me know.</p>
