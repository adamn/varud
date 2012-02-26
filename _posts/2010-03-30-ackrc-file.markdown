---
layout: post
title: ackrc file
wordpress_id: 233
wordpress_url: http://varud.com/?p=233
date: 2010-03-30 14:02:25.000000000 -04:00
---
Great tip, add this to your ~/.ackrc file for <a href="http://betterthangrep.com/">ack</a>:

--ignore-dir=migrations

Then, when you run <a href="http://github.com/protocool/ack-tmbundle">Ack in Project</a> from TextMate, you won't get hits on your migration directories - which typically aren't what you're looking for anyway.
