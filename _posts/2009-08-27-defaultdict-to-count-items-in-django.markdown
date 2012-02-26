---
layout: post
title: defaultdict to count items in Django
wordpress_id: 211
wordpress_url: http://varud.com/?p=211
date: 2009-08-27 18:10:43.000000000 -04:00
---
One of the great things I discovered today is <a href="http://docs.python.org/library/collections.html#collections.defaultdict">defaultdict()</a>.   This allows one to create dictionaries with a count for each item in a very compact and powerful way.  Look at this:
<blockquote>
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 0px; width: 1px; height: 1px; overflow-x: hidden; overflow-y: hidden;">&gt;&gt;&gt; for item in NoticeQueueBatchByUser.objects.filter(user=3).values('label','on_site'):</div>
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 0px; width: 1px; height: 1px; overflow-x: hidden; overflow-y: hidden;">...   d[item['label']] += 1</div>
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 0px; width: 1px; height: 1px; overflow-x: hidden; overflow-y: hidden;">...</div>
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 0px; width: 1px; height: 1px; overflow-x: hidden; overflow-y: hidden;">&gt;&gt;&gt; d.items()</div>
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 0px; width: 1px; height: 1px; overflow-x: hidden; overflow-y: hidden;">[(u'pagedisplay_violation', 4)]</div>
<div id="_mcePaste" style="position: absolute; left: -10000px; top: 0px; width: 1px; height: 1px; overflow-x: hidden; overflow-y: hidden;">&gt;&gt;&gt;</div>
<blockquote>&gt;&gt;&gt; from collections import defaultdict</blockquote>
<blockquote>&gt;&gt;&gt; d = defaultdict(int)</blockquote>
<blockquote>&gt;&gt;&gt; for item in ExampleModel.objects.values('label','other_info'):</blockquote>
<blockquote>...   d[item['label']] += 1</blockquote>
<blockquote>...</blockquote>
<blockquote>&gt;&gt;&gt; d.items()</blockquote>
<blockquote>[(u'key_1', 4),(u'another_key',2)]</blockquote>
<blockquote>&gt;&gt;&gt;</blockquote>
</blockquote>
This will give you the number of times each label appears in ExampleModel.objects.values('label','other_info')
