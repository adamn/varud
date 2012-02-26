---
layout: post
title: Version Control
wordpress_id: 132
wordpress_url: http://www.varud.com/?p=132
date: 2008-12-10 13:34:02.000000000 -05:00
---
I've burned way too many hours on version control over the past few months, I just wanted to write a short and sweet post to let people know what's going on.  First off, there are three valid options for version control these days:
<ul>
	<li><a href="http://git.or.cz/">Git</a> - Used by the Linux kernel at this point.  A super-flexible system for distributed development.  The one drawback to this system is that distributed development is built right into the system so that it is very difficult to get acquainted with for the casual developer.  I do not recommend this system unlesss the user is technical or the project already exists in Git.</li>
	<li><a href="http://subversion.tigris.org/">Subversion (svn)</a> - I've used svn for many years now.  It's a really fantastic system.  It is used by Google Code (version 1.4.0 btw) for all of their hosted open source projects.  I highly recommend this.  Version 1.5 is probably much better but for this particular type of software, I prefer to follow rather than lead.  I'll move to 1.5 when it's standard on Mac and Google.  Larger groups would benefit from going to 1.5 right now because of it's better merge handling.</li>
	<li><a href="http://www.selenic.com/mercurial/">Mercurial</a> - I didn't play around with Mercurial much but it looks fantastic.  It's especially good for Python developers because of the large Python/Mercurial community.  I would highly recommend this package for somebody who isn't already working with the other two - based simply on what I've read and community feedback.</li>
</ul>
The second large problem is hosting.  I tried to do my own hosting but it's a real pain in the #$@$.  At first, all is well.  Then, you have to do something weird (like delete and re-add a directory) and all of a sudden you're out on a limb - wasting time - not getting things done.  Here are the options:
<ul>
	<li><a href="http://github.com/">Github</a> - Github is hands down the best option for Git projects.  All the open source projects using Git are there and a small fee can be paid for private projects.</li>
	<li><a href="http://www.assembla.com/">Assembla</a> -  Lots of people recommend Assembla.  I haven't tried them but they look fine.</li>
	<li><a href="http://www.springloops.com/">SpringLoops</a> - This is a really great svn host.  I'm using them right now.  It's pay as you go which is a really good option (free for small projects).</li>
	<li><a href="http://www.svnhub.com">Svnhub</a> - This is Github for svn.  When this is live, I will definitely check it out.</li>
</ul>
None of these services are more than a few dollars a month - even with many users.  Don't waste your time hosting and also don't waste your time with a half-assed solution from someplace like Dreamhost.  These sites are more than just version control hosts, they also give administrative control, good workflow, project management hooks (to Lighthouse, etc...).

Lesson learned.
