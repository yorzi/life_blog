---
layout: post
title: mysql dump
categories:
- Tech Notes
tags:
- bz2
- dump
- mysql
- script
- tech
published: true
comments: true
---
<p>I'm a little shamed that I ask Sonic for a mysql dump command several times, I rarely dump db myself, that's why I forget the way dealing with it.. Ok, the commands are:
<pre name="code" class="mysql">
mysqldump -u root user_production > user_production.sql
bzip2 user_production.sql</pre></p>

<p>scp from server to local.</p>

<p>bunzip2 user_production.sql.bz2<br />
bzcat user_production.sql.bz2 | mysql -u root user_production<br />
or extracts the backup files, to create db directly.
</p>

<p>Thanks Sonic.</p>
