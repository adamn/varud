---
layout: post
title: Cloud Computing
wordpress_id: 181
wordpress_url: http://www.varud.com/?p=181
date: 2009-03-16 19:19:06.000000000 -04:00
---
I have alot to do right now - so what better time than now to write about stuff that has nothing to do with anything.  Recently, <a href="http://www.feld.com/wp/archives/2009/03/cloud-computing-streak-marks.html">Brad Feld</a> and<a href="http://continuations.com/post/86941076/cloud-competition-is-great-for-startups"> Albert Wenger</a> have thrown themselves into the ring with comments about the future of 'the cloud' and whether it's ready for real usage.  It most definitely is ready.

First of all, let's just give everybody a little primer on what cloud computing is.  Cloud computing is very simple: it's a network of computers (cloud) that can be used by people or organizations to run software at a metered price.  In theory, the price could be free, but just like free electricity, it costs somebody something.

Why is this a big deal?  We had that in the 70s.  It's true, the whole point of VAX and UNIX systems was to allow multiple programs to run on the same physical infrastructure without interfering with everybody else.  The problem with those time sharing implementations is that they share many different high level resources.  In the olden days (and still), you had one root user who had ultimate control, and was trusted.  Now, everybody will say at this point, "Hmm, I understand, it's a trust issue."  There is most definitely a trust problem but that's not the root of it (no pun intended).  The problem is sharing.  Just like with little children, sharing precedes trust.

Do you know what's great about your desktop?  What's great is that you get to decide whether you want to install <a href="http://skitch.com/">Skitch</a> or not.  You get to decide if you like a solar system for your wallpaper.  You know what's not great about a shared system, you are constrained by having to share it with others who have different needs.  If you want Python 2.5.2 instead of Python 2.5.1, open a ticket with the owner of the system and wait. In the meantime, make your program work on Python 2.5.1 because you have to - and add a little bit more clutter to a cluttered world.

Cloud computing doesn't change the fundamentals of sharing a server, it just reduces the amount of stuff that is shared.  In a <a href="http://aws.amazon.com/ec2/">large system</a>, if you are a small user (i.e. not a top 1,000 site), you can basically pretend that the machine is infinite.  What you are sharing is simply the CPU, the memory, the hard drives, etc... However, you get minimum amounts of those things that nobody else can infringe upon, and which are commodities at this point.  Most importantly, you're not sharing anything for which there are many different options.  Somebody could in theory say, "I want to program for an ARM processor, but the cloud doesn't support that".  However, very few are doing large scale Internet deployments on something other than x86/SPARC using standard device architectures.  With the cloud, I simply don't have to share as much.

All the arguments against the cloud miss the point.  One has to view it in a real world context.  There are only a few alternatives to cloud computing.  One is to share it with other people the old fashioned way (see above).  Except for cost considerations, this is not a better option because other people are stepping on your turf.  The other option is to get a dedicated server.  The problem with the dedicated server is that you only have one of them.  There's no redundancy at the machine level.  If the network device goes, you're out of luck.  You're getting the gain of having your own system while giving up the economies of scale that go with sharing.

Cloud computing is about sharing what everybody agrees are standard (CPUs, Memory IO, etc..) while not having to share things like high level language libraries - for which many options may be necessary.
