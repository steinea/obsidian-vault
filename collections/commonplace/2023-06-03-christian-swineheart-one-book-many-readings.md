---
layout: entry
category: commonplace
author: Christian Swinehart
title: One Book, Many Readings
publication: Samizdat
link: https://samizdat.co/cyoa/
date: 2023-06-03
---

"Like many children of the 80s, I spent a significant proportion of my rainy afternoons in worlds conjured up by the [Choose Your Own Adventure](http://www.chooseco.com) book series"

"As recounted on the official [History of cyoa](https://www.cyoa.com/pages/history-of-cyoa) page, 100,000 copies of *Space and Beyond* were ‘seeded’ at libraries around the U.S. in 1980 in an attempt to kickstart sales"

"though your actions were limited to the often vexing choices offered to you, there was actual uncertainty as to how things would play out, and direct feedback based on your decisions"

"It is less surprising that this kind of interactive, hypertextual book happened at all than that it happened so late in the life of the book as a medium. One of the fundamental properties of books as objects is their ability to be dealt with in a random-access fashion. All those loose paper edges let you jump to a page more or less directly, without having to go through all the intervening material as you would with an ancient scroll (or ancient [audiotape](http://www.c-90.org/catalogue/tapes/Denon%20-%20Columbia))"

"Historically, reference books have made use of this aspect most directly. Dictionaries cut [indentations](http://www.thefreedictionary.com/thumb+index) into the pages to help you find the neighborhood of your entry then let you flip along glancing at guide words to finish your search. Likewise encyclopedias use their alphabetical organization (itself a fairly [recent](http://research.swtch.com/2008/04/alphabetical-order.html) innovation) to allow for a kind of hyperlinking as one entry typically references several others"

"Outside of the realm of task-oriented books, this sort of [hopscotch](https://web.archive.org/web/20090215093827/http://quarterlyconversation.com/hopscotch-by-julio-cortazar-review) across the contents is a rarity. And the cyoa books are actually not exceptions in this respect, for they too are books that perform a task"

"But rather than being a definition retrieval system or associative datastore, their interactive function is to create a gameworld for the reader"

"This is part of the wonder of these books – they took a pre-existing set of interface conventions designed for utilitarian search tasks and mapped a new activity onto it"

"Interactive gamebooks started to appear in the late 70s, around the same time that [Interactive Fiction](http://www.ifarchive.org/) popped into existence with [Colossal Cave Adventure](http://xyzzy.io/play/adventure) (which begat [Zork](http://xyzzy.io/play/zork) and, in turn, [Infocom](http://en.wikipedia.org/wiki/Infocom)). Whether in paper or electronic form, these games all hinge upon movement through a set of static locations: pages in the book, or ‘rooms’ in the text adventure"

"And from any one of these locations you can move to a new one based on a set of fixed rules. The book might offer you the choice of going to page 13 vs 22 while the game lets you choose rooms to the north, west, or south"

"This sort of locations-and-transitions structure is known in computer science jargon as a [finite state machine](http://en.wikipedia.org/wiki/Finite-state_machine), a branch of theory an old classmate summed up as ‘flocks of circles and arrows’"

"His quip was accurate in that the analysis of these sorts of systems takes the form of drawing out [diagrams](http://www.flickr.com/photos/emkladil/375995342/) of transitions between ‘states’."

"At its atomic level, a cyoa book is a collection of numbered pages of a few different types. Most pages tell a portion of the story, then finish by telling you to jump to another page. A smaller number of pages tell a conclusion to the story and represent an endpoint with no further jumps"

"We can subdivide these ‘narrative’ and ‘endings’ groups further based on the number of choices offered or the goodness of the ending"

"To visualize this, imagine color-coding every page in the book and then laying the pages out next to each other"

"In scanning over the distribution of colors in this plot, one clear pattern is a gradual decline in the number of endings. The earliest books (in the top row) are awash in reds and oranges, with a healthy number of ‘winning’ endings mixed in. Later cyoa books tended to favor a single ‘best’ ending (see CYOA 44 & 53). The most extreme case of this was actually not a Choose Your Own Adventure book at all but a gamebook offshoot of the Zork text adventure series. [The Cavern of Doom](https://samizdat.co/cyoa/img/etc/the-cavern-of-doom.jpg) (labeled WDIDN 3 above) has a virtually linear progression where endings later in the book are increasingly better than those on earlier pages. This is reflected in the nearly unbroken spectrum from red to blue when scanning down the rows"

"The one outlier is the catastrophic ending seen in the third row from the bottom. This was a punishment page that could only be reached by cheating. Unlike most other endings in the book it does not offer to let you continue the story from a few pages back but instead calls you a cheater and leaves you with no choice but to start over from the beginning"

