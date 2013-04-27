title: 在ROR中执行定时任务
link: http://blog.wangyaodi.com/2009/11/13/%e5%9c%a8ror%e4%b8%ad%e6%89%a7%e8%a1%8c%e5%ae%9a%e6%97%b6%e4%bb%bb%e5%8a%a1/
creator: yorzi
description: 
post_id: 79
post_date: 2009-11-13 15:48:18
post_date_gmt: 2009-11-13 07:48:18
comment_status: open
post_name: %e5%9c%a8ror%e4%b8%ad%e6%89%a7%e8%a1%8c%e5%ae%9a%e6%97%b6%e4%bb%bb%e5%8a%a1
status: publish
post_type: post

# 在ROR中执行定时任务

目前最常用的方法是利用Unix自身的[cron](http://en.wikipedia.org/wiki/Cron)功能来实现定时任务，但是cron的语法比较麻烦(个人感觉)，今天为了执行一个定时任务发现了一个很好的RubyGem可以让你用Ruby的方式定义定时任务，这就是[Whenever](http://github.com/javan/whenever/tree/master)。 Whenever可以让你写出类似下面的定时任务： 
    
    
     set :cron_log, "/path/to/my/cron_log.log"
    
     every 2.hours do
       command "/usr/bin/some_great_command"
       runner "MyModel.some_method"
       rake "some:great:rake:task"
     end
    

赶快去Github看看文档和代码吧[http://github.com/javan/whenever](http://github.com/javan/whenever)