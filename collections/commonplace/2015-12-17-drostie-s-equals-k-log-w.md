---
layout: entry
category: commonplace
author: Drostie
title: "S = k*log(W)"
publication: Yahoo
link: https://ca.answers.yahoo.com/question/index?qid=20090423013431AABs7Gy
date: 2015-12-17
---

It's written on Ludwig Boltzmann's tombstone, and it means that "entropy is the logarithm of multiplicity." It's a thermodynamics and statistical mechanics fact. 

Let's step back a bit. 

Sometimes, the things which you know about the world are not a complete picture of it: this coffee cup in my hand has a certain volume of coffee, a certain temperature, an internal pressure profile, sugar content, number of molecules of water, et cetera. That's on the order of 10 variables that we know. By contrast, it's made up of 10^25 or so molecules, and each of those molecules can be defined by on the order of 10 scalar parameters -- 3 dimensions of position, 3 dimensions of momentum, 3 dimensions of angular momentum, 3 dimensions of a dipole moment is 12, off the top of my head. 

So there's around 10^26 parameters about the system that I don't know, and around 10 that I do. What happens when I'm missing such a great deal of information about the world? 

Well, we have to start grouping. The coffee cup has a secret "microstate" among these 10^26 variables, and I don't know which one it is exactly because a lot of these microstates "look the same" to me. 

Meanwhile, what I *can* see is a "macrostate" among the 10 variables. And you can interpret the macrostate also as the set of all microstates which all "look the same" to me. In turn, the system's "state" can be any of its microstates as usual: but now, that microstate implies some macrostate as well. So the system is in a microstate, and it's in the corresponding macrostate, and I see the latter -- not the former. (Reread these paragraphs at least twice, until you're sure you understand the difference between "macrostates" and "microstates.") 

Well, the most obvious thing that you can do -- although nobody really thought of it until Boltzmann -- is to ask, "how many microstates are in a macrostate? How 'big' is it?" We call this number the "multiplicity", W. It's just counting. 

So W is a macrostate parameter which just counts how many microstates all "look the same." The system finds itself in some particular microstate, and that implies that it's in the such-and-so macrostate, and now we can say that our level of uncertainty about the particular microstate is something like "one in W," because there are W microstates that we could also have been in. 

Why does this matter? Because uncertainty propagates! Generally, if I lack knowledge about the world, that uncertainty increases, rather than decreases, in size. 

In certain conditions (constant number of particles in a fixed volume with a fixed total internal energy) we should expect to see that the molecules just "choose" a microstate at random -- and then the macrostate with the highest multiplicity is just the most likely to show up when the molecules find themselves in a microstate. More importantly, we should see that our uncertainty grows until we're in the most uncertain state: again, just the macrostate with the biggest W. 

Now, there's one thing about multiplicities that I haven't mentioned yet, and it makes them frustrating to work with. They *multiply*. If you imagine that my coffee cup is in a macrostate with a multiplicity W, and you imagine that I *also* don't know whether the light in the next-door room is on or off, then my uncertainty grows to 2W -- there are W microstates if the light next-door is on, and W if the light next-door is off, because they're independent.  

Or, if I have two independent coffee cups: for each of the W microstates in the first one, there are another W in the second one, so we should add W + W + W... a total of W times. That's a multiplicity of W². 

To get around this, we use the logarithm of multiplicity instead. If the total multiplicity of two systems W1 and W2 always combines like W = W1 W2, we can just take the logarithm of both sides to find that: 

log W = log W1 + log W2. 

So that L = log W is *additive* rather than *multiplicative*. (Bonus: the logarithm function is always increasing, so a maximum of W is also a maximum of L.) 

Now we can immediately do something cool with this: Let's just use this notion that "the world spontaneously goes to the state with highest W" to describe spontaneous heat flows. Let's take two boxes, at fixed total particles, fixed volume, fixed total energy. But let's allow them to share energy with each other. A packet of energy "q" goes from box 1 to box 2. 

If the variables are continuous or roughly so, then there's some parameter P which says, "if you change the energy in the box by an amount ΔE, then there's a corresponding change in L, which we'll denote by P ΔL = ΔE."  

(Edit: sorry, Yahoo thinks my comment was too large. Basically, you can show that P is proportional to temperature with some universal constant k, and thus the thermodynamic definition of entropy as ΔS = ΔE / T becomes just S = k log W, as you might have expected.)
