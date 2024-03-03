---
layout: update
category: updates
title: Updates and Fixes
date: 2023-09-23
---

Been very busy with site updates over the last week.

First, I moved my <code>/work</code> page to my homepage, reformatting it as a new Curriculum Vitae section with more robust citation information for each line item ([1176683b](https://gitlab.com/steinea/website/-/commit/1176683bf062a7ded74ae931b03676d9c66783ba)).

Then, I migrated my homepage index sections to the <code>_includes</code> directory, cleaning up the index file itself ([168b2668](https://gitlab.com/steinea/website/-/commit/168b266866c66737897d195b21faa6519385d3e7)). This will allow me to have one source file for elements I might want to include on other pages.

Then, I resolved the IndieAuth login issues that had persisted since I first noted them in the last log. It turned out I needed to add an authentication endpoint to my site, which was not clear from the documentation. I added an invisible link to my identities section: <code>&lt;link rel="authorization_endpoint" href="https://indieauth.com/auth"&gt;</code> ([eed18784](https://gitlab.com/steinea/website/-/commit/eed18784aa5bcb31e9f2c227cc41f54ac3358499)).

Then, I added the IndieWeb webring to the footer of the page ([ec86f8b8](https://gitlab.com/steinea/website/-/commit/ec86f8b882cb55a17a3ace12b325e5d47c04b7c5)).

Next, I reran the website carbon scan and added the details to the meta section ([2c670623](https://gitlab.com/steinea/website/-/commit/2c6706232e0af1cd8978273c104ecc43f96040d1)).

After that, I got to work adding h-entry markup to my post layouts ([ab882700](https://gitlab.com/steinea/website/-/commit/ab88270097b2dee8c45195717e2cbc8ca4bb5838)).

Then, I added a line to the site meta that pulls the latest commit reference with the following line of code: <code>&lt;a href="https://gitlab.com/steinea/website/-/commit/{% raw %}{{ site.env.COMMIT_REF }}"&gt;{{ site.env.COMMIT_REF | truncate: 6, ""}}{% endraw %}&lt;/a&gt;</code> ([35a54ce4](https://gitlab.com/steinea/website/-/commit/35a54ce4cab1443529b2ad9f0a8524bca408640e)).

And finally today, I added a support section to my homepage footer with a button linking to my [Liberapay](https://liberapay.com/steinea/) profile ([3dfbc249](https://gitlab.com/steinea/website/-/commit/3dfbc2d9c457c3012f8b1aa82c3dc9e70409747e)). I added the identity to my OpenPGP key, but Keyoxide is having trouble verifying the proof, and there's no elegant way to display it on the Liberapay platform, other than slapping it directly in the profile description (also, my DNS proof fails to verify I'd say over 80% of the time, and seems others in the Keyoxide forums have similar troubles, with no solutions found). Open identity continues to be a pain.

Much done, much still to do!
