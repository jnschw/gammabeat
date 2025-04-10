---
author: Jürgen Schwarz
layout: post
title: San Francisco Crime 
categories: R, crime, San Francisco 
---

![San Francisco](/public/images/Death_to_stock_above_8.JPG) 
*Photo Credit: [DeathToTheStockPhoto](http://deathtostock.staging.wpengine.com/)*


Crime in San Francisco should reach a wider audience than statistical pyhsics 
since very popular actual TV crime series such as *Monk* or *The Mentalist* 
are located there. Unfortunately, the set locations are nowadays chosen 
close to the film studios (i.e. most scenes are taken in LA or elsewhere...), 
so that interested readers have to go back in TV history into the early 70s 
and watch *The streets of San Francisco* to get some non-fictional impressions.
I recommend the epsisode with the young Arnold Schwarzenegger (Season 5, 
epsiode 20 "Dead Lift") which shows one of the -- attention: spoiler! -- 
extremely rare crime event in a San Franciso park area.

<!-- more -->

### Exploratory Data Analysis

The dataset consists of crime reports from the *real* San Francisco 
Police Department's Crime Incident Reporting system, and is available 
either via the official San Francisco OpenData website

<https://data.sfgov.org/>

or through a Kaggle competition 

<https://www.kaggle.com/c/sf-crime>.

Kaggle provides a set of three files consisting of a traing data set, 
actually a *csv-file* with 878.049 entries between January 2003 and May 2015 
from all even weeks. A test set, which in turn contains the odd weeks. In the 
training data the following features are available:


 * __Dates__: Timestamp of the crime incident.
 * __Category__: Category of the incident. Also, this is the variable to 
predict in the Kaggle challenge. (This variable is available only in the 
training dataset.)
 * __Descript__: A short description of the incident. (This variable is 
available only in the training dataset.)
 * __DayOfWeek__: Day of the week when the incident occurred.
 * __PdDistrict__: Police Department District
 * __Resolution__: Outcome of the incident. (This variable is available 
only in the training dataset.)
 * __Address__: Address of the incident.
 * __X__: Longitude
 * __Y__: Latitude

The data is ordered by timestamp. As third file a template for submission 
is attached.


### Data preprocessing

A few outlier with implausible coordinates should be removed first. Then, 
date and time are smooshed together in a single timestamp. To turn 
those into coarser units of time, i.e. year, month, day, and hour, will 
hopefully give better insights on the temporal aspects of the data.



### Visualization

For visualization we first get a roadmap of San Francisco from OpenStreetMap 
and plot it.
![San Francisco roadmap](/public/images/sfmap1.jpeg)

Then we add the raw data to the map (which we now fetch from Stamen since a 
grey background shoud lead to a better readability).
![San Francisco roadmap](/public/images/sfmap2.jpeg)



### Crime categories

In 1930 the Uniform Crime Reporting (UCR) program to collect, compile and 
standardize data on police reports across the United States became 
operational. UCR reports are divided into Part One and Part Two offenses. 
The Part One offenses are the most serious offenses and the offenses most 
likely to be reported to police. The seven original Part One offenses are 
the violent crimes - criminal homicide, forcible rape, robbery, and 
aggravated assault - and the property crimes - burglary, larceny and motor 
vehicle theft. In 1979 arson was added to the Part One crimes.

Part Two offenses are less serious and, to a greater degree than Part One 
offenses, are often not reported to police. These are: simple assault,
curfew offenses and loitering, embezzlement, forgery and counterfeiting, 
disorderly conduct, driving under the influence, drug offenses, fraud, 
gambling, liquor offenses, offenses against the family, prostitution, 
public drunkenness, runaways, sex offenses, stolen property, vandalism, 
vagrancy, and weapons offenses.


![San Francisco crime categories](/public/images/sfcrimecat.jpeg)


Apart from the crime categories the dataset contains also non-criminal cases like
car trouble assists, vehicle accidents, and medical cases where security and medical 
assistance has been requested. To simplify a first analysis, we build four subsets 
reclassifying the data into higher-level categories:

violent crimes:

 * assault 
 * robbery 
 * kidnapping 
 * sex offenses forcible 
 * familiy offenses

property crimes:

 * arson 
 * burglary 
 * larceny/theft 
 * vehicle theft

drug crimes:

 * drug/narcotic 
 * drunkenness 
 * driving under the influence 
 * liquor laws

economic crimes:

 * fraud 
 * stolen property 
 * bribery 
 * embezzlement 
 * forgery/counterfeiting 
 * bad checks
