title: bowline
link: http://blog.wangyaodi.com/2010/06/16/bowline/
creator: yorzi
description: 
post_id: 518
post_date: 2010-06-16 15:22:16
post_date_gmt: 2010-06-16 07:22:16
comment_status: open
post_name: bowline
status: publish
post_type: post

# bowline

> Bowline is a framework for making cross platform desktop applications in Ruby, HTML and JavaScript. If you've ever wished creating a desktop application was as simple as creating a Rails website, Bowline's for you. Bowline respects MVC, you can design your views in HTML5/CSS3 - then bind them to your Ruby models. There's no request/response cycle - any changes in models automatically get reflected in the view.

**See : [http://bowlineapp.com/](http://bowlineapp.com/)**

Experiment on this framework: **Requirements:** * Mac OSX >=10.5 or Ubuntu -----> [I am on Ubuntu 9.04] * Ruby 1.9 -----------------------------> [I use [RVM](http://rvm.beginrescueend.com/) to switch ruby between different version] * Bowline gem -----------------------> sudo gem install [bowline](http://github.com/maccman/bowline) **RVM** * [Install RVM](http://rvm.beginrescueend.com/rvm/install/) to manage Ruby easily, then you decide which version you will use. OK, Now create an application in an easy way: _>> bowline-gen app helloworld >> cd helloworld >> bowline-bundle >> ./script/run_ Unluckily, On Ubuntu 9.0.4, There is an error about a needed lib when I run the application, see _/usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /home/andy/.bowline/bowline-desktop)_ I searched around and found it's something wrong with gcc version, or these is still a webkit lib involved issue under Ubuntu9.0.4, anyway, it's interesting to me, I am now wondering if we can reference some bowline experience to create iphone/ipad application based on ruby on rails. not sure, I am researching in advance.