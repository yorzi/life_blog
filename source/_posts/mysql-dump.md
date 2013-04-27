title: mysql dump
link: http://blog.wangyaodi.com/2009/11/06/mysql-dump/
creator: yorzi
description: 
post_id: 30
post_date: 2009-11-06 11:42:45
post_date_gmt: 2009-11-06 03:42:45
comment_status: open
post_name: mysql-dump
status: publish
post_type: post

# mysql dump

I'm a little shamed that I ask Sonic for a mysql dump command several times, I rarely dump db myself, that's why I forget the way dealing with it.. Ok, the commands are: 
    
    
    mysqldump -u root user_production > user_production.sql
    bzip2 user_production.sql
    
    scp from server to local.
    
    bunzip2 user_production.sql.bz2
    bzcat user_production.sql.bz2 | mysql -u root user_production
    or extracts the backup files, to create db directly.
    

Thanks Sonic.

## Comments

**[sasa](#255 "2009-11-07 10:18:07"):** sql是啥？ 今天很流畅，应该不是IE的事，IE我基本没在用了：）

**[sasa](#256 "2009-11-07 10:27:03"):** 刚才收拾东西 翻出来我们小学初中高中还有大学的照片了!aha 发现 每长大几岁的照片都有浓重的儿时印记..

**[Andy Wang](#257 "2009-11-07 12:06:53"):** 哈，不好意思，一开始comment没有设置自动显示～ MYSQL是数据库，程序员就知道怎么回事

