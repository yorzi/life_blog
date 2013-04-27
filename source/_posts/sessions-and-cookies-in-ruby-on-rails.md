title: Sessions and Cookies in Ruby on Rails
link: http://blog.wangyaodi.com/2009/12/22/sessions-and-cookies-in-ruby-on-rails/
creator: yorzi
description: 
post_id: 225
post_date: 2009-12-22 12:02:24
post_date_gmt: 2009-12-22 04:02:24
comment_status: open
post_name: sessions-and-cookies-in-ruby-on-rails
status: publish
post_type: post

# Sessions and Cookies in Ruby on Rails

1. 最近读了一篇文章，里面介绍了Session和Cookie在RoR开发中的使用方法，英文还不错的同学请[直接读这篇文章](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#scinrails)。我仅仅在这篇Post里面做个整理，把那些有用的资料在此备份，免得下回又的麻烦Google。上面提到的文章很全面的介绍了很多细节，目录如下： 
    1. [**Introduction**](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#sintro)
    2. [**Sessions**](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#ssessions)
      1. [Session in rails](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#sinrails)
      2. [Configure your sessions](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#sconfig)
      3. [Storage options](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#sstorage)
      4. [Session storage limitations](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#slimitations)
      5. [Session and Security](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#ssecurity)
      6. [HowTo](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#showto)
        1. [Implement session expiration](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#sexpire)
        2. [Delete stale sessions](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#sstale)
        3. [Find out active users](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#sactive)
        4. [Access session data using session_id](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#ssessionid)
      7. [Miscellaneous](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#smisc)
    3. [**Cookies**](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#scookies)
      1. [Cookie on rails](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#scinrails)
      2. [cookies vs. request.cookies](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#scvr)
      3. [CookieJar](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#scookiejar)
      4. [Miscellaneous](http://www.quarkruby.com/2007/10/21/sessions-and-cookies-in-ruby-on-rails#scmisc)