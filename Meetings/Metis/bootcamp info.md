# General info
My cohort ID is: onl21_ds5

# Standard schedule
The usual daily schedule for the bootcamp will be...

8:30 - Pair programming
10:30 - Lecture / Project time
12:30 - Lunch
1:30 - Afternoon session (varies)
4:30 - End of day

# Project proposal
My main idea is to use some kind of predictive model to calculate forest fire risk for a given property in the United States. 

## Data inputs
Off the top of my head, I would need
- Geographic location
	- Could use zipcode if we don't have anything better
- Surrounding land use
- Local precipitation
- Previous fire extents

### Data sources
I assume that an insurance company would have access to the location of the property, but that isn't guaranteed. We would definitley know the zipcode at least. 

I can get land use data for that zipcode from the [MRLC](https://www.mrlc.gov/) (Multi-resolution land use characteristics) consortium provided by the USGS. 

I feel like there must be a [[database]] somewhere of previous extents of forest fires, but that isn't guaranteed. 

Distance to population center could be approximated by the population density of the zipcode, or whatever proxy we're using for location. 
## Applications
A model like this would be very useful for fire prevention and that end of things, as well as for insurance reasons (much more lucrative). When setting rates for fire insurance, an insurance company would be very interested in how likely they would be to pay for a fire on that property. 

## Questions to ask
Could this model be generalized for all kinds of fires, or are urban fires less predictable?

`LINKS:` [[Metis]]