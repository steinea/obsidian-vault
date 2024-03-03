---
layout: update
category: updates
title: Second Attempt
date: 2022-10-25
permalink: 2022/10/25/second-attempt
---

Yesterday after much pain and suffering, I broke everything. Turns out, I <code>sudo</code> installed some or all of Ruby. I couldn't figure out how to fix it, so I nuked the pi and started over. Thankfully, logging my misadventures helped me do things (mostly) correctly today. I'm logging the steps for my future self in case I have to do this again. So, first:

<pre>
sudo apt-get update
</pre>

This returned the expected error:

<pre>
e: repository 'http://archive.raspberrypi.org/debian buster inrelease' changed its 'suite' value from 'testing' to 'oldstable'
n: this must be accepted explicitly before updates for this repository can be applied. see apt-secure(8) manpage for details.
</pre>

So I allowed the release change, and proceeded:

<pre>
sudo apt-get --allow-releaseinfo-change update
sudo nano /etc/apt/sources.list
deb https://raspbian.freemirror.org/raspbian/ buster main contrib non-free rpi
sudo apt-get upgrade
</pre>

This time I checked if Ruby was already installed, and it was. Ruby v2.5.5p157.

Next, RVM. Curl comes pre-installed, so I just needed to get gnupg2.

<pre>
sudo apt-get update
sudo apt-get install -y gnupg2
</pre>

I had the same issue with gpg keys as before. I imported the .asc files directly, and then was able to curl and install RVM successfully:

<pre>
curl -sSL https://get.rvm.io | bash -s stable
source /home/pi/.rvm/scripts/rvm
</pre>

Now to update Ruby to latest, v3.1.2, and RubyGems to latest, v3.3.24:

<pre>
rvm install 3.1.2
rvm docs generate-ri
rvm use 3.1.2 --default
gem update --system
</pre>

Then, update the path for Ruby Gems as directed by the Jekyll instructions:

<pre>
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
</pre>

Check GCC and Make to be safe (v8.3.0 and v4.2.1 respectively):

<pre>
gcc -v
make -v
</pre>

And finally, install Jekyll (v4.3.0):

<pre>
gem install jekyll bundler
jekyll -v
jekyll new website
cd website
bundle exec jekyll serve --livereload
</pre>

I proceeded to replace the Jekyll defaults with my own site. Most I was able to just get rid of. I kept the default <code>_config.yml</code>, added my own specifications, and removed some of the irrelevant ones (such as theme).

Now to get to work building the full site!
