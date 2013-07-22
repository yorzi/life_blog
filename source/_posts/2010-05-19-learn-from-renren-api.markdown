---
layout: post
title: Learn From Renren API
categories:
- Study Records
- Tech Notes
tags:
- api
- cross-domain
- renren
- technoloy
published: true
comments: true
---
<p>Been working on Renren Connect application for a while, when talking about its API, I think every coin has two sides, so let's see its sides:</p>

<p>A(davantage) side :<br />
1. Configure cross domain file to resolve JS cross-domain issue between application domain and renren domain. Not sure if a similar solution can solve our ajax load cross domain-issue.. or meet our other future use. The file as below:
<code lang="html">
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>
<body>
<script src="http://static.connect.renren.com/js/v1.0/XdCommReceiver.jsp" type="text/javascript"></script>
</body>
</html>
</code></p>

<p>2. Learn from Renren "markable language", it's an clear way to capsule complex code block. It may help us to build standard function/display lib in future, I guess its a good way to reuse component among applications. sample is:
<code lang="html">
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xmlns:xn="http:///www.renren.com/2009/xnml">
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
  <title>Renren Connect</title>
</head>
<body>
  <xn:login-button autologoutlink="true"></xn:login-button>
  <script type="text/javascript" src="http://static.connect.renren.com/js/v1.0/FeatureLoader.jsp"></script>
  <script type="text/javascript">
    XN_RequireFeatures(["EXNML"], function()<br>
    {<br>
      XN.Main.init("16356ddc758343a39400837e79f1a18e", "/xd_receiver.html");<br>
    });
</script>
</body>
</html>
</code>
Above two technologies are a bit impressive to me, we may use it in future to organize our platform somehow.</p>

<p>D(isadvantage) side:<br />
1. I think the first "D", which is also bad, is the development document. It's partially out-of-date, that results in many stupid tries for their API. So we should learn the lesson and plan to write handful document in a clear way..</p>

<p>2. The second "D" is Renren doesn't have convenient sandbox for testing the third party application, we can't easily test or improve it when it's released, cause Renren only has one single configuration for each one application, that also means we have to take risk for further development which may change your application directly when it's released.</p>

<p>Summary:<br />
Great Technology + Clear Convenience = Comfortable Awesome</p>
