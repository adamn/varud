---
layout: post
title: Cassandra learnings
wordpress_id: 218
wordpress_url: http://varud.com/?p=218
date: 2009-11-20 15:21:59.000000000 -05:00
---
I've been reading up on NoSQL databases for our new deployment.  We're down to two: Cassandra and MongoDB.  I wish I'd been more thorough about the decision to get it down to those two but suffice to say that we only got rid of the others (Voldemort, CouchDB, etc...) if they didn't support sharding, if they didn't have Python libraries, if they weren't 'mature', or for a few other specific reasons.  We didn't just deny solutions out of hand.

I'm just focused on Cassandra right now because my colleague, Ara, is focused on MongoDB.  We will be jousting later on about which software is best.

Pros:
<ul>
	<li>Shards can handle datasets larger than the memory available (unlike Redis which can't handle more data than it has RAM).  This is a pro only in our case where we're expecting many GB of data.</li>
	<li>Favors <a href="http://wiki.apache.org/cassandra/ArchitectureOverview">Availability and Partitioning</a> over Consistency - although it is <a href="http://www.allthingsdistributed.com/2008/12/eventually_consistent.html">Eventually Consistent</a>.</li>
	<li>Fully supports replication, partitioning, self-repair, etc... without application-level logic.</li>
	<li>Supports asynchronous write where the node takes the right and returns control to the client while the the node takes care of forwarding the write appropriately.  The write is logged locally for fault tolerance.</li>
	<li>Data is split locally between Memtable (on RAM) and SSTable(on disk) for low latency and low volatility.</li>
	<li>'Bloom Filter' allows very fast checking of uniqueness (i.e. keys) without having to touch the Data File - for increased speed to check whether a key exists.</li>
	<li>Supported Python <a href="http://github.com/digg/lazyboy">client library</a> maintained by Digg.</li>
	<li>Write is non-blocking - no read required.</li>
	<li>Writes are atomic within a ColumnFamily.</li>
	<li>'Remove' functionality uses 'Tombstones' to mark a record as ready for deletion so that deletes are asynchronous.</li>
</ul>
Cons:
<ul>
	<li>'Schema' changes require restarting service.</li>
	<li>No Commercial support.</li>
	<li>Writes are favored over reads (which is good for typical scenarios, but worth considering for some people).</li>
	<li>Loss of <a href="http://www.maxineaston.co.uk/cassandra/">Libido</a></li>
</ul>
