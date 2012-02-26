---
layout: post
title: Pros and Cons of MongoDB
excerpt: MongoDB answers to a potential user's questions.
wordpress_id: 224
wordpress_url: http://varud.com/?p=224
date: 2010-01-22 13:23:52.000000000 -05:00
---
<div>I was recently asked by somebody to answer some questions regarding MongoDB.  Unfortunately, I have yet to use it in production, but Ara, Zach and I have put it through quite a few paces at this point ...</div>
<ul>
	<li><strong>Nature of Use:</strong></li>
<ul>
	<li>Would be useful if you can mention the nature of application (for ex. reporting or analytics ?) you are using MongoDB for?</li>
<blockquote>
	We use MongoDB for high volume logging.  After what we need is logged, we use Python/PyMongo to transform the data into chunks suitable for Postgres.  Postgres is our central data store used for our Django application and all its associated models.
</blockquote>
	<li>What were the other NoSQL storage solutions were evaluated and why MongoDB was chosen against the others?</li>
<blockquote>
	Cassandra was the other one that we got pretty far with.  In terms of maturity and scalability, Cassandra appeared to be the winner.  However, Cassandra has extremely limited query capabilities that weren't sufficient for us.  In addition, MongoDB has plans to focus on scalability which suited our needs fine.
</blockquote>
</ul>
</li>
	<li><strong>Robustness: </strong></li>
<ul>
	<li>How long you have been running MongoDB in production ?</li>
<blockquote>
	Have not run it in production yet.
</blockquote>
	Did you encounter any issues on stability front (any crashes or restart needed) ?
<blockquote>
	One issue is how best to keep it 'living' without human intervention.  So far, the tools have been very straightforward and simpler than solutions for other products.  However, we haven't tested the quality of backups under high load nor have we really pressured the system in the wild.  We architected MongoDB in our system so that we could lose it and all we would lose is incoming data while it was down, not historical data or reporting capabilities (which is ok for us for a few hours).
</blockquote>
</ul>
</li>
	<li><strong>Performance:</strong></li>
<ul>
	<li>What has been your experience on performance side like (queries/sec for the hardware configuration being used)?</li>
<blockquote>
	We hit 30 inserts per second on a high cpu (the lowest 64 bit) Amazon ec2 instance.  However, the bottleneck was in our Python listener, so we don't know how much higher MongoDB could go.  We suspect quite alot as the load average was under .2 during this test.
</blockquote>
	<li>Did the performance degraded when datasize grew?</li>
<blockquote>
	We haven't sufficiently tested this yet.
</blockquote>
</ul>
</li>
	<li><strong>Scalability:</strong></li>
<ul>
	<li>What is the rough datasize (number of records, number of collections, size on the disk?) Mongo is being used for?</li>
<blockquote>
	The goal is to hit 1k inserts/second with real time processing (i.e. using their upsert functionality which is something like INSERT ... ELSE UPDATE) and to hold onto 10M+ records in a collection.  If we weren't confident in that being possible, we would not have chosen MongoDB.
</blockquote>
	Does all the data sit in one MongoDB server or you are using MongoDB in a clustered environment ?. If being used in sharded environment, would like to know your experience because MongoDB does not support auto-sharding out of the box?
<blockquote>
	We are using sharding, but again, we have not pushed it to the limit.  Although it does not support auto-sharding, manually setting up a shard is pretty straightforward.  This is one of the advantages Cassandra has.
</blockquote>
</ul>
</li>
	<li><strong>DataReplication/Persistence:</strong></li>
<ul>
	<li>Did you use data-replication in Mongo? What has been the general experience with it?</li>
<blockquote>
	We are planning to use replication but are not.  As referenced above, we have the option of losing MongoDB for a few hours and not incurring a major business penalty.
</blockquote>
	<li>Regarding persistence of data, did you encounter any issues given that MongoDB does lazy writes to the file system?</li>
<blockquote>
	No, but again it has not been pushed enough for me to feel confident that this is a non-issue.  We are planning using XFS however which does have journaling to account for problems at the file block level.
</blockquote>
</ul>
</li>
	<li><strong>Search:</strong></li>
<ul>
	<li>Did your application required text-searches on the documents stored in Mongo? Since MongoDB does not support text-search out of the box, how did you take care of search?</li>
<blockquote>
	We aren't using full text search.  Our goal with regards to that is to setup Sphinx or something similar when we need something like that.  That seems like the right architectural solution.
</blockquote>
</ul>
</li>
	<li><strong>Support</strong>:</li>
<ul>
	<li>Regarding resolving issues related to Mongo, did you rely on the open-source community or signed up for the paid-support? What has been your experience ?</li>
<blockquote>
	Community.
</blockquote>
</ul>
</li>
	<li><strong>Client-side tools:</strong></li>
<ul>
	<li>Which libraries did you use talking to MongoDB server ? We have web-app to be running in Python and there are two libraries available for Python.</li>
<blockquote>
	PyMongo.
</blockquote>
	<li>Would be great if you can share(pointers) to client-side tools you are using with MongoDB ?</li>
<blockquote>
	The Mongo interface is a bit chunky (the way it uses JSON for everything), so often I just use PyMongo since all of our real code uses that anyway.  Our plan is to only have a small number of collections so any necessary queries would happen through our code, not in an ad hoc way requiring a client gui or something like that.
</blockquote>
</ul>
</li>
</ul>
