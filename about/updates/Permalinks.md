---
layout: update
category: updates
title: Permalinks
date: 2022-11-20
permalink: 2022/11/20/permalinks
---

I discovered that my permalink format in <code>_config.yml</code> had a hardcoded element left over from the original build of the site. Every post, no matter the type, had the prefix <code>/blog</code> in its url. This was because I had the global permalink set as:

<pre>/blog/:year/:month/:day/:title</pre>

The [Jekyll documentation](https://jekyllrb.com/docs/permalinks/) had an easy fix. I simply had to replace <code>/blog</code> with <code>/:categories</code>, like so:

<pre>/:categories/:year/:month/:day/:title</pre>

However, this produced some peculiar results. I currently have four directories with posts on the site: /blog, /portal/commonplace, /portal/journal, and /about/log.

The first three worked as expected, displaying as with the examples below:

<pre>/blog/2022/06/19/compost-epistemology
<br>/portal/commonplace/2022/11/10-william-gibson-the-jackpot
<br>/portal/journal/2022/11/03/the-peripheral</pre>

But for some reason, my site log had an extra term added to the url:

<pre>/about/log/update/2022/11/11/post-navigation</pre>

My blogs use the layout type "post," my commonplace book uses the layout type "entry," and my journal uses the layout type "journal." Similarly, my logs use the layout type "update," but for whatever reason only these posts interpolated the layout type between the category and the date. I ultimately decided to remove category entirely, and settled on a simple date prefix instead:

<pre>/:year/:month/:day/:title</pre>

Though calling out the category in the url would be nice, this format makes for a much more compact link, and won't break in the future if I decide to move a collection of posts to a new category, or change the category name. The permalink will remain the permalink, separate from site navigation within a given category.

A weird thing though... While fussing around with all of this, I somehow caused the post navigation to flip again, as I struggled to resolve in [2022-11-11](/2022/11/11/post-navigation) log. For whatever reason, the point that had nagged at me in that log was now precisely the thing requiring a fix. I opened the <code>.rb</code> file and flipped back the <code>next_in_category</code> and <code>previous_in_category</code> variables, while leaving the navigation div with next on the left and previous on the right (and so under their opposite headings). I could probably now do the opposite, re-flip the variables in the <code>.rb</code> and then put next and previous on the correct side in the navigation div, but I'm going to save that attempt for another day. With this fix, everything appears to be working properly again.
