---
layout: post
title: Install Eclipse Galileo for Django and Pinax - Part 1
excerpt: Part 1 of how to install a starter Django/Pinax project on a Mac.
wordpress_id: 193
wordpress_url: http://varud.com/?p=193
date: 2009-06-16 18:15:09.000000000 -04:00
---
Today I decided to see if I could do a proof of concept <a href="http://djangoproject.com">Django</a>/<a href="http://pinaxproject.com">Pinax</a> deployment for an anti-fraud advertising service.  Since they already use PHP for their legacy codebase and since the existing developer uses Eclipse and the <a href="http://zend.com/">Zend</a> Plugin for debugging, I decided to use Eclipse for the proof of concept (since I have to convince that person to switch to Django).

First things first.  Update your Mac to the latest and greatest software and JVM.  A new JVM literally came out today so that's what I did.  

Now, go download the bleeding edge release candidate Eclipse for Java EE Cocoa Version - <a href="http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/galileo/RC4/eclipse-jee-galileo-RC4-macosx-cocoa.tar.gz">Galileo</a>.  Some people will probably want something else, but I say that Cocoa apps are way nicer than Carbon ones and anyway, I went with Galileo.  The Java EE version has web development tools built in there which I thought would be important.  Feel free to comment below with a leaner way to do this - I'm not using Java.

Now, grab the new version of <a href="http://www.open.collab.net/downloads/community/">Subversion</a> (if you're using Subversion).  I got, and highly recommend, version 1.6.2.  I usually don't get the latest SVN packages but when trying 1.4.x it did not work.

Spin up Eclipse and grab some plugins.  You'll need the PyDev and Subclipse plugins.  Go to Help > Install New Software, and install these:

Get the 1.6 series of Subclipse here:
http://subclipse.tigris.org/update_1.6.x

PyDev for debugging and highlighting:
http://pydev.sourceforge.net/updates/

For Subclipse, you'll get alot of options.  Just install everything (again, I'm usually lean but I tried not installing everything and had issues - I would just do it all).

Now, run through the fantastic <a href="http://www.fabioz.com/pydev/manual_101_root.html">Getting Started</a> guide on the PyDev website.  It's written for Windows and a previous version, but you should be able to get through everything.

When you've gone through that, it's time to get your existing SVN project into the project you created for PyDev above.  Just right-click on the project and select 'Import'.  From there, choose SVN and import from your svn repository (if you have one - otherwise, skip this).

I will get to Pinax on the next post, when I figure it out :-) 

