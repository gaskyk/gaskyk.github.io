---
layout: single
title:  "Footfall in York city centre"
date:   2018-12-14 08:38:07 +0000
---
## Overview

Footfall information counts the number of people (typically in shopping centres) who walk past particular cameras over a period of time. It shows how busy an area is over a period of time and is used by retailers to help them consider where to put their stores, store opening hours and how many staff they need.

[Open data](https://data.gov.uk/dataset/6449d8f5-76e7-4aff-bfb1-46d46542a56c/footfall) showing hourly footfall from several cameras in York city centre every hour from 2009 until late in 2018 is available. This seemed fun so I downloaded it and had a play with what it showed.

## Average Saturday footfall peaks at 2pm

I generated a map showing the four camera locations and footfall every hour during an average Saturday in 2018:

![Average footfall on a Saturday in 2018]({{site.url}}/assets/York_footfall.gif)

It is unsurprising that Saturday is the busiest day of the week in York. It can also be seen that footfall peaks earlier (at midday or 1pm) on weekdays than at weekends (at 2pm).

![Average weekly footfall in 2018]({{site.url}}/assets/Footfall_Hour_weekday_2018.png)

## Footfall started decreasing in 2013 but has risen more recently

![Average monthly footfall between 2009 and 2018]({{site.url}}/assets/Footfall_Average_year_monthly.png)

It is interesting to note the temporal pattern in monthly footfall, with expected increases towards the end of the year peak in Christmas shopping. We can also see that footfall began decreasing in 2013 with an upturn in recent years. I wondered whether there was a change in the location of footfall cameras which might account for these changes but this doesn&#39;t appear to be the case given the graph below.

![Average annual footfall by location]({{site.url}}/assets/Footfall_Average_yearly_location.png)

I realise that this is a &quot;quick and dirty&quot; analysis of the data available and clearly much more could be done to fully analyse the data, including the different temporal patterns. Indeed, I expect I will return to it to explore some of these methods further.

## Get the code

My code so far is available on [Github](https://github.com/gaskyk/footfall) and I always welcome comments or suggestions for improvements.
