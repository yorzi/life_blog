title: memory
link: http://blog.wangyaodi.com/2008/03/14/memory/
creator: yorzi
description: 
post_id: 9992
post_date: 2008-03-14 00:00:00
post_date_gmt: 2008-03-13 16:00:00
comment_status: open
post_name: memory
status: publish
post_type: post

# memory

def fresh  
  Love.find(:all).delete  
end  
  
render => :fresh  
  
#reference-http://rubyonrails.org/