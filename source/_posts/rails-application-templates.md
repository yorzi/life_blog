title: Rails Application Templates
link: http://blog.wangyaodi.com/2009/12/11/rails-application-templates/
creator: yorzi
description: 
post_id: 162
post_date: 2009-12-11 14:28:03
post_date_gmt: 2009-12-11 06:28:03
comment_status: open
post_name: rails-application-templates
status: publish
post_type: post

# Rails Application Templates

When talking about templates in Rails, usually people mean the templates which help to re-use views, but this templates is a [feature after Rails 2.3 for generating Rails application](http://github.com/rails/rails/commit/e8cc4b116c460c524961a07da92da3f323854c15) easily, so give it a try if you haven't used it yet. It's helpful for me to create Rails application according to similar skeleton, a sample below was written about one year ago, but recently I want to create a new application with the same environment/configuration. ` #idapted_template.rb generate :rspec environment 'config.time_zone = "Beijing"' environment 'config.i18n.default_locale = :zh' name = ask("What's app's name?") file 'config/site_config.yml', <<-CODE app: #{name} domain: mydomain CODE user = ask("What's db user name?") pwd = ask("What's db user password?") file 'config/database.yml', <<-CODE development: adapter: mysql encoding: utf8 database: #{name}_development user: #{user} password: #{pwd} pool: 5 timeout: 5000 test: adapter: mysql encoding: utf8 database: #{name}_test user: #{user} password: #{pwd} pool: 5 timeout: 5000 production: adapter: mysql encoding: utf8 database: #{name}_production user: #{user} password: #{pwd} pool: 5 timeout: 5000 CODE rake 'db:create:all' rake 'db:sessions:create' rake 'db:migrate' gem 'idp_helpers' gem 'idp_core' run "rm public/index.html" run "rm -rf tmp log" run "svn import . http://mydomain.com/svn/projects/applications/#{name} -m 'add new app'" run "rm -rf *" run "svn checkout http://mydomain.com/svn/projects/applications/#{name} ." file 'ignore_list', <<-CODE log tmp nbproject CODE run "svn propset svn:ignore -F ignore_list ." run "rm ignore_list" run "svn commit -m 'set svn ignore'" ` There are several useful commands which help you write powerful templates, you can learn more good examples [here](http://m.onkey.org/2008/12/4/rails-templates). or watch Ryan's Railscasts about [App Templates in Rails 2.3](http://railscasts.com/episodes/148-app-templates-in-rails-2-3). Enjoy it.