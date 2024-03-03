---
layout: update
category: updates
title: Pi, Ruby, Jekyll
date: 2022-10-24
permalink: 2022/10/24/pi-ruby-jekyll
---

At last booted the Raspberry Pi 4 today, a 32 GB EVO+ starter kit with 8 GB of RAM from CanaKit. I received it as a Christmas gift two Christmases ago, and have finally got around to the project.

The plan is to turn the pi into a webserver so I can host my own site. Previously, I've used GitHub pages and the native Jekyll functionality therein, but I want to learn how to do it all myself. I thought about making an even simpler site without Jekyll, but I like the functionality and the cleanliness of the folder structure. As well, an important feature for me is being able to add markdown files that get built to html. I write in markdown, and like to have my source files in that format for human legibility and long term [durability](https://programminghistorian.org/en/lessons/sustainable-authorship-in-plain-text-using-pandoc-and-markdown), as well as for being convertible to other formats via pandoc.

First step after system configuration was to install Ruby, and I immediately ran into problems. Ruby kept getting errors because everything installed was out of date. But I couldn't update anything because the mirror certificate could not be verified. Every time it tried to update via <http://mirror.switch.ca/> it threw an error. After a lot of searching, I came across this brief post: <https://dev.to/ryderdamen/fixing-broken-mirrors-raspberry-pi-1een>. Following the instructions here, I used <code>sudo nano /etc/apt/sources.list</code> to access the list of mirrors, and replaced the listed mirror with <code>deb http://raspbian.freemirror.org/rasbian/ buster main contrib non-free rpi</code> (not https, which gave me more errors). I was then able to run <code>sudo get-update</code>, which was now able to update everything, taking about 45 minutes to do so.

I then proceeded to install Ruby, but when I went to install Jekyll it failed to build. The quick start instructions on the homepage are misleading. I was missing dependencies that I found on the installation page. First, I updated RubyGems to latest, v3.3.24, which also took a significant amount of time, mostly on installing documentation. Then, I realized I'd used a slightly incorrect command to install Ruby on Raspbian, so re-ran, this time with <code>ruby-full</code>.

Having completed the full install, I noticed that the command had installed Ruby v2.5.5p157 by default. I wanted to update this to latest as well to align with [RubyGems](https://rubygems.org/pages/download), which meant I needed to install [RVM](https://github.com/rvm/rvm). It failed on the first attempt, so I installed gnupg2 as recommended. However, the install failed again, so I tried to fetch the public key from the key server. This also failed, so I at last had to <code>curl</code> the .asc files directly. Finally, I was able to install RVM, and proceed to update Ruby to v3.1.2.

After checking GCC and Make, I then followed the simple [directions](https://jekyllrb.com/docs/installation/ubuntu/) to point my environment variables to <code>~/.bashrc</code>, and following that, ran <code>gem install jekyll bundler</code> to *finally* install Jekyll.

I started to get my site directory set up, and was ready to preview. And then Jekyll wouldn't run. Now at almost 1 AM, I threw in the towel for the night.
