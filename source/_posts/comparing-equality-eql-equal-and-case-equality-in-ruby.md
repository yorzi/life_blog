title: Comparing Equality (==, eql?, equal?) and Case Equality (===) in Ruby
link: http://blog.wangyaodi.com/2009/12/09/comparing-equality-eql-equal-and-case-equality-in-ruby/
creator: yorzi
description: 
post_id: 159
post_date: 2009-12-09 13:46:26
post_date_gmt: 2009-12-09 05:46:26
comment_status: open
post_name: comparing-equality-eql-equal-and-case-equality-in-ruby
status: publish
post_type: post

# Comparing Equality (==, eql?, equal?) and Case Equality (===) in Ruby

In weekly code review, GL mentioned a weird issues : ` def self.test(obj) case obj.class when Student, TrialPlan puts "1" when Call puts "2" else puts "3" end end ` This doesn't behave as expected. When we run test(Student.first), it prints out "3"! but this works fine. ` def self.test(obj) case obj.class.to_s when "Student", "TrialPlan" puts "1" when "Call" puts "2" else puts "3" end end ` Then I searched around for explaining this, I found the _case statement_ in Ruby is very different with what in other languages. Ruby implements the Case statement according to its special operator "===", which is not the same as "==". what's difference? See below explainations: [how-a-ruby-case-statement-works-and-what-you-can-do-with-it/](http://www.skorks.com/2009/08/how-a-ruby-case-statement-works-and-what-you-can-do-with-it/) [ruby-case-statement-comparison-feature.html](http://blog.mustmodify.com/2008/11/ruby-case-statement-comparison-feature.html)