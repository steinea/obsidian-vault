---
layout: entry
category: commonplace
author: Emily Short
title: Beyond Branching
publication: Emily Short's Interactive Storytelling
link: https://emshort.wordpress.com/2016/04/12/beyond-branching-quality-based-and-salience-based-narrative-structures/
date: 2022-12-17
---

"[Quality-based narrative](https://emshort.wordpress.com/category/quality-based-narrative/) is the term invented by Failbetter Games to refer to [interactive narratives structured around storylets unlocked by qualities](http://www.failbettergames.com/tag/narrative-engineering/)."

"A storylet is typically a paragraph or two of text followed by a choice for the user (each option is referred to as a branch in Failbetter parlance) and text describing the outcome of that choice"

"Qualities are numerical variables that can go up or down during play, and represent absolutely everything from inventory (how many bottles of laudanum are you carrying?) to skills (what is your Dangerous skill level?) to story progress (how far have you gotten in your relationship to your Aunt?)"

"**Salience-based narrative** is a term I just made up to refer to interactive narratives that pick a bit of content out of a large pool depending on which content element is judged to be most applicable at the moment. Like QBN, this approach is agnostic about what kind of information matters: just as a quality in *Fallen London* could be pretty much anything, salience narrative can be tied to pretty much any testable information in the world state."

"An excellent example of this is [Elan Ruskin’s dialogue system for Left4Dead](http://www.gdcvault.com/play/1015528/AI-driven-Dynamic-Dialog-through), and more recently it was [picked up by Firewatch](http://www.slate.com/articles/arts/gaming/2016/02/the_video_game_firewatch_and_its_origins_in_1980s_text_adventures.html). Both of these games allow the player to traverse a 3D world and encounter different situations, and they need to be able to feed in dialogue chosen to match those situations tightly."

"It’s not coincidental that both of the “salience-based” applications I mentioned are for triggering dialogue specifically, and that they’re handling a narrative layer transposed on an otherwise explorable environment. I gather that *Firewatch* has a lot of flags under the surface, but it’s also relying a lot on player location and adjacent objects, which provide a bunch of independently-modeled world state. (In contrast, in a QBN system, the qualities *are* the world state. Even location is sort of a quality, and the player can be in exactly one location at a time.)"

"**Waypoint narrative**. Again, I’m making this term up, but it corresponds to the method I used for [Glass](http://ifdb.tads.org/viewgame?id=29l04xfgii5roq63). In *Glass*, the interaction is all about conversation. Both the players and the NPCs are able to change the current conversation topic. Finally, there are trigger topics that advance the story to a new state whenever we reach them."

"In *Glass*, the story engine is constantly trying to heal the story, to move from the player’s chaotic input back towards the next authored beat. The more content I added, the more ways there were to move through the topic space and the more efficient and responsive the story-healing could be."

"Twine is a fabulous tool both for finished work and for prototyping, but it is not really designed for some of these structures. In particular, we should totally be teaching students about Twine and how to use it, but we shouldn’t teach them that that’s the only way to prototype an interactive story, or the way to prototype all forms of interactive story. Otherwise, they’re likely to get stuck on combinatorial explosions that could be solved using another system with more robust state tracking."
