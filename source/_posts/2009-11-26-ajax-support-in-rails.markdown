---
layout: post
title: Ajax Support in Rails
categories:
- Reading Marks
- Tech Notes
tags:
- ajax
- javascript
- prototype
- rails
- RJS
- scriptaculous
published: true
comments: true
---
<p><strong>Topics</strong>
  Ajax/JavaScript libraries in Rails<br />
  PrototypeHelper<br />
  ScriptaculousHelper<br />
  JavaScriptMacrosHelper<br />
  JavaScript related utility methods<br />
  Ruby JavaScript template</p>

<p><strong>Ajax/JavaScript Libraries in Rails</strong>
• Prototype - used mainly for Ajax<br />
  > ActionView::Helpers::PrototypeHelper<br />
• Scriptaculous - used mainly for visual effects, drag and drop, auto-completion<br />
  > ActionView::Helpers::ScriptaculousHelper<br />
• JavaScript related utility methods<br />
  > ActionView::Helpers::JavaScriptHelper<br />
• Others can be easily added</p>

<p><strong>How to Include Ajax?JavaScript Libraries</strong>
• Option 1: Use <%= javascript_include_tag :defaults %> in the HEAD section of your page (recommended):<br />
   > Return references to the JavaScript files in your public/javascripts directory.<br />
   > Recommended as the browser can then cache the libraries instead of fetching all the functions anew on every request.<br />
• Option 2: Use <%= javascript_include_tag ‘prototype’ %>
   > Will only include the Prototype core library<br />
• Option 3: Use <%= define_javascript_functions %>
   > Will copy all the JavaScript support functions within a single script block. Not recommended.</p>

<p>SEE MORE DETAILS VIA <a href="http://blog.wangyaodi.com/2009/11/26/ajax-support-in-rails/rails_ajax/" rel="attachment wp-att-136">Download the PDF</a> stuff.</p>
