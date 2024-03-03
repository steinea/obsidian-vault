---
layout: update
category: updates
title: Alexandria
date: 2023-03-21
---

One of my larger projects over the last few months has been getting what I am referring to as "Alexandria" up and running here on the site---a unified back end for tracking my library of books and reading notes, comparable to what I have already set up for my [commonplace](/collections/documents/commonplace/).

As of today, all the updates are made and I now have a very easy system. A custom template for books allows me to generate Chicago format citations for each from YAML. Some liquid logic allows me to display annotations, if I have made them. Multiple date fields allow me to list books by the date they entered my [library](/collections/documents/library) and by the date I finished reading and [annotating](/collections/documents/annotations) them.

The [bibliographies](https://www.steinea.ca/collections/documents/bibliographies/) I have been adding to the site since January can now be built with a simple for loop that iterates through the books category of posts, looking for specific tags. For now, all the bibliographies here are hard-coded, and I likely won't worry too much about going back through and updating them. But, for new research projects, as I get my hands on new books and takes notes, I can have bibliographies that will dynamically update with these new materials. A nice quality of life improvement to my research and record-keeping workflows.
