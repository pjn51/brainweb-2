# Sample and Population
---
# In [[statistics]]
## Population
This is the total group being studied, the complete set of observations. Usually too large to study. 

We want the population parameter, such as the population mean or the variance.

## Sample
A subset of the population. We can only gather the sample parameter, and use this to make inferences about population parameters.

It’s important to maintain a representative sample when collecting it. 

## Central limit theorem
If you repeatedly sample from a distribution, regardless of the original probability distribution, the distribution of your sample means will approach the [[normal distribution]]. 
It will be more similar to the normal distribution as you increase the size of each sample taken from the population. 

In a nutshell, we can think of any variable as a combination of weighted factors. Some factors are more important than others, but theoretically you can model the variables going into any feature or characteristic in the world. This works as long as the dependent variable has a normal distribution. If not, this idea falls flat. 

## Law of large numbers
If we perform an experiment many many times, the average result will approach the expected value of the distribution that was being sampled from. Basically, as we repeat an experiment again and again, the expected pattern will slowly emerge in the data out of the chaos of each individual trial. 

# Populations in [[environmental science]]
Populations are dynamic, varying over time and space. There are two variables that describe a population: distribution and abundance. 

Dispersal patterns unique to the species link the populations of a species to one another. This keeps the populations genetically similar. Dispersal patterns depend on a number of factors, such as the distribution of resources, competition, and the method of dispersal (seed, flying, swimming, etc)

## Limits to population movement
The distribution of suitable habitat determines the distribution of a population. This depends on both biotic and abiotic factors. These factors cause most species to have a rather patchy distribution, because the world is a very diverse place in terms of habitable zones for individual species. Only true generalists can span extremely large ranges of habitats. 

## Estimating populations
We have to sample if we want to estimate a population 'in the wild'. There are multiple methods of doing this. One method is an area-based count. If you count all the members of a species in a square mile, and multiply by the range of the species, then you might have a good estimate for population, as long as the population density is the same in the square mile you measured as it is elsewhere.

Another method is mark-and-recapture. You capture as many of the species as you can, and mark them. 

## Predator-prey dynamics in python
We can model simple predator-prey dynamics in python...

```python
import matplotlib.pyplot as plt

def predPrey():
    t = 0

    foxes = [10]
    fox_death_rate = 0.5
    fox_birth_rate = 0.015

    rabbits = [100]
    rabbit_death_rate = 0.015
    rabbit_birth_rate = 0.5
    
    while t <= 1600:
        baby_fox =  foxes[-1] + 
					0.01*(fox_birth_rate*foxes[-1]*rabbits[-1] - 
					fox_death_rate*foxes[-1])
        baby_rabbit =rabbits[-1] + 
					 0.01*(rabbits[-1]*rabbit_birth_rate -
					 rabbits[-1]*rabbit_death_rate*foxes[-1])

        foxes.append(baby_fox)
        rabbits.append(baby_rabbit)
    
        t += 1

    plt.plot(rabbits, color = 'blue', label = 'rabbits')
    plt.plot(foxes, color = 'red', label = 'foxes')
    plt.title('Foxes and Rabbits')
    plt.xlabel('Time')
    plt.ylabel('Population')
    plt.legend()
```

This returns...
![[foxes_and_rabbits.png]]

Over time, the fox population rapidly increases, until it starts to deplete the rabbit population, at which point the fox death rate overtakes the birth rate, and the rabbit population begins to recover. These boom-and-bust cycles are common in the natural world. 

## Forest floor cover dynamics
The dynamics of floor composition in forests can be surprisingly complex. Take a beechwood forest for instance. For every plot of beechwood forest floor, we can model the successional pattern as having four stages: gap, bare, oxalis, and rubis. 

### Gap
Gap means that there is natural light streaming down to the floor, and there is no vegetation to block it. We would expect to see a lot of gap after a disturbance event like a fire.

### Bare
Bare indicates that trees have moved into the area, but there is no undergrowth. This is because at the beginning of a forest stand, trees are grouped so closely together that there isn't any available light for undergrowth.

### Oxalis
Oxalis is a flowering plant that is a first-on-the-scene colonizer of forest floor space. As trees thin out due to competition, the oxalis take advantage of the new light sources and multiply.

### Rubis
Rubis is a family of bushes like blackberries, raspberries, etc. They eventually outcompete the oxalis, but take longer to invade an area. 

### Modeling dynamics in python
We can model the interactions of these species / floor cover states in python...
```python
def succession(endYr, fireChance):
    from random import randint
    import matplotlib.pyplot as plt
    import numpy as np
    gap = [.25]         # defining variables, setting starting values
    bare = [.25]
    oxalis = [.25]
    rubis = [.25]
    fireChanceInt = fireChance * 100
    i = 1               # creating time variable
    while i <= endYr:
        newGap = gap[-1] + .018*oxalis[-1] + .018*rubis[-1] - .067*gap[-1]          # defining change rates for variables
        newBare = bare[-1] + .067*gap[-1] - .015*bare[-1]
        newOxalis = oxalis[-1] + .015*bare[-1] - .018*oxalis[-1] - .05*oxalis[-1]
        newRubis = rubis[-1] + .05*oxalis[-1] - .018*rubis[-1]

        gap.append(round(newGap, 5))        # adding new values to original variable list
        bare.append(round(newBare,5))
        oxalis.append(round(newOxalis,5))
        rubis.append(round(newRubis,5))

        diceRoll = randint(0,100)
        if diceRoll <= fireChanceInt:
            gap[-1] = gap[-1] + (1-.66)*bare[-1] + .5*oxalis[-1] + .5*rubis[-1]
            bare[-1] = .66*bare[-1]
            oxalis[-1] = .5*oxalis[-1]
            rubis[-1] = .5*rubis[-1]

        i = i + 1

    gapArray = np.array(gap)        # converting lists to arrays for plotting
    bareArray = np.array(bare)
    oxalisArray = np.array(oxalis)
    rubisArray = np.array(rubis)

    plt.plot(range(1,endYr+2), gapArray, label="Gap")       # plotting data
    plt.plot(range(1,endYr+2), bareArray, label="Bare")
    plt.plot(range(1,endYr+2), oxalisArray, label="Oxalis")
    plt.plot(range(1,endYr+2), rubisArray, label="Rubis")
    plt.title("Forest floor cover")
    plt.xlabel("Time (years)")
    plt.ylabel("Ground cover (%)")
    plt.legend()        # there is some kind of error with showing the plot. Idk what it is...
    plt.show()
```

Running `succession(400,0.01)` yields...

![[forest_floor_dynamics.png]]

As we can see, a system of only four species with one possible disturbance event can cause quite complex and non-linear patterns to emerge!

This model is of course very simplistic. It has fire occur as a random event every so many years, when fire has its own patterns and events, as it is a function of many other environmental variables, such as precipitation, woody debris, etc. 

# Sources
*Ecology, Fourth Edition* by Bowman, Hacker, and Cain (2018)