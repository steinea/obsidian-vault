---
layout: entry
category: commonplace
author: Geoff Boeing
title: Chaos Theory and the Logistic Map
publication: Geoff Boeing
link: http://geoffboeing.com/2015/03/chaos-theory-logistic-map/
date: 2016-03-10
---

“Chaos theory is a branch of mathematics that deals with nonlinear dynamical systems.”

“A system is just a set of interacting components that form a larger whole.”

“Nonlinear means that due to feedback or multiplicative effects between the components, the whole becomes something greater than just adding up the individual parts.”

“Lastly, dynamical means the system changes over time based on its current state.”

“Chaotic systems are a simple sub-type of nonlinear dynamical systems. They may contain very few interacting parts and these may follow very simple rules, but these systems all have a very sensitive dependence on their initial conditions.”

“Despite their deterministic simplicity, over time these systems can produce totally unpredictable and wildly divergent (aka, chaotic) behavior. Edward Lorenz, the father of chaos theory, described chaos as “when the present determines the future, but the approximate present does not approximately determine the future.””

“An attractor is the value, or set of values, that the system settles toward over time. When the growth rate parameter is set to 0.5, the system has a fixed-point attractor at population level 0 as depicted by the blue line. In other words, the population value is drawn toward 0 over time as the model iterates. When the growth rate parameter is set to 3.5, the system oscillates between four values, as depicted by the gray line. This attractor is called a limit cycle.”

“But when we adjust the growth rate parameter beyond 3.5, we see the onset of chaos. A chaotic system has a strange attractor, around which the system oscillates forever, never repeating itself or settling into a steady state of behavior. It never hits the same point twice and its structure has a fractal form, meaning the same patterns exist at every scale no matter how much you zoom into it.”

“Beyond a growth rate of 3.6, however, the bifurcations ramp up until the system is capable of eventually landing on any population value. This is known as the period-doubling path to chaos. As you adjust the growth rate parameter upwards, the logistic map will oscillate between two then four then eight then 16 then 32 (and on and on) population values. These are periods, just like the period of a pendulum.”

“By the time we reach growth rate 3.9, it has bifurcated so many times that the system now jumps, seemingly randomly, between all population values. I only say seemingly randomly because it is definitely not random. Rather, this model follows very simple deterministic rules yet produces apparent randomness. This is chaos: deterministic and aperiodic.”

“Incredibly, we see the exact same structure that we saw earlier at the macro-level. In fact, if we keep zooming infinitely in to this plot, we’ll keep seeing the same structure and patterns at finer and finer scales, forever. How can this be?”

“I mentioned earlier that chaotic systems have strange attractors and that their structure can be characterized as fractal. Fractals are self-similar, meaning that they have the same structure at every scale. As you zoom in on them, you find smaller copies of the larger macro-structure. Here, at this fine scale, you can see a tiny reiteration of the same bifurcations, chaos, and limit cycles we saw in the first bifurcation diagram of the full range of growth rates.”

“The plot on the left depicts a parabola formed by a growth rate parameter of 3.9. The plot on the right depicts 50 different growth rate parameters between 3.6 and 4.0. This range of parameters represents the chaotic regime: the range of parameter values in which the logistic map behaves chaotically. Each growth rate forms its own curve. These parabolas never overlap, due to their fractal geometry and the deterministic nature of the logistic equation.”

“Strange attractors are revealed by these shapes: the system is somehow oddly constrained, yet never settles into a fixed point or a steady oscillation like it did in the earlier Poincaré plots for r=2.9 and r=3.5. It just bounces around different population values, forever, without ever repeating a value twice.”

“Now we can see our chaotic system (in red, above) constrained by its strange attractor. In contrast, the random data (in blue, above) just looks like noise. This is even more compelling in the 3-D Poincaré plot that embeds our time series into a 3-dimensional state space by depicting the population value at generation t + 2 vs the value at generation t + 1 vs the value at t.”

“In three dimensions, the beautiful structure of the strange attractor is revealed as it twists and curls around its 3-D state space. This structure demonstrates that our apparently random time series data from the logistic model isn’t really random at all. Instead, it is aperiodic deterministic chaos, constrained by a mind-bending strange attractor.”

“Chaotic systems are also characterized by their sensitive dependence on initial conditions. They don’t have a basin of attraction that collects nearby points over time into a fixed-point or limit cycle attractor. Rather, with a strange attractor, close points diverge over time.”

“Both have the same growth rate parameter, 3.9. The blue line represents an initial population value of 0.5. The red line represents an initial population of 0.50001. These two initial conditions are extremely similar to one another. Accordingly their results look essentially identical for the first 30 generations. After that, however, the minuscule difference in initial conditions starts to compound. By the 40th generation the two lines show little in common.”

“If our knowledge of these two systems started at generation 50, we would have no way of guessing that they were almost identical in the beginning. With chaos, history is lost to time and prediction of the future is only as accurate as your measurements.”

“In real-world chaotic systems, measurements are never infinitely precise, so errors always compound, and the future becomes entirely unknowable given long enough time horizons.”

“Real-world chaotic and fractal systems include leaky faucets, ferns, heart rates, and random number generators. Many scholars have studied the implications of chaos theory for the social sciences, cities, and urban planning. Chaos fundamentally indicates that there are limits to knowledge and prediction.”

“Some futures may be unknowable with any precision.”

“Deterministic systems can produce wildly fluctuating and non-repeating behavior. Interventions into a system may have unpredictable outcomes even if they initially change things only slightly, as these effects compound over time.”

“During the 1990s, complexity theory grew out of chaos theory and largely supplanted it as an analytic frame for social systems. Complexity draws on similar principles but in the end is a very different beast. Instead of looking at simple, closed, deterministic systems, complexity examines large open systems made of many interacting parts.”

“Unlike chaotic systems, complex systems retain some trace of their initial conditions and previous states, through path dependence. They are unpredictable, but in a different way than chaos: complex systems have the ability to surprise through novelty and emergence. But that is a tale for another day.”
