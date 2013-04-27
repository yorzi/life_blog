title: Session in Ruby on Rails
link: http://blog.wangyaodi.com/2009/12/29/session-in-ruby-on-rails/
creator: yorzi
description: 
post_id: 273
post_date: 2009-12-29 13:31:34
post_date_gmt: 2009-12-29 05:31:34
comment_status: open
post_name: session-in-ruby-on-rails
status: publish
post_type: post

# Session in Ruby on Rails

**session**: a way to store information across pages. **set value as:** session[:person] = ＠user **read values as:** Hello #{session[:person]} **set as nil:** session[:person] = nil **reset all sessions** reset_session There are many solutions to store session in ruby on rails, including **PStore** [it's the default way in rails] **ActiveRecordStore** [to use ActiveRecord, better to share information across apps in this way] **DRbStore** **FileStore** **MemoryStore** Much more compares on above solutions : check out [Ruby on Rails Session Container Performance](http://scott.elitists.net/sessions.html) see the details.