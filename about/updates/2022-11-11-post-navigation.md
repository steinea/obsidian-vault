---
layout: update
category: updates
title: Post Navigation
date: 2022-11-11
---

Today's project was to get next and previous hyperlinks working for my [commonplace book](/portal/commonplace/). Jekyll and Liquid have nice built in functionality for generating next and previous links without having to hard code anything. I added the following, pulled from [David Elbe](http://david.elbe.me/jekyll/2015/06/20/how-to-link-to-next-and-previous-post-with-jekyll.html)'s site, and it worked immediately:

{% raw %}
<pre>
&lt;h4&gt;Previous Entry &lt;span style="float:right;"&gt;Next Entry&lt;/span&gt;&lt;/h4&gt;

&lt;div class="postNavigation"&gt;
  {% if page.previous.url %}
    &lt;a class="prev" href="{{page.previous.url}}"&gt;&laquo; {{page.previous.title}}&lt;/a&gt;
  {% endif %}

  {% if page.next.url %}
    &lt;span style="float:right;"&gt;&lt;a class="next" href="{{page.next.url}}"&gt;{{page.next.title}} &raquo;&lt;/a&gt;&lt;/span&gt;
  {% endif %}
&lt;/div&gt;
</pre>
{% endraw %}

However, this code does not account for post *categories*, and so I quickly discovered that the next and previous buttons would take me to other posts on the website (such as those under [blog](/blog/) or [log](/about/log/)). After some sleuthing, and quite a bit of trial and error, I arrived at the following solution, adapted from the solution at [Adam Clarkson](https://ajclarkson.co.uk/blog/jekyll-category-post-navigation/)'s site.

First, I created a new generator, <code>WithinCategoryPostNavigation.rb</code>, and added it to a new subdirectory <code>_plugins</code>:

<pre>
module Jekyll
  class WithinCategoryPostNavigation < Generator
    def generate(site)
      site.categories.each_pair do |category, posts|
        posts.sort! { |a,b| b <=> a}
        posts.each do |post|
          index = posts.index post
          next_in_category = nil
          previous_in_category = nil
          if index
            if index < posts.length - 1
              previous_in_category = posts[index + 1]
            end
            if index > 0
              next_in_category = posts[index - 1]
            end
          end
          post.data["previous_in_category"] = previous_in_category unless previous_in_category.nil?
          post.data["next_in_category"] = next_in_category unless next_in_category.nil?
        end
      end
    end
  end
end
</pre>

Jekyll knows to run <code>.rb</code> files in the <code>_plugins</code> folder by default. Next, I just had to tweak the Liquid in my commonplace entry layout to the following:

{% raw %}
<pre>
&lt;h4&gt;Previous Entry &lt;span style="float:right;"&gt;Next Entry&lt;/span&gt;&lt;/h4&gt;

&lt;div class="postNavigation"&gt;
  {% if page.next_in_category != nil %}
		&lt;a href="{{page.next_in_category.url}}" class="next-link"&gt;&laquo; {{page.next_in_category.title}}&lt;/a&gt;
  {% endif %}

	{% if page.previous_in_category != nil %}
    &lt;span style="float: right;"&gt;&lt;a href="{{page.previous_in_category.url}}" class="previous-link"&gt;{{page.previous_in_category.title}} &raquo;&lt;/a&gt;&lt;/span&gt;
  {% endif %}
&lt;/div&gt;
</pre>
{% endraw %}

I had a heck of a time getting the next and previous links to display *and* link correctly. For some reason, Clarkson's solution has <code>page.next_in_category</code> link to the next *older* post, while <code>page.previous_in_category</code> links to the next *newer* post. The solution above involved swapping next and previous in the <code>.rb</code> file and putting next on the left and previous on the right in the <code>entry.html</code> layout. This is still not quite right, though, because the swap in the <code>.rb</code> effectively accomplishes nothing, because I've been forced to put next and previous on the wrong sides from each other anyway.

Regardless, from the end user perspective it's working the way I want it to now, even if the code is counterintuitive. I'll leave it as  and try to be content.
