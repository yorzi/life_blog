title: Love named_scope
link: http://blog.wangyaodi.com/2009/12/07/love-named_scope/
creator: yorzi
description: 
post_id: 144
post_date: 2009-12-07 11:32:47
post_date_gmt: 2009-12-07 03:32:47
comment_status: open
post_name: love-named_scope
status: publish
post_type: post

# Love named_scope

Rails Best Practice Snippet: About named_scope. Reference link to the PDF. [Rails-best-practices.](/2009/11/26/law-of-demeter/rails-best-practices-2/) named_scope is a Rails 2.x feature which can simplify your rails code, move your finders into their own Model, and compact the code logically and gracefully. Below code refactoring is a named_scope sample to show the tricky. **BEFORE** ` class PostController < ApplicationController def search conditions = { :title => "%#{params[:title]}%" } if params[:title] conditions.merge!{ :content => "%#{params[:content]}%" } if params[:content] case params[:order] when "title" : order = "title desc" when "created_at" : order = "created_at" end if params[:is_published] conditions.merge!{ :is_published => true } end @posts = Post.find(:all, :conditions => conditions, :order => order, :limit => params[:limit]) end end ` **AFTER** ` class Post < ActiveRecord::Base named_scope :matching, lambda { |column, value| return {} if value.blank? { :conditions => ["#{column} like ?", "%#{value}%"] } } named_scope :order, lambda { |order| { :order => case order when "title" : "title desc" when "created_at" : "created_at" end } } end ` ` class PostController < ApplicationController def search @posts = Post.matching(:title, params[:title]) .matching(:content, params[:content]) .order(params[:order]) end end ` More references : [http://ryandaigle.com/articles/2008/3/24/what-s-new-in-edge-rails-has-finder-functionality](http://ryandaigle.com/articles/2008/3/24/what-s-new-in-edge-rails-has-finder-functionality) [http://railscasts.com/episodes/108-named-scope](http://railscasts.com/episodes/108-named-scope)