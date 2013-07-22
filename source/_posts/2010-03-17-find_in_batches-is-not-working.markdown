---
layout: post
title: find_in_batches is not working
categories:
- Tech Notes
tags:
- bug
- find_in_batches
- rails
- rake
published: true
comments: true
---
<p>Days ago, I came across a situation in which <a href="http://api.rubyonrails.org/classes/ActiveRecord/Batches/ClassMethods.html">find_in_batches</a> does not work correctly, the sample code is as below:
<code lang="ruby">
#NOT WORKING AS EXPECTED.<br />
namespace :studycenter do<br />
  desc 'generate item extra items'<br />
  task :update_extra_items => :environment do<br />
    puts "starting at #{@time = Time.now}......"<br />
    Item.find_in_batches(:conditions => {:content_type => "Scenario"}) do |items|<br />
      items.each do |item|<br />
        begin<br />
          if item.extra_items.blank?<br />
            item.related_lessons.each do |extra|<br />
              @item = ItemExtraItem.create({:item_id => item.id, :extra_item_id => extra.id})<br />
              puts "=============================================#{@item.id}"<br />
            end<br />
          end<br />
          puts "finished item with ID:#{item.id}"<br />
        rescue Exception => e<br />
          puts "something wrong happened!! item with ID:#{item.id}"<br />
          next<br />
        end<br />
      end<br />
      puts "------------------spent #{(Time.now - @time)/60} minutes!"<br />
    end<br />
    puts "finished at #{Time.now}, totally, spent #{(Time.now - @time)/60} minutes!"<br />
  end<br />
end
</code>
Then I refactor this task, so I can migrate data which generated day by day.
<code lang="ruby">
#WORKING WELL<br />
namespace :studycenter do<br />
  desc 'generate item extra items'<br />
  task :update_extra_items => :environment do<br />
    puts "starting at #{@time = Time.now}......"<br />
    (1..300).each do |n|<br />
      items = Item.all(:conditions => ["content_type = 'Scenario' and items.created_at >= ? and items.created_at < ?",("2010-03-13".to_date - n.days), ("2010-03-13".to_date - (n-1).days) ])<br />
      items.each do |item|<br />
        begin<br />
          if item.extra_items.blank?<br />
            item.related_lessons.each do |extra|<br />
              @item = ItemExtraItem.create({:item_id => item.id, :extra_item_id => extra.id})<br />
              puts "=============================================#{@item.id}"<br />
            end<br />
          end<br />
          puts "finished item with ID:#{item.id}"<br />
        rescue Exception => e<br />
          puts "something wrong happened!! item with ID:#{item.id}"<br />
          next<br />
        end<br />
      end<br />
      puts "------------------spent #{(Time.now - @time)/60} minutes!"<br />
    end<br />
    puts "finished at #{Time.now}, totally, spent #{(Time.now - @time)/60} minutes!"<br />
  end<br />
end
</code>
Do you know why find_in_batches is not working here?<br />
PS:  item.related_lessons is an item array, so the item and its related lesson are all the same class.</p>

<p><strong>Answer</strong>: In find_in_batches loop, the specific Class only has a range of its instances(e.g. 1~1000), so item.related_lessons can not find the item(e.g. 1001) out of the range..</p>
