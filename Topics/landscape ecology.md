# ESCI 435: Landscape Ecology
`TAGS:`

---

Landscape ecology is fundamentally about the spatial structure of the [[environmental science|environment]]. 

Vegitation gradient analysis is a way to model vegetation patterns through sampling, and relate these patterns to abiotic factors that are a result of this template. [[remote sensing]] is essential for this sort of stuff. Common patterns include temp as a function of elevation, and moisture as a function of aspect (slope). 

## The physical template
Big factors here include temperature, moisture, and soil composition. The physical template of the landscape leaves an impression on the biotic factors that populate the landscape. For instance, trees must form structures to support themselves on soil, and in relation to the slope and abiotic conditions. 

There are lots of variables that are a part of the physical template...

### Temperature as a variable
Temperature varies with elevation strongly (-). It also varies with topography due to radiation and cool-air flows. 

### Radiation
Radiation varies with elevation(+) and topography. Slopes facing southwest tend to get the most radiation, and radiation increases with altitude. 

### Precipitation
Varies with elevation, topography. 

### Catena model of soils
Erosion moves soil downhill. This brings clay, organics, nutrients, and water downhill over time. 

### Water balance
Available water is a function of supply minus demand. 

Supply is a function of input of water, and water stored. 

$$available \ water \ (W_a) = supply(W_s) - demand(W_d)$$

$$
W_s = input(I) + storage(S)
$$

$$
S = precipitation(P) + drainage(D)
$$

$$
P = rain(R) + snowmelt(S_n)
$$

$$
W_d = f(temp(T),radiation(R),vapor \ pressure \ deficit(Vpd)
$$

Therefore...

$W_a=(I+R+S_n+D)-(f(temp(T),radiation(R),vapor pressure deficit(Vpd)))$

You can see how this gets complicated. 

By proxy, we assume water balance to just be a function of terrain. 

### Proxies for radiation
We can use slope aspect or surface area. We can also do a process called analytic hillshading with [[remote sensing]]. 

### Why not measure soil moisture?
It's too damn complicated! 

### Measuring drainage
We measure drainage using this equation.

$$
TCI = ln(\frac{A}{tan(b)})
$$
Where A is upslope area, b is local slope angle, and TCI is topographic convergence index. 

## Biotic processes
Tundra bushes develop a positive feedback loop through increasing snow depth. This depth causes soil temp to rise, bacterial activity, and therefore more available N, and more growth for the bush, causing more snow to develop, etc. 

Sucession: the process of new generations of life taking the place of the old. 

### The unit pattern
This is the holy grail. We are searching for the full representation of the sucessional pattern with all phases visible. Ideally, this would be represented in the smallest possible area / time frame to see all phases play out to the full extent. 

This concept is the basis for space-for-time substitution. Using this process, we can examine multiple plots of an ecosystem and map out which phase each plot is in. Using this, we can examine the sucessional patterns of processes that could take more than a human lifetime to fully unfold. 

Watt was the first to come up with these ideas. His ideas imply two levels to a forest ecosystem. At the small scale, there is a lot of noise and continual dynamics happening. But at a larger scale, these dynamics cancel each other out and more stable patterns emerge. 

Early sucessional species tend to have short lifespans and high growth rates. Later-sucessional ones tend to live longer. 

### Dispersal
Organisms disperse across the landscape according to a combination of environmental factors like wind and slope, and according to their evolved method of reproduction. 

If dispersal is density-dependent, it will create waves of new growth. 

## Disturbance
A disturbance is a discrete event that causes a disruption in the environmental conditions of a system. Examples are wildfires, floods, etc. Depending on how we define the system, the disturbance could come from outside or inside the system. 

### Disturbance in the White Mountains of NH
![fir waves](https://upload.wikimedia.org/wikipedia/commons/7/72/Fir_waves.jpg)
There are repeating waves of fir trees, almost in a rippling pattern. Why? 

This is caused by an interaction between wind and pathogenic fungi that live on the pine trees. The fungi kills the trees, and tends to spread in the downwind direction, because that's how the spores move around. In the spaces where the trees are now dead, the fir find it easiest to colonize the dead-zone. The spruce are later in the sucessional stage of the forest. 

---
## Correlation
Moran's I is a measure of autocorrelation (correlation of a variable to itself). Autocorrelation basically measures if there is a pattern as opposed to a random distribution of something, a species for example. 

Autocorrelation is defined with this equation.

$$
r_x = \frac{\sum_i
		{\sum_j{(x_i-\bar{x})(x_j-\bar{x})/(n-1)}
		
	   }}{s^2}
$$
We measure the correlation of a variable with itself based on distance between sample sites. 

Using Moran's I, we can create a corrallelogram that tells us the scale of patterns in the landscape. We plot Moran's I against distance. The autocorrelation will decrease as distance between sampling sites increases. By looking at how this curve decreases, we can see the scale on which the landscape pattern exists. 

For more on correlation in general, see [[covariance and correlation]]. 

### Grain and extent
Grain is the smallest possible unit we can measure in a study area. Basically it's the pixel size in the image we're looking at. Extent is the size of the study area.

Grain size increases as extent increases because of logistical issues usually. 

## Scale
The issue of scale is the most important issue in ecology.

As scale increases, 
- Small-scale variables become constants
- Constants become variables
- New processes emerge

While processes generally remain similar between scales, the variables at play in these processes change a lot. 

### Inference
We can't really prove that something is going on, we can only disprove stuff. With landscapes, we can't really run traditional experiments, so we have to model their behavior instead. 

## Models
### Neutral models
We don't fully understand models, so we can use "unnatural" models to compare landscapes to to see their patterns in contrast. An example of this would be a neutral model. 

### Percolation theory
This is a kind of neutral model, used to look at connectivity and patchiness. As percent land cover of a variable increases, the number of patches first increases, and then decreases as connectivity reduces the raw number of patches. 

### Graph theory
This model is made up of nodes and edges (connections). The nodes have properties that are transmitted through the connections and alter neighboring nodes. 

## Effects of habitat loss
Patch size decreases, edge size increases. Patch distance increases. 

