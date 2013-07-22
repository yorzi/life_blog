---
layout: post
title: Rails Application Templates
categories:
- Tech Notes
tags:
- rails
- templates
published: true
comments: true
---
<p>When talking about templates in Rails, usually people mean the templates which help to re-use views, but this templates is a <a href="http://github.com/rails/rails/commit/e8cc4b116c460c524961a07da92da3f323854c15">feature after Rails 2.3 for generating Rails application</a> easily, so give it a try if you haven't used it yet.</p>

<p>It's helpful for me to create Rails application according to similar skeleton, a sample below was written about one year ago, but recently I want to create a new application with the same environment/configuration.</p>

<p><code lang="ruby">
#idapted_template.rb<br />
generate :rspec</code></p>

<p>environment 'config.time_zone = "Beijing"'<br />
environment 'config.i18n.default_locale = :zh'</p>

<p>name = ask("What's app's name?")<br />
file 'config/site_config.yml', <<-CODE<br />
app: #{name}<br />
domain: mydomain<br />
CODE</p>

<p>user = ask("What's db user name?")<br />
pwd = ask("What's db user password?")<br />
file 'config/database.yml', <<-CODE<br />
development:<br />
  adapter: mysql<br />
  encoding: utf8<br />
  database: #{name}_development<br />
  user: #{user}<br />
  password: #{pwd}<br />
  pool: 5<br />
  timeout: 5000</p>

<p>test:<br />
  adapter: mysql<br />
  encoding: utf8<br />
  database: #{name}_test<br />
  user: #{user}<br />
  password: #{pwd}<br />
  pool: 5<br />
  timeout: 5000</p>

<p>production:<br />
  adapter: mysql<br />
  encoding: utf8<br />
  database: #{name}_production<br />
  user: #{user}<br />
  password: #{pwd}<br />
  pool: 5<br />
  timeout: 5000<br />
CODE</p>

<p>rake 'db:create:all'<br />
rake 'db:sessions:create'<br />
rake 'db:migrate'</p>

<p>gem 'idp_helpers'<br />
gem 'idp_core'</p>

<p>run "rm public/index.html"</p>

<p>run "rm -rf tmp log"<br />
run "svn import . http://mydomain.com/svn/projects/applications/#{name} -m 'add new app'"<br />
run "rm -rf *"<br />
run "svn checkout http://mydomain.com/svn/projects/applications/#{name} ."</p>

<p>file 'ignore_list', <<-CODE<br />
log<br />
tmp<br />
nbproject<br />
CODE<br />
run "svn propset svn:ignore -F ignore_list ."<br />
run "rm ignore_list"<br />
run "svn commit -m 'set svn ignore'"
</p>

<p>There are several useful commands which help you write powerful templates, you can learn more good examples <a href="http://m.onkey.org/2008/12/4/rails-templates">here</a>. or watch Ryan's Railscasts about <a href="http://railscasts.com/episodes/148-app-templates-in-rails-2-3">App Templates in Rails 2.3</a>.</p>

<p>Enjoy it.</p>
