---
layout: post
title: Django 1.2 Alpha - Template Threading
excerpt: Notes about threading and template caching in Django 1.2
wordpress_id: 221
wordpress_url: http://varud.com/?p=221
date: 2010-01-13 18:35:02.000000000 -05:00
---
Django 1.2 Alpha 1 was recently <a href="http://docs.djangoproject.com/en/dev/releases/1.2-alpha-1/">released</a> to developers worldwide.  I haven't been able to play around with it yet but I am reading through the announced changes and plan to write a series of articles for people making the leap from 1.1 to 1.2 - since that's what I'll be doing this Spring.

First of all, this is a giant release.  I don't expect it to go smoothly and I can pretty much guarantee that some major third-party packages will be broken even when Django 1.2 is released as stable.  One of the major changes is that template node bytecode will now be <a href="http://docs.djangoproject.com/en/dev/ref/templates/api/#template-loaders">cached</a> in memory (I think - at least that's how I understand it).  Most people will say, 'cached is faster than not cached ... this is great'.

Unfortunately, what this really means is that the web server will cache the code and run it across all the threads that share that process memory pool.  Now, imagine you are on a default Apache installation on a <a href="http://www.ubuntu.com/products/whatisubuntu/serveredition">modern OS</a>.  These days, that Apache will be running in a multithreaded configuration.  That means that each thread (end user) will hit that bytecode in a shared fashion.  If you (or a third party developer) have written any custom template tags, this can be a problem.

Thankfully, the fantastic Django docs <a href="http://docs.djangoproject.com/en/dev/howto/custom-template-tags/#template-tag-thread-safety">point this out</a> and explain why this matters.  For the lazy, I'll reproduce version 1.1 compatible template tag code that could drive the cycle tag:
<blockquote>
<pre>{% cycle 'row1' 'row2' %}</pre>
</blockquote>
<pre>And the Python code behind it:</pre>
<blockquote>
<pre>class CycleNode(Node):
    def __init__(self, cyclevars):
        self.cycle_iter = itertools.cycle(cyclevars)
    def render(self, context):
        return self.cycle_iter.next()</pre>
</blockquote>
To take their example, if you write a tag that cycles different styles for list items, and two threads hit that tag node, you might get cycling that crosses the thread boundaries.  Typically, one client request is getting one request, and another the other.  One client in that example would get two odd styles, and the other would get two even styles - even though in Django 1.1, since the template tag node was not cached, each user would get an odd, even cycle of their styles - the expected behavior.

What this means for people with custom tags?  In English, this is only really an issue if context can't be global.  Keep in mind that the variable passed will still be thread-safe (they are stored in the thread, not the template node code).  If you are using a template tag that depends on the context of the template at a given moment, then you need to worry and follow their advice of testing render_context, if not, it's ok.

Keep posted for a discussion on the <a href="http://docs.djangoproject.com/en/dev/ref/contrib/messages/#ref-contrib-messages">Messaging API</a> next.
