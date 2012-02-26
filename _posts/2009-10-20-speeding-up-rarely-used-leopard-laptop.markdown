---
layout: post
title: Speeding up rarely used Leopard laptop
wordpress_id: 216
wordpress_url: http://varud.com/?p=216
date: 2009-10-20 22:37:30.000000000 -04:00
---
I have an old G4 laptop that comes out sometimes when my <span style="text-decoration: line-through;">girlfriend</span> fiance is using the shiny new MacBook Air.  Unfortunately, every time I use it, the hard drive thrashes and the CPU goes to 90%.  This is not good when you're simply trying to read <a href="http://nytimes.com">nytimes.com</a>.

What you'll probably notice if you look at the activity monitor or the output of ps from the terminal is the locate command running.  This is trying to update the locate database - which makes running 'locate' from the command line faster and I'm presuming is the backend for Spotlight?

Just pop into the terminal and from /etc/periodic run:
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 80px; width: 1px; height: 1px; overflow-x: hidden; overflow-y: hidden;">sudo mv weekly/310.locate monthly/</div>
sudo mv /etc/periodic/weekly/310.locate /etc/periodic/monthly/
<div>Now, locate will only run monthly when you haven't opened it in a long time.  If you don't care about locate - you can also just delete the file entirely - if it's just a browser machine with no new files - it doesn't matter anyway.</div>
