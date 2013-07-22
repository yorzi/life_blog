---
layout: post
title: Law of Demeter
categories:
- Reading Marks
- Tech Notes
tags:
- delegate
- demeter
- model
- rails
- refactor
- ruby
published: true
comments: true
---
<p>Rails Best Practice Snippet: Model refactor.<br />
Reference link to the PDF.<a href="http://blog.wangyaodi.com/2009/11/26/law-of-demeter/rails-best-practices-2/" rel="attachment wp-att-125">Rails-best-practices.</a></p>

<p>Before:
<code lang="ruby">
class Invoice < ActiveRecord::Base<br />
  belongs_to :user<br />
end
<%= @invoice.user.name %>
<%= @invoice.user.address %>
<%= @invoice.user.cellphone %>
</code>
After:
<code lang="rails">
class Invoice < ActiveRecord::Base<br />
  belongs_to :user<br />
  delegate :name, :address, :cellphone, :to => :user, :prefix => true<br />
end
<%= @invoice.user_name %>
<%= @invoice.user_address %>
<%= @invoice.user_cellphone %>
</code></p>

<p>See more details about <a href="http://api.rubyonrails.org/classes/Module.html#M000110">Delegate</a> in rails doc.</p>
