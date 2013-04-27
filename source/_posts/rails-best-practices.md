title: Rails Best Practices
link: http://blog.wangyaodi.com/2009/11/09/rails-best-practices/
creator: yorzi
description: 
post_id: 43
post_date: 2009-11-09 11:26:03
post_date_gmt: 2009-11-09 03:26:03
comment_status: open
post_name: rails-best-practices
status: publish
post_type: post

# Rails Best Practices

Quote from Gary's weekly code review post, thanks to Gary Zhang. 

> all advises on Ruby on Rails code: * Lesson 1. Move code from Controller to Model 1. Move finder to named_scope 2. Use model association 3. Use scope access 4. Add model virtual attribute 5. Use model callback 6. Replace Complex Creation with Factory Method 7. Move Model Logic into the Model 8. model.collection_model_ids (many-to-many) 9. Nested Model Forms (one-to-one) 10. Nested Model Forms (one-to-many) * Lesson 2. RESTful Conventions 1. Overuse route customizations 2. Needless deep nesting 3. Not use default route * Lesson 3. Model 1. Keep Finders on Their Own Model 2. Love named_scope # same as Move finder to named_scope 3. the Law of Demeter 4. DRY: metaprogramming 5. Extract into Module 6. Extract to composed class 7. Use Observer * Lesson 4. Migration 1. Isolating Seed Data 2. Always add DB index * Lesson 5. Controller 1. Use before_filter 2. DRY Controller * Lesson 6. View 1. Move code into controller 2. Move code into model 3. Move code into helper 4. Replace instance variable with local variable 5. Use Form Builder 6. Organize Helper files I think all these advises are very useful for our farther refactor on our system. There is a very cool gem to check code according these advises(Sources : [Rails Best Practices](http://github.com/flyerhzm/rails_best_practices)) install: sudo gem install rails_best_practices --source http://gemcutter.org usage: in rails rails app, run "rails_best_practices ." (don't forget the parameter: ".") 

Not try this tool yet, but it looks really handy.