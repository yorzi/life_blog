title: Ajax Support in Rails
link: http://blog.wangyaodi.com/2009/11/26/ajax-support-in-rails/
creator: yorzi
description: 
post_id: 135
post_date: 2009-11-26 18:05:17
post_date_gmt: 2009-11-26 10:05:17
comment_status: open
post_name: ajax-support-in-rails
status: publish
post_type: post

# Ajax Support in Rails

**Topics** Ajax/JavaScript libraries in Rails PrototypeHelper ScriptaculousHelper JavaScriptMacrosHelper JavaScript related utility methods Ruby JavaScript template **Ajax/JavaScript Libraries in Rails** • Prototype - used mainly for Ajax > ActionView::Helpers::PrototypeHelper • Scriptaculous - used mainly for visual effects, drag and drop, auto-completion > ActionView::Helpers::ScriptaculousHelper • JavaScript related utility methods > ActionView::Helpers::JavaScriptHelper • Others can be easily added **How to Include Ajax?JavaScript Libraries** • Option 1: Use <%= javascript_include_tag :defaults %> in the HEAD section of your page (recommended): > Return references to the JavaScript files in your public/javascripts directory. > Recommended as the browser can then cache the libraries instead of fetching all the functions anew on every request. • Option 2: Use <%= javascript_include_tag ‘prototype’ %> > Will only include the Prototype core library • Option 3: Use <%= define_javascript_functions %> > Will copy all the JavaScript support functions within a single script block. Not recommended. SEE MORE DETAILS VIA [Download the PDF](/2009/11/26/ajax-support-in-rails/rails_ajax/) stuff.