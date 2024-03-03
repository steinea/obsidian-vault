---
layout: update
category: updates
title: Repository Setup
date: 2022-11-08
---

I have been busy with content for the last few weeks, but today my task was to get the repository for the site set up so I could have things nicely versioned and backed up. This will also allow me to add content to the site remotely, rather than directly on the pi.

First, I made sure git was configured to sign commits with my gpg key. I followed GitHub's [guide](https://docs.github.com/en/authentication/managing-commit-signature-verification/telling-git-about-your-signing-key):

<pre>
git config --global user.signingkey FINGERPRINT
git config --global commit.gpgsign true
[ -f ~/.bashrc ] && echo 'export GPG_TTY=$(tty)' >> ~/.bashrc
</pre>

Next, I initialized a new repository in my existing local directory for the website.

<pre>
echo "# test" >> README.md
git init
git add README.md
git commit -m "Initialize Repository"
</pre>

I hadn't actually configured git fully yet, so got an error here. I configured git as directed:

<pre>
git config --global user.email "EMAIL@ADDRESS.com"
git config --global user.name "MY NAME"
</pre>

I was then able to make my first commit successfully and proceed from there:

<pre>
git branch -M main
</pre>

Then, I got the remote set up at [Codeberg](https://codeberg.org/steinea/website), and continued on:

<pre>
git remote add origin https://codeberg.org/steinea/website.git
git push -u origin main
</pre>

And here is where the trouble started. Trying to push via HTTPS kept returning the error <code>server certificate verification failed. CAfile: none CRLfile: none</code>. From my searching, this error appeared linked to a certificate expiry event last year that impacted everyone using Let's Encrypt, but I was unable to resolve the issue (even after lots of technical help from my engineer friend who actually knows what he's doing).

I tried lots of different approaches:

<code>sudo update-ca-certificates</code> ran, but had nothing to update.

This [discussion](https://github.com/probonopd/MiniDexed/discussions/269) presented a possible solution, so I ran:

<pre>
openssl s_client -showcerts -servername codeberg.org -connect codeberg.org:443 &lt; /dev/null 2 &gt;/dev/null | sed -n -e '/BEGIN\ CERTIFICATE/,/END\ CERTIFICATE/ p'  &gt; codeberg-org.pem
</pre>

<pre>
cat codeberg-org.pem | sudo tee -a /etc/ssl/certs/ca-certificates.crt
</pre>

This ran successfully, but I still could not push, receiving the same error.

I tried to reinstall my certificates:

<pre>
sudo apt-get install --reinstall ca-certificates
</pre>

Which successfully reinstalled the certificates, but also did not resolve the problem.

So after all of this, my friend suggested I try SSH instead of HTTPS.

<pre>
ssh-keygen
</pre>

I followed the steps, creating a local directory for SSH keys, and adding a secure password. For reference, my public key fingerprint is:

<pre>
SHA256:8xlNrcyvXGuxzE7tl6VerlTqlRv0dlZSY7JPjxUPflE pi@Maia
</pre>

My randomart image is:

<pre>
+---[RSA 2048]----+
|                E|
|             .  .|
|            ..o=.|
|           = o+o=|
|        S . =.oo*|
|         o o .=O*|
|          o  oBB%|
|           . **X=|
|            o+*o+|
+----[SHA256]-----+
</pre>

I then added the key to my Codeberg account, and reset the origin for git to use SSH:

<pre>
git remote rm origin
git remote add origin git@codeberg.org:steinea/website.git
git push -u origin main
</pre>

When prompted, I verified Codeberg's SSH fingerprint prior to accepting it. The fingerprint can be found in Codeberg's [documentation](https://docs.codeberg.org/security/ssh-fingerprint/).

And with this, I at last successfully pushed! Now, to add everything from the website. This was my first experience with git in the terminal rather than in a GUI, so it took some getting used to, but all very straight forward:

<pre>
git status
git add /home/pi/website
git commit -m "Initial website setup and content"
git push -u origin main
</pre>

Now, I can breathe a bit more easily with version control in place. With all the power failures lately as winter storms start to pick up, I have had some concern about a surge borking the pi, so I feel much better.
