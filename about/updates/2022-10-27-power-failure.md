---
layout: update
category: updates
title: Power Failure
date: 2022-10-27
---

There was a power failure today. After the power came back and I rebooted the pi, I had issues serving the site.

For some reason, the default Ruby had reverted on reboot. <code>rvm use 3.1.2 --default</code> did not seem to have done the job. I tried a variant, <code> rvm --default use 3.1.2</code>, and then discovered that I have to run <code>bash -l</code> after reboot before I can run Ruby/RVM commands. I tried again, and this time successfully switched to 3.1.2, and then was able to serve the site with <code>bundle exec jekyll serve --livereload</code>.

A few more reboots today for a variety of reasons, and it seems I always need to set Ruby to 3.1.2 after reboot. I have not yet been able to figure out a way to make the default *actually* default.
