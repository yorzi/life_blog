---
layout: post
title: Love named_scope
categories:
- Reading Marks
- Tech Notes
tags:
- named_scope
- rails
- refactor
- snippet
published: true
comments: true
---
<p>Rails Best Practice Snippet: About named_scope.<br />
Reference link to the PDF. <a rel="attachment wp-att-125" href="http://blog.wangyaodi.com/2009/11/26/law-of-demeter/rails-best-practices-2/">Rails-best-practices.</a></p>

<p>named_scope is a Rails 2.x feature which can simplify your rails code, move your finders into their own Model, and compact the code logically and gracefully. Below code refactoring is a named_scope sample to show the tricky.</p>

<p><strong>BEFORE</strong>
<code lang="ruby">
class PostController < ApplicationController<br />
  def search<br />
    conditions = { :title => "%#{params[:title]}%" } if params[:title]<br />
    conditions.merge!{ :content => "%#{params[:content]}%" } if params[:content]<br />
    case params[:order]<br />
      when "title" : order = "title desc"<br />
      when "created_at" : order = "created_at"<br />
    end<br />
    if params[:is_published]<br />
      conditions.merge!{ :is_published => true }<br />
    end<br />
    @posts = Post.find(:all, :conditions => conditions, :order => order,<br />
                             :limit => params[:limit])<br />
  end<br />
end
</code></p>

<p><strong>AFTER</strong>
<code lang="ruby">
class Post < ActiveRecord::Base<br />
  named_scope :matching, lambda { |column, value|<br />
    return {} if value.blank?<br />
    { :conditions => ["#{column} like ?", "%#{value}%"] }<br />
  }<br />
  named_scope :order, lambda { |order|<br />
  { :order => case order<br />
      when "title" : "title desc"<br />
      when "created_at" : "created_at"<br />
    end }<br />
  }<br />
end
</code>
<code lang="ruby">
class PostController < ApplicationController<br />
  def search<br />
    @posts = Post.matching(:title, params[:title])<br />
                 .matching(:content, params[:content])<br />
                 .order(params[:order])<br />
  end<br />
end
</code></p>

<p>More references :
<a href="http://ryandaigle.com/articles/2008/3/24/what-s-new-in-edge-rails-has-finder-functionality">http://ryandaigle.com/articles/2008/3/24/what-s-new-in-edge-rails-has-finder-functionality</a>
<a href="http://railscasts.com/episodes/108-named-scope">http://railscasts.com/episodes/108-named-scope</a></p>
