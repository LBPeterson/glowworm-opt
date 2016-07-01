# glowworm-opt

Glowworm swarm optimization

[From Wikipedia:](https://en.wikipedia.org/wiki/Glowworm_swarm_optimization)
>The glowworm swarm optimization (GSO) is a swarm intelligence optimization algorithm developed based on the behaviour of >glowworms (also known as fireflies or lightning bugs). The behaviour pattern of glowworms which is used for this algorithm >is the apparent capability of the glowworms to change the intensity of the luciferin emission and thus appear to glow at >different intensities.
>
>1.The GSO algorithm makes the agents glow at intensities approximately proportional to the function value being optimized. >It is assumed that glowworms of brighter intensities attract glowworms that have lower intensity.
>
>2.The second significant part of the algorithm incorporates a dynamic decision range by which the effect of distant >glowworms are discounted when a glowworm has sufficient number of neighbours or the range goes beyond the range of >perception of the glowworms.

In short, the GSO finds local maximum or minimum points in a function passed to it. Each worm is scored, then effects other worms that have a lesser score than it does by exerting influence, or "pulling" the poorer scored worms toward it. Add in a bit of random jitter among all worms, and they find peaks in the funciton quite quickly. 

## This example

This is an example of 20 worms on a 10 x 10 grid optimizing for maximum. Given a worms location, its' score is determined by the fitness function, which in this example was made up to provide multiple local maximums within the area. The result is seen here:

![glowworm_normal.gif](glowworm_normal.gif)

The worms find four local maximums, two of which are more significant than the others. To understand why four maximums were found, see that each group of worms was outside the influence of the other groups of worms. The influence area can be adjusted, and is set somewhat arbitrarily for the example. See the areas of influence for each worm below:

![glowworm_influences.gif](glowworm_influences.gif)

The 'pull' from each worm on another is an interesting thing. Given two worms of the same influence strength, one wants the closer worm to exert more 'pull'. At the same time, given two worms of the same distance, one wants the one with larger influence strength to exert more 'pull'. This balance is acheived by calculating the ratio of distance from one worm to the worm it is being pulled towards and the distance of the pulling worms' influence. This ratio is then subtracted from one, and the moving worm will move that percentage of distance to its puller. This ensures that a balance of distance and influence strength is accounted for.
