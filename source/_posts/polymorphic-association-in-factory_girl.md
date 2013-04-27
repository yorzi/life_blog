title: Polymorphic association in factory_girl
link: http://blog.wangyaodi.com/2009/11/03/polymorphic-association-in-factory_girl/
creator: yorzi
description: 
post_id: 10300
post_date: 2009-11-03 15:40:39
post_date_gmt: 2009-11-03 07:40:39
comment_status: open
post_name: polymorphic-association-in-factory_girl
status: publish
post_type: post

# Polymorphic association in factory_girl

I tried factroy_girl yesterday to work with rspec framework, It's excellent way to support testing, however, the polymorphic association in factroy_girl almost defeated me. The factory definition in my code is as: 
    
    
    Factory.define :item do |i|
        i.status 0
        i.related_with_id 1
        i.association :unit
    end
    
    Factory.define :study_record do |sr|
        sr.association :content, :factory => :item
        sr.add_attribute :interaction_id
        sr.add_attribute :finished_at
    end
    

Then I did this: 
    
    
    
        @item = Factory(:item)
        @study_record = Factory(:study_record)
        @item.study_records << @study_record
    
    

But actually, this does not work to associate @study_record with @item, the problem is that @study_record.content is totally a new instance of Item rather than @item. It seems that "<<" doesn't work in this case. The right way to do so: 
    
    
    
         @item = Factory(:item)
        @study_record = Factory(:study_record, :content => @item)
    
    

Polymorphic association works, and it's better than the fixtures solution indeed.