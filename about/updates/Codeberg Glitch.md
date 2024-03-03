---
layout: update
category: updates
title: Codeberg Glitch
date: 2023-01-07
permalink: 2023/01/07-codeberg-glitch
---

I was working away on the site today, when all of a sudden I stopped being able to pull changes to the Pi. I kept getting the error:

<pre>
git@codeberg.org: Permission denied (publickey).
fatal: Could not read from remote repository.
Please make sure you have the correct access rights
and the repository exists
</pre>

I did a bunch of troubleshooting to try and figure out what was going on, even going so far as to remove my SSH key from Codeberg, erase it from my machine, generate a new keypair, and then upload that to Codeberg, but had no success. Turned out it was a [Codeberg issue](https://codeberg.org/Codeberg/Community/issues/876), and things were resolved in the morning. For the record (updating from the earlier [log](/2022/11/08/repository-setup)), the new public key for the host is:

<pre>
SHA256:kMnGlTCpo6LNISvyDzYHphuGSehcANHEqgaMoNDaN4E pi@Maia
</pre>

My randomart image is:

<pre>
+---[RSA 2048]----+
|o*..  oo..       |
|+ E .o.=.        |
|*=   oB          |
|B.o =. .         |
|+.o+ o  S        |
|O=+.             |
|BX+..            |
|*+o+             |
|+....            |
+----[SHA256]-----+
</pre>