"Unless of course you were reading the book with a finger tucked in at the page of your most recent choice, a strategy which informal polling has shown to be surprisingly common among grown readers of these books.

*The Cavern of Doom* shows a consciousness of this insurance-policy play style in its ‘reset’ approach to bad endings, saving you the trouble of remembering what page to turn back to when your plans go terribly awry"

"Video games too went through this transition from the finality of the `GAME` `OVER` screen to a more benevolent system of save-points as the medium shifted from coin-ops to home systems"

"Forcing you to start over from the beginning is a great way to turn your [frustration](https://strategywiki.org/wiki/Ghosts_%27n_Goblins) into another quarter down the slot. But when the customer pays for the cartridge up-front, financial success is no longer directly correlated with the number of barrel-squashed Marios, and in-game failure can be used as a [catalyst](https://www.wired.com/2006/08/saved-by-the-bell-2/) rather than a tax"

"Another surprising change over time is the decline in the number of choices in the books. The mess of light grey boxes in the top row gives way to books like A New Hope (CYOASW 1) which have more pages devoted to linear narrative than to decisions and endings combined. But to address this apparent pattern with more rigor it would be best to look at the numbers of pages in each category independent of their placement in the book"

"I’d be very curious to know the reason for this progression toward linearity. Presumably the invisible hand was guiding this development, but whether the hunger was for less difficulty in the books or simply for something with more in the way of traditional storytelling is harder to unravel"

"It could be that the glut of choices in the early books reflected more a rush toward the new than a well-considered balancing of storytelling and reader-directedness"

"Just as looking at a film only in terms of its individual frames would be missing the point, considering the pages of a CYOA book in isolation ignores what makes the structure of these books special. As in all hypertext systems, pages make up the body of the organism, but it is the nervous system of connections between them that allows for emergent properties to develop"

"Part of the fun in playing through these books (or part of the obsession) was trying to find every ending and every path. In attempting to map out the structure of the choices a similar concern arises since we don’t want to miss any of the less-traveled corners of the book. Here again computer science offers an methodology for dealing with this problem. The first step is to look at the list of all the book’s choices in a different way: by drawing a map of its branches. In doing so we transform the book into a tree-like datastructure known as a [directed graph](http://mathworld.wolfram.com/DirectedGraph.html) and can then use the wealth of established traversal methods to map out all the possible paths through it"

"In the post-[microcomputer](http://en.wikipedia.org/wiki/Altair_8800) world, we think little of operating on long lists of information because we have so successfully offloaded the painstaking work upon our machines. It’s easy now to forget how much of a drag it was to deal with these sorts of data-shuffling problems before the mass [democratization of computing](https://youtu.be/Ba4kdetNc_M) in the 80s. When the first of these books were conceived, computers were at best a fringe product (sometimes requiring [carpentry](http://images.google.com/images?q=apple+I) skills). But this is a fringe that clearly overlapped with at least some of the early [authors](http://www.infocom-if.org/authors/meretzky.html) of these books"

"So it’s an open question how the ordering of pages was decided.[‡](https://samizdat.co/cyoa/#fn2) Did they write programs in Integer BASIC? Assign page numbers pulled out of a hat? Draw a napkin sketch? Short of first-hand information I can only speculate. But this is where superimposing the choices onto the order of pages in the final book can suggest some possibilities"

"It’s also fair to ask which came first: the choice structure or the stories? In the case of crossword puzzles, the puzzle-writer’s first descision is typically the pattern of blacked-out squares to build off of. Next comes a compatible set of interconnecting words, and finally the clues"

"One wonders whether CYOA pages were written out of the need to fill in predetermined positions in the tree. Or, in a more organic scenario, whether the tree was simply an emergent pattern falling out of the choices in the story"

"*The Cavern of Doom* is resolutely single-threaded, with a spine of near-universally travelled choices seen in the thick arcs moving left to right. Notably there is only a single choice (both in this view and in the entire book) that goes back to an earlier page"

"*House of Danger* has a form typical of books from later in the series. There is a dense section of activity on the early pages, but paths quickly begin jumping to quite distant pages. In addition there is an almost even balance between forward and backward jumps. These traits suggest a more-or-less random ordering of pages after the writing was complete. What is odd is that in a number of books with patterns similar to this, there is still a bias in favor of forward jumps. So clearly the process wasn’t purely stochastic, but all the same the method remains lost in the noise"

