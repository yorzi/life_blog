title: Learn From Renren API
link: http://blog.wangyaodi.com/2010/05/19/learn-from-renren-api/
creator: yorzi
description: 
post_id: 484
post_date: 2010-05-19 11:03:10
post_date_gmt: 2010-05-19 03:03:10
comment_status: open
post_name: learn-from-renren-api
status: publish
post_type: post

# Learn From Renren API

Been working on Renren Connect application for a while, when talking about its API, I think every coin has two sides, so let's see its sides: A(davantage) side : 1. Configure cross domain file to resolve JS cross-domain issue between application domain and renren domain. Not sure if a similar solution can solve our ajax load cross domain-issue.. or meet our other future use. The file as below: ` ` 2. Learn from Renren "markable language", it's an clear way to capsule complex code block. It may help us to build standard function/display lib in future, I guess its a good way to reuse component among applications. sample is: ` ` Above two technologies are a bit impressive to me, we may use it in future to organize our platform somehow. D(isadvantage) side: 1. I think the first "D", which is also bad, is the development document. It's partially out-of-date, that results in many stupid tries for their API. So we should learn the lesson and plan to write handful document in a clear way.. 2. The second "D" is Renren doesn't have convenient sandbox for testing the third party application, we can't easily test or improve it when it's released, cause Renren only has one single configuration for each one application, that also means we have to take risk for further development which may change your application directly when it's released. Summary: Great Technology + Clear Convenience = Comfortable Awesome