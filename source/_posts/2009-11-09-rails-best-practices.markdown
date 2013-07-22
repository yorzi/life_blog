---
layout: post
title: Rails Best Practices
categories:
- Tech Notes
tags:
- coding
- gem
- rails
- ruby
- test
published: true
comments: true
---
<p>Quote from Gary's weekly code review post, thanks to Gary Zhang.
<blockquote>
all advises on Ruby on Rails code:</blockquote></p>

<p>    * Lesson 1. Move code from Controller to Model<br />
      1. Move finder to named_scope<br />
      2. Use model association<br />
      3. Use scope access<br />
      4. Add model virtual attribute<br />
      5. Use model callback<br />
      6. Replace Complex Creation with Factory Method<br />
      7. Move Model Logic into the Model<br />
      8. model.collection_model_ids (many-to-many)<br />
      9. Nested Model Forms (one-to-one)<br />
      10. Nested Model Forms (one-to-many)</p>

<p>    * Lesson 2. RESTful Conventions<br />
      1. Overuse route customizations<br />
      2. Needless deep nesting<br />
      3. Not use default route</p>

<p>    * Lesson 3. Model<br />
      1. Keep Finders on Their Own Model<br />
      2. Love named_scope # same as Move finder to named_scope<br />
      3. the Law of Demeter<br />
      4. DRY: metaprogramming<br />
      5. Extract into Module<br />
      6. Extract to composed class<br />
      7. Use Observer</p>

<p>    * Lesson 4. Migration<br />
      1. Isolating Seed Data<br />
      2. Always add DB index</p>

<p>    * Lesson 5. Controller<br />
      1. Use before_filter<br />
      2. DRY Controller</p>

<p>    * Lesson 6. View<br />
      1. Move code into controller<br />
      2. Move code into model<br />
      3. Move code into helper<br />
      4. Replace instance variable with local variable<br />
      5. Use Form Builder<br />
      6. Organize Helper files</p>

<p>I think all these advises are very useful for our farther refactor on our system.</p>

<p>There is a very cool gem to check code according these advises(Sources : <a href="http://github.com/flyerhzm/rails_best_practices">Rails Best Practices</a>)</p>

<p>install:<br />
sudo gem install rails_best_practices --source http://gemcutter.org</p>

<p>usage:<br />
in rails rails app, run "rails_best_practices ." (don't forget the parameter: ".")
</p>

<p>Not try this tool yet, but it looks really handy.</p>
