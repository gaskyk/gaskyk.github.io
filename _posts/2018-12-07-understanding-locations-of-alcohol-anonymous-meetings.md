---
layout: post
title:  "Understanding locations of Alcohol Anonymous meetings"
date:   2018-12-07 08:38:07 +0000
---
## Overview
 
As we know, the consumption of large volumes of alcohol can causes physical and emotional problems and alcoholism (at the extreme end) can lead to a wide variety of health and social issues.

Some data is collected about both the consumption of alcohol and the effects (such as hospital admissions), but I wondered whether there was a correlation between the number of Alcohol Anonymous (AA) meetings in an area and other indicators of alcohol misuse.
 
## Web scraping
 
All AA meetings are published on the AA website (insert hyperlink). Previously to do web scraping, I&#39;ve used the [beautiful soup](https://www.crummy.com/software/BeautifulSoup/) package in Python to get the html behind the pages I&#39;ve been interested in. However, the AA page is different in that a user first needs to interact with the page (by selecting an area, then pressing the search button) before the information about meetings is available.

This means that beautiful soup alone can't be used and that we need to use [selenium](https://www.seleniumhq.org/) to mimic this human interaction with the web page. Through doing this, I looped through all the geographic areas on the drop-down list to get information about each meeting in Great Britain such as its location, start time and day of the week. Sometimes information about the duration of the meeting is available.
 
## Comparing this with public health information
 
There is a wide variety of data from [Public Health England (PHE)](https://www.gov.uk/government/organisations/public-health-england) about many topics including alcohol. A lot of the data is available through PHE&#39;s fingertips tool online, or, usefully for a data scientist, also available through the [fingertipsR](https://cran.r-project.org/web/packages/fingertipsR/index.html) package. This package essentially calls the fingertips API and retrieves relevant data on specific indicators.

I explored the indicators and found 38 relating to alcohol. I had to do some data wrangling to:
- Import some data about the residential population in each area to calculate the number of AA meetings per 100,000 population
- Ensure that I only kept the most recent data for each indicator.

I found that none of the indicators had a particularly strong correlation with the location of AA meetings. The indicator which was most positively correlated (value of 0.33) was the rate (per 100,000) of adults in treatment at specialist alcohol misuse services, while the indicator which was most negatively correlated (value of -0.26) was the volume of pure alcohol sold through the off-trade (all alcohol sales).

Given that this didn't inform the location of AA meetings as much as I thought it might, I looked at other information about the meetings.

## Where are AA meetings?

![Map]({{% include aa_map.html %}})

<iframe src="{{% include aa_map.html %}}" width="640" height="480"></iframe>

It's clearer to see here that the number of AA meetings in an area appears to be strongly correlated with population density. In other words, there are more meetings per head of population in towns and cities. That makes sense as some people want to go to meetings before or after work, which may not necessarily be near where they live.

## When and how long are the meetings?

![Days of the week]({{site.url}}/assets/aa_Day_of_week.png)

As we can see, meetings are held every day of the week, with slightly fewer meetings at weekends.

![Times of the day]({{site.url}}/assets/aa_Start_time.png)

What is more interesting is that there is a small peak of meetings around lunchtime, while most of the meetings occur in the evening with the most popular start time being 8pm. There are also some very early meetings (6am in the City of London) and very late meetings (10.30pm in Glasgow and Edinburgh).

![Length of meetings]({{site.url}}/assets/aa_Duration.png)

Not every meeting contained information about its duration, but where it did the most popular lengths were 1.5 hours or 1 hour. It is unusual to have other durations.

## Get the code

My code is available on [Github](https://github.com/gaskyk/aa_meetings) and I always welcome comments or suggestions for improvements.
