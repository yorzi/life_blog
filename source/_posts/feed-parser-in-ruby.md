title: Feed parser in Ruby
link: http://blog.wangyaodi.com/2009/11/13/feed-parser-in-ruby/
creator: yorzi
description: 
post_id: 73
post_date: 2009-11-13 15:28:53
post_date_gmt: 2009-11-13 07:28:53
comment_status: open
post_name: feed-parser-in-ruby
status: publish
post_type: post

# Feed parser in Ruby

> There are a number of ways of parsing an RSS feed in Ruby, but one of the best is a gem called [Feedzirra](http://github.com/pauldix/feedzirra/tree/master). The main advantage of Feedzirra is its speed; it parses feeds very quickly, but it is also useful as it can parse many different types of feed. 

To install Feedzirra we first need to make sure that `http://gems.github.com` is in our list of gem sources. If not we’ll need to add it. 
    
    gem sources -a http://gems.github.com

Now we can install the gem: 
    
    sudo gem install pauldix-feedzirra

**_Notice:_** When I was installing the gem, there are several libs needed, including _libcurl4-gnutls-dev libcurl3-gnutls libxslt1-dev_, you may not meet this issue, it's not a big deal, just install what it rely on. Several dependencies will also be installed alongside the gem. Once everything’s installed we’ll need to add a reference to the gem in our application’s _/config/environment.rb_ file. 
    
    config.gem "pauldix-feedzirra", :lib => "feedzirra", :source => "http://gems.github.com"

That’s it. We’re ready to start parsing RSS feeds in our application. Getting start: Assume that, you've got a model to store the feed content which is fetched by the parser, so the model should be like : 
    
    
    class FeedEntry < ActiveRecord::Base
      def self.update_from_feed(feed_url)
        feed = Feedzirra::Feed.fetch_and_parse(feed_url)
        add_entries(feed.entries)
      end
    
      private
      def self.add_entries(entries)
        entries.each do |entry|
          unless exists? :guid => entry.id
            create!(
              :name         => entry.title,
              :summary      => entry.summary,
              :url          => entry.url,
              :published_at => entry.published,
              :guid         => entry.id
            )
          end
        end
      end
    end
    

A more detailed manual is [here!](http://asciicasts.com/episodes/168-feed-parsing)