"*Chimney Rock* is simultaneously more varied and more regular. At any given position in the book, a choice is likely to take you forward by a more or less fixed number of pages. This is reflected in the grid-like pattern created by the overlapping arcs. In addition, choices frequently go to sequences of pages (e.g., choices A, B, and C going to pages 12, 13, and 14), thus the number of arcs that seem to divide into halves or thirds just as they land"

"Though the fun of these books came from working your way through the story choice-by-choice, the challenge which prompted endless rereading was in finding the ‘best’ ending. Perhaps this stems from a desire for narrative closure, wanting the gamebook to behave like a normal one with a ‘real’ ending that can be reached after learning to avoid the suboptimal ones"

"Just as likely it is the game aspect of the books coming to the fore: games exist to be played and *won*"

"The early CYOA books were set up to discourage this kind of play-via-[obsessive-optimization](http://blog.wolfire.com/2009/07/creating-the-illusion-of-accomplishment/). It was rare for there to be a single ending that was unequivocally better than all the others. In addition, the set of best endings was distributed fairly evenly throughout the branches of the decision tree, so early choices don’t necessarily take you out of the running for a good ending"

"Stories that built toward a single, ideal ending were more the province of non-CYOA gamebooks, particularly the [Time Machine](https://samizdat.co/cyoa/img/etc/time-machine-2@2x.jpg) series and the Zork books"

"The way *[The Cavern of Doom](https://samizdat.co/cyoa/books/cavern-of-doom)* handles this progression toward the ‘you win’ ending is particularly ingenious (and in keeping with the gameplay style of the text adventures). Over the course of the book, choices take you slowly forward and the endings get progressively better as you go. The ending on page 119 is unambiguously the goal both through its placement at the very end of the book and, more explicitly, by awarding you 10 out of 10 points in the final sentence"

"The story follows the same arc on each rereading but allows the reader to diverge from the main thread for a page or two in search of items that are key to solving puzzles later in the book"

"These kinds of [fetch quests](http://en.wiktionary.org/wiki/fetch_quest) are a staple of computer games, and [adventure games](http://www.scummvm.org/screenshots/lec) in particular. What these special items add to a game is a kind of persistent state in addition to the player or reader’s current location (e.g., you are on the page with a locked door and you either have the key or do not)"

"The book pulls this off through a series of sieves and funnels in which choices split off to certain pages where you find an item and others where you avoid the spooky hut or dark cave"

"In a computer game, tracking this kind of inventory state is a simple matter. By flipping bits in memory, the program itself can keep a running tally of items you’ve encountered and possibly picked up. In a book this responsibility falls to the reader, and with it an expectation of honesty"

"To encourage a degree of fair play, the *Cavern of Doom* engages in a form of entrapment by asking the reader, in the midst of a dicy situation, whether they have a magic item that would clearly save the day. What the book knows and the reader may not is that this item does not even exist. Woe upon the adventurer who angers the gamebook in this way"

"This kind of trust-but-verify behavior is one way to deal with the ease of ‘cheating’ in these books. But this presumes that the only way for them to be enjoyed is through following the prescribed directions on each page. *Inside UFO 54-40* neatly turns this idea on its head by instead rewarding this sort of creative interpretation of the rules"

"In the story, your Concorde flight is interrupted when you are beamed aboard a nearby [spacecraft](https://samizdat.co/cyoa/img/etc/schematic-54-40.jpg) trolling the universe for intelligent life. Once aboard you discover your new captors, the U-TY, are interested in keeping you around only to the extent that you can help them find Ultima, the ‘planet of paradise’. The planet’s location is cloaked in mystery and you are only told that it’s a place that cannot be reached ‘by making a choice or following directions’. However this is all foreshadowing for when the reader finally becomes frustrated in the apparently impossible quest and begins flipping through the book hunting for that ending. In fact not choosing *is* the only way to reach Ultima"

"The branch diagram for *UFO 54-40* is unique in that it has one ending – the Ultima ending – which is completely disconnected from the rest of the story. It exists as an island, unreachable through choices but discoverable thanks to the random-access nature of the book"

"This ending was not just an [easter egg](http://en.wikipedia.org/wiki/Easter_egg_(media)) for the obsessive reader who didn’t mind skimming every page looking for telltale words. Instead it’s hard to miss in even a casual riffling. A two-page illustration showing what could only be paradise (or perhaps a theme park) leaps out as the only spread in the book without any text. Flipping to the page before brings you to 101, where you discover that your curiosity has been rewarded. You have found the planet, not by following the constraints of the system, but by going [outside](http://www.urbandictionary.com/define.php?term=Kobayashi%20Maru) of them – a fitting moral to the story and an encouraging reminder that any game should be a starting point for the imagination, not the end"
