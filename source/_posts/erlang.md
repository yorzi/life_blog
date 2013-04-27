title: Erlang
link: http://blog.wangyaodi.com/2009/11/19/erlang/
creator: yorzi
description: 
post_id: 103
post_date: 2009-11-19 10:19:29
post_date_gmt: 2009-11-19 02:19:29
comment_status: open
post_name: erlang
status: publish
post_type: post

# Erlang

本篇是完全转载的一篇文章，[7哥](http://www.dujingfang.com)昨天利用这个例子给team讲了一下erlang，在这里做个备份，免得以后要用时候找不到了。[原文链接](http://erlang-china.org/start/mochiweb_intro.html) ------------------------------------------------------------------------------------------------------------------------------ [MochiWeb](http://code.google.com/p/mochiweb)是[mochibot.com](http://www.mochibot.com/)的[Bob Ippolito](http://bob.pythonmac.org/)贡献的开源项目[在[这里](http://undefined.org/c4-1/)有一个介绍它的Slide]。 MochiBot.com 提供 Flash 内容的访问统计和用户跟踪服务（大致上，可以理解为针对 flash 的 google Analytics 服务），他们在 mochiweb 之上构建了一个定制化的 web server ，并通过这个 web server 获取用户的访问数据（在这一点上有点象 [Erlana](http://code.google.com/p/erlana/) 项目）。可以想象，这个定制的 web server 需要很高的并发支持，精简和牢固的底层架构，以及对于 http 协议的完备支持（乃至对于 socket 的直接操控）。如果可以的话，最好还有更为精简的 API ，易于定制的 URL 扩展方式，以及易于理解的底层框架。幸运的是，这些 mochiweb 都已经提供，而且还是开源的。 需要说明的是，相比 yaws / inets httpd 而言，它的目标并不是 apache 之类的软件，它并不是一个完整的 web server （没有cache等机制，因而也不做任何加速动作），它只是一个实现 web server 的工具包（这也就意味着，它直接通过代码来扩展，你可以在它的基础上做任何事）。正因为此，在“需要定制 Web Server”的情况下，它成为一个非常不错的选择（比如，配置在 enginx 的后面，专门用于动态内容的生成）。在 erlang 的世界里，有几个项目已经开始转而使用 mochiweb 。 下面是对这个项目代码的一些粗浅实战。 首先遵循它的提示，通过svn获取代码： 

svn checkout http://mochiweb.googlecode.com/svn/trunk/ mochiweb-read-only

获得的文件和目录结构如下： 

deps  ebin     LICENSE   priv    scripts  support doc   include  Makefile  README  src

注：大写字母开头的是文件，小写字母开头的是目录。这是一个相当标准的 Erlang 项目目录结构，其 Makefile （用到 support 目录的 make 包含文件）非常值得借鉴（而且也有简化这一借鉴步骤的办法，后面会提到）。 这是一个纯粹的 Erlang 项目，并不涉及其它语言写的模块，照老规矩，直接 make ： 

make

注：如果你和我一样，仍在 R11* 上工作，那么 make 会在 edoc 的步骤中失败，这是因为 R11* 的 edoc 工具存在 bug 无法正确处理 mochiweb 用到的[ Parameterized module 语法](http://erlang-china.org/study/parameterized-module.html)，不用管它，并不影响后续使用。 make 完成之后，要怎么试运行呢？这就涉及我们上面提到的“借鉴”工作。因为 mochiweb 是设计用来作为一个完整项目的一个基础部分，也就是说，它只是一个骨架（或者如作者所说的toolkit），在你 make 完之后，什么也干不了，除非你对它进行定制化编码，完成这个 web server 。好在它自己已经提供了工具来简化这一步骤： 

escript scripts/new_mochiweb.erl test

new_mochiweb.erl 是一个 EScript 脚本，它负责从 mochiweb 中拷贝使用 mochiweb 所必须文件和目录，形成你的新项目的“骨架”（概念上有点类似于 rails 的自动生成代码）。上面的命令生成了名为 test 的项目，会在当前目录建立名为 test 子目录（还可以使用 escript scripts/new_mochiweb.erl test testdir 将新建立的项目放在 testdir 目录中）。上面的命令生成了一些文件，我加了注释： 

./test/ 项目目录 Makefile Make文件 start.sh 启动脚本 start-dev.sh 开发模式下的启动脚本（开启代码重载机制） ./test/ebin/ 编译目录 ./test/support/ Make支持文件目录 include.mk Make包含脚本 ./test/deps/ 依赖目录，包含mochiweb自身 ./test/src/ 代码目录 skel.app 实际名称为test.app，OTP规范的应用定义文件 Makefile Make文件 skel_web.erl 实际名称为test_web.erl，应用的web服务器代码 skel_deps.erl 实际名称为test_deps.erl，负责加载deps目录的代码 skel_sup.erl 实际名称为test_sup.erl，OTP规范的监控树 skel.hrl 实际名称为test.hrl，应用的头文件 skel_app.erl 实际名称为test_app.erl，OTP规范的应用启动文件 skel.erl 实际名称为test.erl，应用的API定义文件 ./test/doc/ 文档目录 ./test/include/ 包含文件目录 ./test/priv/ 项目附加目录 ./test/priv/www/ 项目附加的www目录 index.html 默认的项目首页

是的，什么也不用改，在新生成的项目骨架中，一个可用的web服务器已经就绪： 

make ./start-dev.sh

这会打开一个 erlang shell ，输出的信息表明在 8000 端口开了一个 web 服务，此时用浏览器访问 http://localhost:8000 （或者其它正确的地址）就能看到“MochiWeb running.”，这表明 mochiweb 配置正确，运行良好。注意，我们上面是用 start-dev.sh 来启动的，它打开了 reloader 特性。 现在修改一下 test_web.erl 的代码，加点料。因为我们上面已经打开了 reloader 所以，不用关掉这个 erlang shell ，我们可以直接修改和编译，然后刷新就能看到效果（有点 PHP 编程的意思了）。把 test_web.erl 改成这样，看看会有什么情况发生： 

下载: [test_web.erl](http://erlang-china.org/wordpress/wp-content/plugins/coolcode/coolcode.php?p=151&download=test_web.erl)

  1. %% @author author <author@example.com>
  2. %% @copyright YYYY author.
  3.   4. %% @doc Web server for test.
  5.   6. -module(test_web).
  7. -author('author <author@example.com>').
  8.   9. -export([start/1, stop/0, loop/2]).
  10.   11. %% External API
  12.   13. start(Options) ->