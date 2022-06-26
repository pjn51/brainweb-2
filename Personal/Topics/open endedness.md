# Open endedness: The last grand challenge you've never heard of
`LINKS:` [[data science]] | [Source](https://www.oreilly.com/radar/open-endedness-the-last-grand-challenge-youve-never-heard-of/)
`TAGS:` 

---
For something to be open ended means that it continually produces more and more content, on a higher and higher level of complexity. The best example is [[evolution]]. 

Through relatively unassuming processes, evolution has created life itself, and evolved that life up to the point we humans are at today. Pretty impressive!

However, open endedness has proved impossible to program. [[evolutionary algorithms]] (EAs) usually run for a bit, then find an optimization solution and stop running. But that isn't what happens in evolution. 

This leads to a critique of EAs, that other methods are just better at optimizing. However, the failure of EAs to mimic evolution isn't a reason to abandon EAs, it's a reason to investigate them even further. Why don't they produce the complexity that we *know* evolution can produce???

Solving this question would result in the creation of a never-ending creativity machine. 

## A brief history of open-endedness
Because of the inspiration of natural evolution, the search for open-endedness has mainly focused on EAs. However, this might not be the answer, and some other sort of process could result in open-endedness being replicated. 

When we search for open-endedness, we aren't looking to solve a specific problem or optimize for a situation, we want to see an explosion of complexity that goes deeper and deeper the longer it runs. 

The early research into this took the form of creating artificial "worlds" populated by artificial creatures that ran around and ate each other and stuff. The goal is to get the creatures to evolve increasingly complex survival strategies in competition with one another. 

Certain metrics for measuring open-endedness were developed. These are called "activity statistics." The ability of some simple systems to pass "activity statistics" tests has sown doubt about their ability to quantify open-endedness. 

Others have questioned if open-endedness is really so great. What we really want are solutions to problems, and we're only impressed with complexity that solves real problems. How can we measure raw "innovation" in this context? 

The field may be able to advance despite these controversies, similar to how AI has advanced despite nobody having any idea what intelligence really means. 

The field was expanded with the introduction of the concept of "novelty search." The idea is to depart from the evolutionary standard for selection, which is survivability. Instead, the algorithm selects for novelty alone. This can increase the number of different directions a system can go in, instead of forcing optimization and closing off alternatives. 

Novelty search seems similar to random search, but ends up being more interesting. Computing the novelty of a candidate in search space needs some info about the candidate relative to other candidates. The result is rapid divergence of candidates, while random search doesn't have this happen. For example, a novelty search method was able to train a robot to walk faster than random search was, and it was even faster than conventional attempts to breed the best walkers. In short, [[Novelty search works surprisingly well as an EA]]. 

A new class of algorithms emerged that tried to combine the benefits of novelty search with some objective criteria for candidates. These were called quality diversity (QD) algos. They included novelty search with local competition (NSLC) and multi-dimensional archive of phenotypic elites (MAP-Elites). 

[One MAP-Elites method](https://arxiv.org/abs/1407.3501) for teaching a robot how to walk was to develop a whole repertoire of gaits, and then allow the robot to switch between them if it ran into issues walking. 

All the methods above are cool, but stop producing novel results very quickly. One issue is that there just aren't that many possibilities in a lot of these search spaces. Once you've tried every way of walking, there's no more open-endedness to be found. The same thing happened with maze-solving algos. 

We have put a lot of work into making sure the algo can find new ways of doing things within the search space, but we aren't as good at expanding the search space itself to allow for new possibilities. 

For example, the evolution of trees, which started as a survival strategy for bushes and small plants, became a [[forest ecology#Niches|niche]] in which new species were able to create a novel strategy. In this way, the creativity of a system should be able to theoretially sustain itself for longer. 

## The necessary ingredients

## Open-endedness in practical domains

## Open-endedness in AI

## Joining the quest

