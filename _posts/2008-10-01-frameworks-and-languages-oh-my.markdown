---
layout: post
title: Frameworks and languages, oh my
wordpress_id: 57
wordpress_url: http://www.varud.com/?p=63
date: 2008-10-01 18:34:01.000000000 -04:00
---
Recently, I've begun the painful process of actually deciding what core languages and frameworks will be used for the application.Â  Some things are kind of obvious for everybody, and leads to my favorite phrase from my days of studying for the SAT - PoE (Process of Elimination).

One dimension to start eliminating on is the breadth of the network supporting that technology over the coming 2-3 years.Â  Perl is a language that is great, rock solid, and also drifting into obsolesence.Â  I feel bad for Perl but what are you going to do?Â  This also leaves out old versions of languages like PHP 4.

Another issue is licensing and money.Â  That cuts out Microsoft products right off the bat as well as some of the supported platforms like WebSphere.Â  I haven't been a Microsoft guy for years although they're still the only game in town for word processing and spreadsheets.

At this point, there are some things that just go along with what I've done before.Â  I'll most certainly use a Linux flavor for the OS - either Ubuntu (which I've never used in production) or CentOS (which is the same as Red Hat but is free).Â  After having some frustrating days trying to deal with a font installation problem (of all things) on an Ubuntu server, I'm starting to consider CentOS.Â  Either way, it's not much of a difference, either will do.

This operating system needs to be on a machine of some sort.Â  I don't want to buy a machine and grow out of it though - I'd prefer to rent.Â  That leads to a slew of hosting options.Â  One of the big guys is Dreamhost.Â  I've worked with them on some minor projects and they're great in alot of ways.Â  However, I need full control, root access, the ability to create an entirely new instance, etc...Â  Dreamhost won't do.Â  It's time to take advantage of the cloud so I've been experimenting with Amazon Web Services Elastic Compute Cloud (AWS ec2) and Simple Storage Service (S3).Â  For about $72/month, I can have a dedicated 'server' on a premium network (Amazon's) with access to S3 which allows for such things as snapshots (backups) and getting data into a solid storage space.

This post will have to be continued - I can't nearly finish this work so quickly.Â  Does anybody have thoughts?Â  Here's the current plan:
<ul>
	<li>Amazon Web Services ec2,S3, etc...</li>
	<li>Linux (Ubuntu or CentOS)</li>
	<li>Apache (I hadn't really thought about anything else, possibly lighttpd)</li>
	<li>Python or Ruby (PHP feels passe and there's really no other option)</li>
	<li>If Python, Django or Turbogears (probably Django because Google App Engine is using that)</li>
	<li>If Ruby, Rails or Merb</li>
</ul>
I could still be convinced on alot of fronts - this is hard :-)
