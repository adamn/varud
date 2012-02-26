---
layout: post
title: Custom Fields on South 0.7
wordpress_id: 237
wordpress_url: http://varud.com/?p=237
date: 2010-03-30 14:25:12.000000000 -04:00
---
If you've upgraded to <a href="http://south.aeracode.org/">South</a> 0.7, you'll notice that <a href="http://docs.djangoproject.com/en/dev/howto/custom-model-fields/">custom model fields</a> are no longer supported.  There's a long, convoluted, discussion about supporting custom fields with <a href="http://south.aeracode.org/docs/customfields.html#extending-introspection">introspection rules</a>, but that's unnecessary for most custom fields.  If you're just extending a standard field like CharField, follow their <a href="http://south.aeracode.org/docs/tutorial/part4.html#tutorial-part-4">tutorial</a> example.  Import:

<code>from south.modelsinspector import add_introspection_rules
</code>

in your fields.py file (which should be holding the custom field MyCustomField, in my case in the util app).  Then, at the bottom, under your field definition, put:

<code>add_introspection_rules([], ["^util\.fields\.MyCustomField"])</code>
