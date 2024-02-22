---
layout: entry
category: commonplace
author: Ben Brubaker
title: Life Lessons in Games
publication: Quanta Magazine
link: https://www.quantamagazine.org/the-computer-scientist-who-finds-life-lessons-in-board-games-20230125/
date: 2023-06-03
---

"Though theoretical, the work had practical applications — and often, he found, practical applications led to new theoretical insights"

"Teng has turned his attention to the beautiful mathematics behind games like tic-tac-toe, chess and Go. In such “combinatorial” games, there’s no element of chance, and both players always know everything about the state of the board. Yet combinatorial games remain challenging because the number of ways a game can play out might be dizzyingly large"

"Game theory researchers like to generalize such games to ever larger boards — scaling up tic-tac-toe from 3-by-3 squares to *n*-by-*n*, for instance — and quantify the difficulty of determining which player will win given some initial board state"

"The different possible answers sort games into the same “[complexity classes](https://www.quantamagazine.org/tag/computational-complexity)” that crop up throughout theoretical computer science"

"One famous complexity class goes by the prosaic name P, for “polynomial time,” and contains the kind of problems that can be solved in a reasonable amount of time, roughly speaking. Problems in the equally famous class NP may take an unreasonable amount of time to solve, but their solutions are easy to check. For problems in another complexity class, dubbed PSPACE, even such efficient verification isn’t guaranteed. When researchers consider the “deep logic” of two-player games — “if you do X, and then if I do Y, and then if you do Z,” and so on — they often find themselves talking about PSPACE. But as Teng has helped prove, the mathematics of combinatorial games is not always straightforward"

"“If you don’t know, it doesn’t matter, as long as you are able to think.”"

"Oh, I love board games! There are beautiful connections with complexity theory"

"Kyle Burke was my student, working on numerical analysis at the time. He came to my office and said there could be a beautiful board game of Sperner’s lemma: Two players iteratively color a board, and whoever induces a three-color triangle will lose the game. The best board games have winners rather than a tie, and here, clearly someone will win. Why? Because Sperner’s lemma!"

"I called my friend David Eppstein from Irvine to talk about what makes a good board game. He said, “A good game has simple rules and a beautiful board, and it has to be PSPACE-hard.” Because if you can solve it in polynomial time, a computer would beat you all the time."

"We had a [paper](https://arxiv.org/abs/2106.02114) recently about an open question: If you put two polynomial-time-solvable games together, side by side, would that make them PSPACE-hard? At each move you can only play one of them. This is called summation of games."

"In the ancient game Go, when you put down enough stones, you get many separate arenas, so in some sense you are playing a sum of games. You have to worry about this corner and that corner. You want to win the whole thing, but that doesn’t mean you have to win every part."

"It’s philosophically interesting, right? It’s like you have a war, and it has many battles, but your attention is finite. At any moment you can only make a single decision on one of the battlefields, and your opponent can either respond or double down in some other battlefield. I was trying to explain this to my father. When you play a sum of games, it really means: How do you lose strategically?"

"We proved it for two games, but you can put three games together and the theorem is still true: Three polynomial-time games put together can become PSPACE-hard"
