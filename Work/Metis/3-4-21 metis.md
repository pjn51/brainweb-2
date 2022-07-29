# Metis Notes for Thursday, March 4th
`LINKS:` [[metis week 9]]
#meeting/career

---
This morning we have a [[deep learning]] assessment, a few investigations, and then we have a lecture on "big [[data]]."

## Investigation - [[GANs]]
Generative adversarial networks are really good at creating fake images. These are the kinds of things that have gained a lot of attention for creating fake faces and other kinds of things. 

The key term here is *adversarial*. Two networks are pitted against each other. One network is the generative network that creates fake images. The other one is the descriminator, which tries to detect fake images. By playing off one another, both get better at outsmarting the other. It's sort of like an arms race. 

After the generative network starts to outsmart the descriminator about half the time, we get rid of the descriminator otherwise it will start messing up the results. 

## Lecture - big data
- What counts as big data?
	- Any amount of data that breaks down our typical workflow or processes.
	- If it crashes your computer, it's big data.
	- Once we have big tools, we're gonna need big data to use them.

### Issues with Big Data
- Volume
	- Vertical scaling (getting a better computer) is \$\$\$\$ 
	- Horizontal scaling (getting more computers) is really complicated 
	- Stability and consistency become an issue as you scale either way.
- Velocity
	- Big data is often a moving target, with new observations coming in quickly
	- Incoming data must be cleaned, stored, and analyzed at the rate it is arriving
	- Most [[data science]] processes have complexity of at least $O(n)$
	- If you parallelize your work, how can we ensure no data falls through the cracks?
	- How do we even parallelize on a 60TB dataset???
- Variety
	- We need to be able to handle all kinds of data, like text, images, sound, and video
	- Data isn't clean and structured all the time. Often there are gaps all over the place and column names that make no sense
- Veracity
	- If you have 1000 samples, having a 4 st dev process occur is rare af.
	- If we have a billion samples, that rare process will happen a million times. 
	- We have to be ready for these weird things happening when we work with so much data
- Moral of the story: we need big data tools for big data that's big

### Handling Big Data
- If it fits in RAM, use [[Pandas]] and [[NumPy]]. Check how much RAM your computer has and don't exceed it or else your machine will crash.
- If it doesn't fit in RAM but still works on the computer, use [[Dask]] locally.
- If it's bigger than that, use [[Spark]] or dask as a cluster.

