---
layout: update
category: updates
title: Markdown Journal
date: 2022-11-21
permalink: 2022/11/21/markdown-journal
---

I wanted to update my [HTML Journal](/portal/journal) so that it would build the journal in [m15o's format](https://journal.miso.town/) from a collection of markdown files, rather than being hardcoded in html. This will make it much easier for me to write and post journal updates, as well as to maintain the journal page itself.

The update was relatively straightforward. In the old format, all of my journal entries lived in a single html file. I split these out and reformatted them as individual markdown files, and then placed them in a <code>_posts</code> subdirectory in my journal folder. Then, I adapted the basic Jekyll blog post index to include the entire content for each post, as well as to use the required html elements for the journal to fit m15o's format (<code>&lt;article&gt;</code> and <code>&lt;h2&gt;</code>). This looks like so:

<pre>
{% for post in site.categories.journal %}
 &lt;article&gt;
  &lt;h2 class="journalHeading"&gt;{{ post.date | date: "%Y-%m-%d" }} &lt;a href="{{ post.url }}"&gt;{{ post.title }}&lt;/a&gt;
  {{ post.content }}
 &lt;/article&gt;
 &lt;br&gt;
{% endfor %}
</pre>

Each journal entry now gets its own permalink by default, thanks to Jekyll's blogging functionality. I've also added inter-post navigation to these individual journal pages, but in doing this, I discovered some peculiar behaviour. Between my different portals with <code>_posts</code> subdirectories, when reaching the first or last post in the category, if there is a post with an earlier or later date in another portal category, the navigation will take you out of the current category and into the other. Posts are *not* getting interspersed with each other, nor is this occurring with posts in other directories, such as this [log](/about/log) or my [blog](/blog) so the solution is still mostly working, but this behaviour is not ideal. It's something to do with how Adam Clarkson's solution that I [adapted](/2022/11/11/post-navigation) is using <code>index</code> to order posts, but I'm not confident to troubleshoot it at this time.

Regardless, for now, I'm pleased with the new system, and it's already enabled me to make journaling a (slightly) more regular activity, adding back-entries that I had written but not had time to add in html.
