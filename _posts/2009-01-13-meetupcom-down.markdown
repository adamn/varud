---
layout: post
title: Meetup.com Down
wordpress_id: 146
wordpress_url: http://www.varud.com/?p=146
date: 2009-01-13 11:06:24.000000000 -05:00
---
I noticed today that <a href="http://meetup.com/">Meetup.com</a> is down.  I've noticed this before with sites that are growing but aren't yet "big".  <a href="http://twitter.com">Twitter</a> and their <a href="http://images.google.com/images?q=fail+whale&amp;oe=utf-8&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a&amp;um=1&amp;ie=UTF-8&amp;sa=X&amp;oi=image_result_group&amp;resnum=4&amp;ct=title">fail whale</a> is of course an obvious example.  What do these sites have in common?  They run <a href="http://www.mysql.com">MySQL</a>.  I'm a big fan of MySQL and have been using it since version 3.23 in 2001.  However, it simply is not a robust database when scaled horizontally unless you do alot of trickery.  The main problem is that it cannot be clustered without giving up referential integrity.

For those who are unaware, referential integrity is when you have two tables with data that are in lockstep with eachother.  These tables are just like spreadsheets in Excel - a set of columns and a set of rows.  Let's imgine that there is one table for all the desks in a building and one table for all the employees in a building.  Each row in the 'desks' table would have an entry for the location of the desk and who sits at that desk.  Each row in the 'employees' table would have an entry for each employee - first name, last name, etc...  If a database has referential integrity between the two tables, you can never have an employee in the 'desk' table without that employee also existing in the 'employees' table.

Many people say "Good Riddance" when they give up referential integrity.  It obviously takes alot of processing power to maintain those relations and sometimes there's a reason that an application needs flexibility in the situation.  For example, if the 'desks' and 'employees' tables are in the same database as a 'payrolls' table, there could be a situation where we need to be able to deal with the fact that an employee was fired by deleting them from the 'employees' table even though that person has now become a consultant and still uses the desk.  The biggest problem with database design is that as the application matures, business logic put into the database can become outdated and difficult to extend.

However, most modern applications accept the need for deep reliability about certain fundamental data points.  There is typically a situation where you know that you need that integrity and then you're stuck, in the case of MySQL, between choosing that integrity and choosing uptime.

The best solution to this situation is to have multiple read-only MySQL servers and 2 write-only MySQL servers acting as a master-slave.  All typical web requests would hit the read-only databases.  Any logging type requests would be queued for insertion into the master write-only database.  There are 2 of these databases so that one can be dropped at any given time.

Cheers!  Meetup.com is back up.
