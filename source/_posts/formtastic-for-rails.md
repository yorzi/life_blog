title: Formtastic for Rails
link: http://blog.wangyaodi.com/2009/12/22/formtastic-for-rails/
creator: yorzi
description: 
post_id: 229
post_date: 2009-12-22 16:29:30
post_date_gmt: 2009-12-22 08:29:30
comment_status: open
post_name: formtastic-for-rails
status: publish
post_type: post

# Formtastic for Rails

I've been working on EQ portal during these days, I wanna share a useful gem which I used, it is called [Formtastic](http://github.com/justinfrench/formtastic/tree/0.9.7). it's a nice way to create form via formtastic, so the finial form is something like: ` <% semantic_form_for @landing, :url=>admin_landings_path do |form| %> 

<% form.inputs do %> <%= form.input :title, :label => 'Title' %> <%= form.input :url_slug, :label => 'Url slug' %> <%= form.input :meta, :label => 'Meta' %> <%= form.input :content, :label => 'Content' %> <% end %> 

<%= form.buttons %>

<% end %> ` Then it will generate HTML like this: `

  1. Title*
  2. Url slug*
  3. Meta*
  4. Content*

  1. ` Also, it can be configured well in display style(not try yet), as well as working with this [validation plugin](http://github.com/redinger/validation_reflection) There is a more detailed Doc at: [http://rdoc.info/rdoc/justinfrench/formtastic/blob/35eadf9a0f3e30101993419c3dd3327fb2fdd0b6/Formtastic/SemanticFormBuilder.html](http://rdoc.info/rdoc/justinfrench/formtastic/blob/35eadf9a0f3e30101993419c3dd3327fb2fdd0b6/Formtastic/SemanticFormBuilder.html).  And samples at: [http://asciicasts.com/episodes/184-formtastic-part-1](http://asciicasts.com/episodes/184-formtastic-part-1) Enjoy it.
  *[*]: required