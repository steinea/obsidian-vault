---
layout: update
category: updates
title: Subdomain and IndieWeb
date: 2023-09-15
permalink: 2023/09/15/subdomain-and-indieweb
---

A short update to help me remember the recent technical tasks I've completed for the site.

First, a couple months ago I got a subdomain set up for my genealogy research, which can now be found at [genealogy.steinea.ca](https://genealogy.steinea.ca). After a bit of research, it turned out to be fairly straight forward. I created a separate complete site repository on [GitLab](https://gitlab.com/steinea/genealogy), and then went through the process of deploying the site on Netlify, as I originally described in [this post](https://www.steinea.ca/2023/01/23/site-live). Then, I went into my DNS records on Hover, created a CNAME record with the hostname <code>genealogy</code> and the target name set to the default Netlify URL for the new site. Then, in the production domains settings in Netlify, I added a new domain alias for <code>genealogy.steinea.ca</code> and set it to primary. After a few minutes to propagate, the new subdomain was live.

Second, I've been getting back into doing [IndieWeb](https://indieweb.org/) research, and starting to look at the process of [indiewebifying](https://indiewebify.me/) my site. The first step after publishing your own website on your own domain is set up web sign in with [IndieAuth](https://indieweb.org/IndieAuth), and I saw that one of the options for signing in to IndieAuth is with PGP. This reminded me that I'd been meaning to do some updates to my PGP profile on [Keyoxide](https://keyoxide.org/ECEDBC433379CF13E2534C29B5B0AA7ED4509C8B), and so I had to read through some documentation to remind myself how GPG notation works.

The documentation for Keyoxide has been updated and is now, at least for me, very confusing. However, thanks to the wonder that is the Wayback Machine, I was able to recover the pages of the original links I saved and follow the steps as outlined there, which are still valid. To [add claims](https://web.archive.org/web/20220125171413/https://docs.keyoxide.org/key-management/adding-claims/), simply follow the steps detailed for your site of choice. I needed to set up claims for GitLab, Mastodon, and DNS (I had previously created GitHub and Twitter claims). For [GitLab](https://web.archive.org/web/20220125180227/https://docs.keyoxide.org/service-providers/gitlab/), you simply create a new repository <code>gitlab_proof</code> with <code>openpgp4fpr:FINGERPRINT</code> in the description, and then add the matching notation to your gpg key. For my own memory, this involves the following steps:

* <code>gpg --edit-key FINGERPRINT</code>
* <code>notation</code>
* <code>proof@ariadne.id=https://gitlab.example.com/USERNAME/gitlab_proof</code>
* <code>save</code>
* <code>gpg --keyserver hkps://keys.openpgp.org --send-keys FINGERPRINT</code>

Similarly, for [Mastodon](https://web.archive.org/web/20220125165801/https://docs.keyoxide.org/service-providers/mastodon/) (ActivityPub), you can either add a metadata tag for PGP with your fingerprint, or for Keyoxide with your profile URL. I chose the latter option, and then followed the same steps as above to publish the notation, except for the proof line which needed to be:

* <code>proof@ariadne.id=https://INSTANCE.ORG/@USERNAME</code>

Finally, for [DNS](https://web.archive.org/web/20220125172121/https://docs.keyoxide.org/service-providers/dns/), the steps are slightly different to get the proof set up, but not all that difficult. Once again, I went to my DNS records on Hover, but this time created a TXT record with the hostname <code>www</code> and the content <code>openpgp4fpr:FINGERPRINT</code>. Then, follow the same sequence as above, but replace the proof line with:

* <code>proof@ariadne.id=dns:DOMAIN?type=TXT</code>

This propagated almost instantly and is now verifiable on my Keyoxide profile along with my other proofs. Deleting a claim is similarly easy. To do so, follow these steps:

* <code>gpg --edit-key FINGERPRINT</code>
* <code>notation</code>
* <code>-proof@ariadne.id=dns:yourdomain.org?type=TXT</code>
* <code>save</code>
* <code>gpg --keyserver hkps://keys.openpgp.org --send-keys FINGERPRINT</code>

In case it's hard to tell, simply preface the proof with a - (minus) sign, and then save and publish, and the proof will be removed from both key and profile.

Third, and finally, I got IndieAuth set up. All that needed to be done here was to upload a copy of my [public PGP key](https://www.steinea.ca/publickey.asc) to my site, and then add a link in the header of my default Jekyll layout pointing to the key. This looks like the following:

* <code>&lt;link rel="me" rel="pgpkey" href="/publickey.asc"&gt;</code>

I originally didn't include the <code>rel="me"</code> and testing worked fine on [IndieLogin](https://indielogin.com/). However, login did not work on [IndieWebify.Me](https://indiewebify.me/) so I added the additional <code>rel="me"</code> attribute to the link. This also didn't work, and nor, with further testing, did [IndieAuth.com](https://indieauth.com/setup). It seems this is at least in part due to the deprecation due to [naming confusion](https://indieweb.org/IndieAuth-brainstorming#naming_confusion) of the IndieAuth site, and IndieLogin is the new current service. For more on web sign-in in general, see the [wiki page](https://indieweb.org/Web_sign-in).

On IndieLogin, I was immediately prompted with a string to sign using my PGP key. I tried signing a file <code>INPUT.txt</code> with Kleopatra, but even deselecting the option to encrypt, no matter the file extension, the output was a garbled binary file. I couldn't find a work around, so I just did it the old fashioned way in the command line:

* <code>gpg --clearsign -o SIGNED.txt INPUT.txt</code>

I copied the complete output from the resulting text file, pasted it into the challenge field on IndieLogin, and successfully validated that web sign-in is working on my site. My IndieWeb journey has begun!
