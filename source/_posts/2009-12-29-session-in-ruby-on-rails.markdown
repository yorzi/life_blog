---
layout: post
title: Session in Ruby on Rails
categories:
- Tech Notes
tags:
- note
- ror
- session
- tech
published: true
comments: true
---
<p><strong>session</strong>: a way to store information across pages.</p>

<p><strong>set value as:</strong>
        session[:person] = ＠user</p>

<p><strong>read values as:</strong>
        Hello #{session[:person]}</p>

<p><strong>set as nil:</strong>
        session[:person] = nil</p>

<p><strong>reset all sessions</strong>
        reset_session</p>

<p>There are many solutions to store session in ruby on rails, including
<strong>PStore</strong> [it's the default way in rails]
<strong>ActiveRecordStore</strong> [to use ActiveRecord, better to share information across apps in this way]
<strong>DRbStore</strong>
<strong>FileStore</strong>
<strong>MemoryStore</strong></p>

<p>Much more compares on above solutions : check out <a href="http://scott.elitists.net/sessions.html">Ruby on Rails Session Container Performance</a> see the details.</p>
