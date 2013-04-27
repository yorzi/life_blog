title: primary_key and foreign_key in Rails association
link: http://blog.wangyaodi.com/2009/11/12/primary_key-and-foreign_key-in-rails-association/
creator: yorzi
description: 
post_id: 71
post_date: 2009-11-12 15:32:30
post_date_gmt: 2009-11-12 07:32:30
comment_status: open
post_name: primary_key-and-foreign_key-in-rails-association
status: publish
post_type: post

# primary_key and foreign_key in Rails association

The has_many and belongs_to association in Rails are with many optional parameters, they are actually the parameters for DB relationship, see more details by [clicking here](http://api.rubyonrails.org/classes/ActiveRecord/Associations/ClassMethods.html). As a reminder to myself, I misunderstood the primary_key an foreign_key conditions in association, it should be set in both sides in some case, for instance: 
    
    
    class Student < ActiveRecord::Base
      has_many :trial_lessons, :foreign_key => :user_id, :primary_key => :profile_id
    end
    

Above code will let you invoke the student.trial_lessons, but if you want to use trial_lesson.student, you have to define the association as below: 
    
    
    class TrialLesson < ActiveRecord::Base
      belongs_to :student, :primary_key => :profile_id, :foreign_key => :user_id
    end
    

> **Notice that**: you actually set the same :primary_key and :foreign_key in both sides, it's because the DB relationship between these two Model can be described the same way..(it's only a way for me to remember the rule)