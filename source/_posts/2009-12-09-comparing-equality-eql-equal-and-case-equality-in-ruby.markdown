---
layout: post
title: Comparing Equality (==, eql?, equal?) and Case Equality (===) in Ruby
categories:
- Tech Notes
tags:
- ==
- ===
- case
- eql?
- ruby
published: true
comments: true
---
<p>In weekly code review, GL mentioned a weird issues :
<code lang="ruby">
def self.test(obj)<br />
    case obj.class<br />
    when Student, TrialPlan<br />
      puts "1"<br />
    when Call<br />
      puts "2"<br />
    else<br />
      puts "3"<br />
    end<br />
end
</code>
This doesn't behave as expected. When we run test(Student.first), it prints out "3"!</p>

<p>but this works fine.
<code lang="ruby">
def self.test(obj)<br />
    case obj.class.to_s<br />
    when "Student", "TrialPlan"<br />
      puts "1"<br />
    when "Call"<br />
      puts "2"<br />
    else<br />
      puts "3"<br />
    end<br />
end
</code></p>

<p>Then I searched around for explaining this, I found the <em>case statement</em> in Ruby is very different with what in other languages. Ruby implements the Case statement according to its special operator "===", which is not the same as "==".</p>

<p>what's difference? See below explainations:
<a href="http://www.skorks.com/2009/08/how-a-ruby-case-statement-works-and-what-you-can-do-with-it/">how-a-ruby-case-statement-works-and-what-you-can-do-with-it/</a>
<a href="http://blog.mustmodify.com/2008/11/ruby-case-statement-comparison-feature.html">ruby-case-statement-comparison-feature.html</a></p>
