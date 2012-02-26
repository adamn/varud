---
layout: post
title: Install Eclipse Galileo for Django and Pinax – Part 2
wordpress_id: 195
wordpress_url: http://varud.com/?p=195
date: 2009-06-17 10:07:50.000000000 -04:00
---
Now, onto getting Pinax installed for development purposes:

I really don't like how things have gone with Pinax installation in the past few months.  I'm going to give my own take on things.  Pinax has moved to <a href="http://github.com">GitHub</a> and so should you.  

First, create an account at GitHub.  Then, fork <a href="http://github.com/pinax/pinax/tree/master">Pinax</a> so you have your own copy to work with.  For me, I have my development version <a href="http://github.com/AdamN/pinax/tree/master">here</a>.  If you want this repository to be private, you can pay GitHub $7/month - well worth it if this is a corporate gig.

Now you can follow the Pinax directions from your own fork.

<code>$ curl -O http://github.com/AdamN/pinax/raw/master/scripts/pinax-boot.py
$ python pinax-boot.py --development ../Documents/workspace/WhateverYouNamedProject/src/pinax
$ source ../Documents/workspace/WhateverYouNamedProject/src/pinax/bin/activate
(pinax)$ cd ../Documents/workspace/WhateverYouNamedProject/src/pinax
(pinax)$ pip install --requirement src/pinax/requirements/external_apps.txt</code>

At this point, if you have an existing installation of Pinax on your machine, you may get an error about django-wikiapp being the wrong version.  In a new command line tab, run: 

<code>pip install django-wikiapp==0.1.2</code>

If it says it's already installed, you may need to delete the existing django-wikiapp in the directory shown by the error in the pip install command above.  Now it's time to start a project:

<code>(pinax)$ pinax-admin clone_project basic_project myproject
</code>
You now have a Pinax site in myproject/ directory

<code>(pinax)$ cd myproject
(pinax)$ ./manage.py syncdb
(pinax)$ ./manage.py runserver</code>

Now, go to your browser and navigate to http://127.0.0.1:8000

Hopefully, you now see a Pinax website in all its glory.




