---
layout: post
title: Reverse Generic Relations
wordpress_id: 177
wordpress_url: http://www.varud.com/?p=177
date: 2009-03-06 17:11:33.000000000 -05:00
---
First off, apologies for not posting in some time.  I've been spending the past week exploring a couple of different technologies - here's a short summary:
<ul>
	<li>Amazon ec2 - I know I've talked about this before but these guys are way ahead of the game.  I'm not deep enough in the field to confirm where the other players are (Google App Engine, etc...), but I'm continually impressed by ec2.  Cloud computing really is the future.  I can only think of a handful of projects for which I would not deploy a cloud computing infrastructure (internal file server I suppose).  All new Internet applications should be placed on a cloud system.</li>
	<li>PHP - I'm sorry to say this, but I'm short on PHP.  I really don't know if there's a future for it.  Maybe some of the frameworks (Zend, Cake) can save it - I'm not sure.  One thing I know is that I'm leaving PHP behind.</li>
	<li>On the vein of PHP, which BTW is a solid OO language now, I want to be clear about the power of OO web frameworks .... like Django, that they are critical to future development.</li>
	<li>Rails documentation is really bad.  Try to figure out what I'm about to tell you with Django in a Rails way - I dare you [Comments section open]</li>
</ul>
Django has something called <a href="http://docs.djangoproject.com/en/dev/ref/contrib/contenttypes">ContentTypes</a> which allow for the creation of models that can generically relate to many other objects.  A straightforward example would be a tagging system.  Tags can be placed on blog post, a page, a person, a group, etc...  When creating the Tag model, you could think ahead about all the possible applications of a given tag, but that would be crazy.  Why not just use a standard ContentType relation to handle it - in other words a relation to any other model that works as you create it.  That's the power of this object.  In the database table, it uses two columns: one is the id of the Content Type itself (User, Bookmark, Tag, etc..), the other is the id of the object (The id of the user, the bookmark, the tag, etc...).  Because the system is smart though, it's all available abstractly.

But wait, it doesn't stop there.  If you do want make life even easier for a model like a Bookmark, so that you can get the tags for it, you can use their <a href="http://docs.djangoproject.com/en/dev/ref/contrib/contenttypes/#reverse-generic-relations">Reverse Generic Relations</a> to give you object oriented access to all the children of a given parent (all the tags of a given bookmark).  And, for each of those children, you can find their children (i.e. all the votes for a given bookmark a la Digg).  All this is object oriented and requires zero SQL.

Kudos to the Django team for creating such a great abstraction - but also for documenting it so well.  I am now a Django evangelist.
