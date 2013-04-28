---
layout: post
title: Polymorphic association in factory_girl
categories:
- Tech Notes
tags:
- factory girl
- polymorphic
- ruby
- testing
- work
published: true
comments: true
---
<p>I tried factroy_girl yesterday to work with rspec framework, It's excellent way to support testing, however, the polymorphic association in factroy_girl almost defeated me.<br />
The factory definition in my code is as:
<pre name="code" class="ruby">
Factory.define :item do |i|
    i.status 0
    i.related_with_id 1
    i.association :unit
end</pre></p>

<p>Factory.define :study_record do |sr|<br />
    sr.association :content, :factory => :item<br />
    sr.add_attribute :interaction_id<br />
    sr.add_attribute :finished_at<br />
end

Then I did this:
<pre name="code" class="ruby" /></p>

<p>    @item = Factory(:item)<br />
    @study_record = Factory(:study_record)<br />
    @item.study_records << @study_record</p>

<p>
But actually, this does not work to associate @study_record with @item, the problem is that @study_record.content is totally a new instance of Item rather than @item. It seems that "<<" doesn't work in this case.<br />
The right way to do so:
<pre name="code" class="ruby" /></p>

<p>     @item = Factory(:item)<br />
    @study_record = Factory(:study_record, :content => @item)</p>

<p>
Polymorphic association works, and it's better than the fixtures solution indeed.</p>
