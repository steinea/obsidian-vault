---
layout: entry
category: commonplace
author: Bitestring
title: Web Fingerprinting
publication: Bitestring
link: https://www.bitestring.com/posts/2023-03-19-web-fingerprinting-is-worse-than-I-thought.html
date: 2023-10-09
---

"you might set your web browser to automatically clear cookies or use add-ons to do that.

But companies found another way to uniquely identify you across different sessions and websites without using cookies or other persistent storage. It’s called web fingerprinting"

"Fingerprinting is a more sophisticated approach to identify a user among millions of others. It works by studying your web browser and hardware configuration. Many websites use a fingerprinting library to generate a unique ID. This library collects data from multiple JavaScript APIs offered by your web browser. For example, websites can see web browser version, number of CPUs on your device, screen size, number of touchpoints, video/audio codecs, operating system and many other details that you would not want a typical news website to see"

"Firefox has a setting called resistFingerprinting (initially contributed by The Tor Project) that makes it more resistance to fingerprinting. When activated, Firefox tries to mask certain properties like User Agent, CPU Count, Timezone, Screen Resolution etc. uniform for all users. This makes it harder for fingerprinting"

"You can enable it by visiting `about:config` and setting `privacy.resistFingerprinting = true` in your Firefox browser"

"Chromium (Chrome) is built by Google, an advertisement company which tracks its users for showing relevant ads. So naturally it doesn’t have any inbuilt protection against fingerprinting. Chromium (and Google Chrome) is vulnerable to fingerprinting"

"Tor Browser is made by [The Tor Project](https://www.torproject.org/), a non-profit organization. Tor Browser routes internet traffic through multiple relays across the world, thus making user’s browsing sessions more private. It is based on Firefox and many features of Tor Browser has been incorporated back in Firefox"

"FingerprintJS could not link two different Tor Browser sessions by the same user. So Tor Browser is more secure against fingerprinting"

"Given there are companies selling fingerprinting as a service, if you want to really protect yourself from fingerprinting, you should use Tor Browser or Firefox with `resistFingerprinting=true`"
