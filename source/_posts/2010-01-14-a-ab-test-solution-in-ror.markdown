---
layout: post
title: an A/B test solution in ROR
categories:
- Tech Notes
tags:
- a/b-test
- EQenglish
- ielts
- landing-page
- ror
- routing
published: true
comments: true
---
<p>Last few days, I worked for a mission to add more flexible control to <a href="http://www.eqenglish.com">our website</a> landing pages. What I did is to add a "a/b" test feature for new landing pages, that means, if people have two designs and want to compare the results, they only release two versions of landing page, and then only get one url for the two versions of pages, after that the url will automatically redirect to different versions evenly, so that through Google analytics marketing people can easily decide which landing page is much better.</p>

<p><strong>Landing pages A/B test solution:</strong>
<code lang="ruby">
class LandingsController < ApplicationController<br />
  layout "layouts/blank"<br />
  caches_page "ielts","ab_test"</code></p>

<p>  def ielts<br />
    @landing_page = Landing.find_by_url_slug(params[:url_slug]) || Landing.valid_landings.first<br />
    if @landing_page.ab_test?<br />
      if not params[:channel].blank?<br />
        redirect_to landing_ab_test_with_channel_path(["a","b"].rand,params[:url_slug],params[:channel])<br />
      else<br />
        redirect_to landing_ab_test_path(["a","b"].rand,params[:url_slug])<br />
      end<br />
    else<br />
      render :layout => "layouts/landing_page"<br />
    end<br />
  end</p>

<p>  def ab_test<br />
    @landing_page = Landing.find_by_url_slug(params[:type].to_s + "/" + params[:url_slug].to_s)<br />
    (@landing_page = Landing.find_by_url_slug(params[:url_slug]) || Landing.valid_landings.first) if @landing_page.nil?<br />
    render :layout => "layouts/landing_page"<br />
  end<br />
end

<strong>Routing:</strong>
<code lang="ruby">
   map.landing_trunk "ielts/:url_slug", :controller => "landings", :action => "ielts"<br />
   map.landing_trunk_with_channel "ielts/:url_slug/:channel", :controller => "landings", :action => "ielts"<br />
   map.landing_ab_test "ielts/sub/:type/:url_slug/", :controller => "landings", :action => "ab_test"<br />
   map.landing_ab_test_with_channel "ielts/sub/:type/:url_slug/:channel", :controller => "landings", :action => "ab_test"
</code></p>

<p><strong>A/B test Sample:</strong>
<em>Suppose</em>:<br />
              We release a type of landing page called : university<br />
              And we have two kinds of different designs : called "a/university" and "b/university"<br />
              Then we may release the landing page to many universities, such as "beida", "renda", "qinghua" etc.. they are different channels.</p>

<p><em>Then we can</em>:<br />
             Only release the url as "http://www.eqenglish.com/ielts/university" to any universities by following "/beida", "/renda", "/qinghua" etc...<br />
             It should be like this "http://www.eqenglish.com/ielts/university/beida",  "http://www.eqenglish.com/ielts/university/renda"... etc.. (For client use)<br />
             But in google analytics, you will see : "http://www.eqenglish.com/ielts/sub/a/university/beida"<br />
                                                                  and : "http://www.eqenglish.com/ielts/sub/b/university/beida"  (For our analysis)</p>

<p> It means, different landing page and different channel and ("a" or "b") will be in a unique URL for certain purpose. but for our client, they don't need to care about "a/b" test, system will redirect pages automatically.</p>

<p>Any involving comments are welcomed.</p>
