title: Law of Demeter
link: http://blog.wangyaodi.com/2009/11/26/law-of-demeter/
creator: yorzi
description: 
post_id: 123
post_date: 2009-11-26 11:24:54
post_date_gmt: 2009-11-26 03:24:54
comment_status: open
post_name: law-of-demeter
status: publish
post_type: post

# Law of Demeter

Rails Best Practice Snippet: Model refactor. Reference link to the PDF.[Rails-best-practices.](/2009/11/26/law-of-demeter/rails-best-practices-2/) Before: ` class Invoice < ActiveRecord::Base belongs_to :user end <%= @invoice.user.name %> <%= @invoice.user.address %> <%= @invoice.user.cellphone %> ` After: ` class Invoice < ActiveRecord::Base belongs_to :user delegate :name, :address, :cellphone, :to => :user, :prefix => true end <%= @invoice.user_name %> <%= @invoice.user_address %> <%= @invoice.user_cellphone %> ` See more details about [Delegate](http://api.rubyonrails.org/classes/Module.html#M000110) in rails doc.