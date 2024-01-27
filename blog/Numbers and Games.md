---
layout: record
category: excurses-3
title: Numbers and Games
date: 2022-09-09
permalink: 2022/09/09/numbers-and-games
---

# Numbers and Games

[[2022]] / [[blog]]

The fact that the description of games in [combinatorial game theory](https://en.wikipedia.org/wiki/Combinatorial_game_theory#Overview) uses the notation &#123; L &#124; R &#125;, a deliberate application of [Dedekind’s cut](https://en.wikipedia.org/wiki/Dedekind_cut) by which he [constructed the set of the real numbers](https://en.wikipedia.org/wiki/Construction_of_the_real_numbers), strikes me as quite remarkable.

A game is defined as the “list of possible ‘moves’ that two players, called *left* and *right*, can make. The game position resulting from any move can be considered to be another game. This idea of viewing games in terms of their possible moves to other games leads to a recursive mathematical definition of games that is standard in combinatorial game theory.” &#123; L &#124; R &#125; is the notation used to write the definition of a given game. L or *left* indicates “the set of game positions that the left player can move to” and R or *right* “the set of game positions that the right player can move to.” Of course, this definition of a game precludes those other games that are not played out through a series of moves between positions (a closure of understanding that I find problematic. See my [*A Game, Perhaps*](https://vagrantludology.itch.io/a-game-perhaps)). Nevertheless, the parallel between sets of numbers and sets of games fascinates me.

The wiki article for the Dedekind cut does not use &#123; L &#124; R &#125; for its notation, but rather &#123; A &#124; B &#125;. It’s John Conway who makes the connection explicit in chapter zero of [*On Numbers and Games*](https://books.google.ca/books/about/On_Numbers_and_Games.html?id=tXiVo8qA5PQC) (1976):

> Dedekind (and before him the author—thought to be Eudoxus—of the fifth book of Euclid) constructed the real numbers from the rationals. His method was to divide the rationals into two sets *L* and *R* in such a way that no number of *L* was greater than any number of *R*, and use this “section” to define a new number (*L* &#124; *R*) in the case that neither *L* nor *R* had an extremal point.

Conway’s book quickly exceeds my abilities, but I’ll be chewing on this connection for some time. I have already written about the combinatorial quality of games (see my notes “[[Combinatorics]]” and “[[Recombinatorics]]”), so this presents a new region of study for me to explore over the coming years.
