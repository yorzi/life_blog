---
layout: post
title: Feed parser in Ruby
categories:
- Tech Notes
tags:
- feedparser
- feedzirra
- gem
- ruby
published: true
comments: true
---
<p><blockquote>There are a number of ways of parsing an RSS feed in Ruby, but one of the best is a gem called <a href="http://github.com/pauldix/feedzirra/tree/master">Feedzirra</a>. The main advantage of Feedzirra is its speed; it parses feeds very quickly, but it is also useful as it can parse many different types of feed.
</blockquote></p>

<p>To install Feedzirra we first need to make sure that <code>http://gems.github.com</code> is in our list of gem sources. If not we’ll need to add it.
<pre>gem sources -a http://gems.github.com</pre>
Now we can install the gem:
<pre>sudo gem install pauldix-feedzirra</pre>
<strong><em>Notice:</em></strong> When I was installing the gem, there are several libs needed, including <em>libcurl4-gnutls-dev libcurl3-gnutls libxslt1-dev</em>, you may not meet this issue, it's not a big deal, just install what it rely on. Several dependencies will also be installed alongside the gem. Once everything’s installed we’ll need to add a reference to the gem in our application’s <em>/config/environment.rb</em> file.
<pre>config.gem "pauldix-feedzirra", :lib =&gt; "feedzirra", :source =&gt; "http://gems.github.com"</pre>
That’s it. We’re ready to start parsing RSS feeds in our application.</p>

<p>Getting start:<br />
Assume that, you've got a model to store the feed content which is fetched by the parser, so the model should be like :
<pre name="code" class="ruby">
class FeedEntry < ActiveRecord::Base
  def self.update_from_feed(feed_url)
    feed = Feedzirra::Feed.fetch_and_parse(feed_url)
    add_entries(feed.entries)
  end</pre></p>

<p>  private<br />
  def self.add_entries(entries)<br />
    entries.each do |entry|<br />
      unless exists? :guid => entry.id<br />
        create!(<br />
          :name         => entry.title,<br />
          :summary      => entry.summary,<br />
          :url          => entry.url,<br />
          :published_at => entry.published,<br />
          :guid         => entry.id<br />
        )<br />
      end<br />
    end<br />
  end<br />
end

A more detailed manual is <a href="http://asciicasts.com/episodes/168-feed-parsing">here!</a></p>
