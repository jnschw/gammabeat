---
author: Jürgen Schwarz
layout: post
title: Statistical Physics of Crime
categories: R, statistical physics
bibliography: references.bib
---

Classical data mining algorithms often performs very poorly when applied to 
spatio-temporal data. Spatio-temporal datasets are typically embedded in 
continuous space, whereas classical datasets are often discrete samples (such 
as measurements or database transactions). One common assumption in 
classical statistics is that data samples are generated independently. For 
spatio-temporal data, however, this assumption is generally false, because 
such data tends to be highly self-correlated. In spatial statistics this 
tendency is called autocorrelation. Thus, specific methods are needed to 
analyze spatio-temporal patterns. 

<!-- more -->

A review on applications of modern statistical pyhsics in crime analytics 
by D'Orsogna and Perc attracted my interest on 
**spatial point pattern analysis**. Mathematically, point pattern analysis is 
the evaluation of the distribution of a set of points on a certain surface. 
The underlying point process is a probabilistic model for random scatterings 
of points on this space. A point process can take on only one of two possible 
values, indicating whether or not an event occurs at that time. 


![Spatial Patterns](/public/images/spatpattern.jpeg)


As the figure nicely shows, the distribution of crime is not random in time 
and space. Environmental, economic, political and sociological factors 
contribute to areas with different occurences and characteristics of crimes. 
A major spatial 
pattern is a _hotspot_, i.e. a spatially focused area with high crime rates. 
The use of hotspot maps is a common practice in visualizing the spatial 
distribution of crime events. These maps highlight areas with high 
concentrations of crime based on _kernel density estimations_. Kernel based 
density estimations are widely used in time series analysis since many machine 
learning techniques require information about the probabilities of events 
involving the data.


![Bandwidth](/public/images/bandwidth.jpeg)


The quality of a kernel estimate depends less on the shape of the kernel 
than on the value of its bandwidth _h_. The figure above shows the effect of 
different choices of _h_ for a Gaussian kernel.


Kernel methods are widely used to estimate the intensity function of a point 
process. The intensity function of a spatial point process describes how the 
expected number of events per unit area varies across the spatial region of 
interest.


A point process is called self-exciting if the occurrence of past points
makes the occurrence of future points more probable. Such processes can be 
found in many domains from seismology, computational neuroscience, finance, 
to social networks and criminology. As a typical application one would like 
to predict discrete events in time and space from the occurrence of past 
event series. Crime can be understood as such a self-exciting point process 
since every crime event may also trigger offspring 
events around the parent event. This leads to a dynamics of spatio-temporal 
crime patterns like birth and death of hotspots. The feature of excitability 
in point processes shows an interesting analogy with neural networks in 
computational neuroscience, which also studies excitable systems: bursting 
behavior. Burst firing is a phenomenon where periods of rapid spike trains 
are interrupted by quescient phases. 


