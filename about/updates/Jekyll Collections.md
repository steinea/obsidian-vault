---
layout: update
category: updates
title: Jekyll Collections
date: 2022-12-09
permalink: 2022/12/09/jekyll-collections
---

For once a straightforward update to the site! While working on the genealogy section of the site, I learned about Jekyll's [collections](https://jekyllrb.com/docs/collections/) functionality and implemented the section as a collection. This was as simple as adding four lines of code to <code>_config.yml</code>, including one line to call NiklasEi's [Jekyll custom permalinks](https://github.com/NiklasEi/jekyll_custom_permalink) gem. This in turn was easily installed by adding <code>gem 'jekyll_custom_permalink', '~> 0.0'</code> to my Gemfile, and then running <code>bundle install</code> on the Pi.

Having implemented one collection, my mind was now open to all of the possibilities that collections afford. But, in their default implementation, collections must be placed at the site root, which make the directory structure quite messy very quickly. There's functionality to account for this, however, and so with another line of code, and some shuffling of folders in the repository, I was set. I pushed the changes, re-executed the server, and after a quick build, everything was up and running. To the user, everything looks the same as before, but now it is much cleaner in the back end.

This article at [Jekyll One](https://jekyll.one/pages/public/manuals/j1/content/collections/) had some useful points of clarification for Jekyll's documentation. This is the code in <code>_config.yml</code>:

<pre>
collections_dir: collections
collections:
  genealogy:
    output: true
    custom_permalink_placeholders: ["sosa"]
    permalink: /genealogy/:sosa/:title/
</pre>

Note the custom permalink to sort genealogy pages by [Sosa-Stradonitz](https://en.wikipedia.org/wiki/Ahnentafel) number, pulled from the yaml in each markdown file.

Also note that it is not necessary to add <code>_posts</code> to the list of collections in <code>_config.yml</code>, *but* the directory must be moved from the site root into the new collections directory, along with any other collections, in order for posts to continue to be accessible.

Up until now, the site had used separate <code>_posts</code> subdirectories within each page's directory. I inverted this to make the collection cleaner, so now the directory looks like this:

<pre>
_posts
 -- blog
  --- post01.md
  --- post02.md
 -- commonplace
  --- entry01.md
  --- entry02.md
 -- journal
  --- record01.md
  --- record01.md
 -- log
  --- log01.md
  --- log01.md
</pre>

A final note: unlike <code>_posts</code>, the other default directories prefixed with an underscore that live in the site root---<code>_layouts</code> and <code>_plugins</code>---do not need to be moved into the collections directory.
