---
layout: single
title:  "Name that baby (with the help of R Shiny)"
date:   2020-05-06 08:38:07 +0000
---

I&#39;m pregnant and one of the fun things to do during pregnancy is to think about possible names for your baby. Sure, there are loads of apps out there for looking at this kind of thing including the popular, Tinder-inspired app [babyname](https://babyname-app.com/). But if you&#39;re a data scientist, you might want to look at this in a more analytical light.

## The data

For some of the apps, it&#39;s unclear what data they use. The most comprehensive baby name data in England and Wales comes from the [Office for National Statistics](https://www.ons.gov.uk/peoplepopulationandcommunity/birthsdeathsandmarriages/livebirths/bulletins/babynamesenglandandwales/previousReleases) in what is their most popular annual statistical product. As well as analysing the most popular boys and girls names, they also look at the [influence of popular culture on the naming of babies](https://www.ons.gov.uk/peoplepopulationandcommunity/birthsdeathsandmarriages/livebirths/articles/10popcultureinfluencesonbabynamesgameofthronesmarvelfrozenandmore/2015-08-17).

I have downloaded their 2019 [baby girl names data](https://www.ons.gov.uk/peoplepopulationandcommunity/birthsdeathsandmarriages/livebirths/datasets/babynamesenglandandwalesbabynamesstatisticsgirls) which includes the first names of baby girls born in 2019, where those counts are three or more.

The data, as downloaded, is an excel file with various sheets showing different cuts of the data. I have used Table 6, showing all the names. Currently the data is shown in ranked order, with the most popular name first, but for my purpose I would like to show the data differently.

## Choosing a name

In choosing a name, we would like to look at these names more systematically, but wouldn&#39;t like our daughter to have one of the most popular names, in say the top 20. We decided that we would like to look at the data by initial (so we can look systematically), and by rank, so that we can exclude those very popular names.

## Using R Shiny

It has been a while since I played around with R Shiny, but thankfully the [official R Shiny website](https://shiny.rstudio.com/) is full of useful tutorials and tips on getting started. I know others&#39; style of learning comes from books, from online videos or courses, but my style favourite learning style is to try to do something then learn the skills I need in the process. So I adapted the code from one of the simple tutorials on the website, then hacked around with errors and Google until it showed what I wanted.

So I have taken the original data, then

- Added a column to show the initial of the name
- Grouped the data by initial
- Took the first 100 rows by initial (which excludes some of the more obscure and least popular names)
- Then show the data in a table in descending rank

Here is part of that code:

```
# Read in baby girl name data
# 2019 data currently used
# Source: https://www.ons.gov.uk/peoplepopulationandcommunity/birthsdeathsandmarriages/livebirths/datasets/babynamesenglandandwalesbabynamesstatisticsgirls
names <- readr::read_csv("babygirlnames2019.csv")

# Create column for initial
names <- names %>%
	mutate(Initial = stringr::str_extract(Name, "^.{1}"))

# Keep only top 100 names per initial
# Often more than 100 are kept if these all have the same count
top_names <- names %>%
	group_by(Initial) %>%
	top_n(n = 100, wt = -Rank) %>%
	ungroup()
```

## Using shinyapps.io

We wanted to be able to see the information at any time, including when we are not using R, so a natural choice was to use [shinyapps.io](https://www.shinyapps.io/). This allows you to upload your R Shiny app for free, as long as you&#39;re not a heavy user, so you can upload up to 5 apps and have up to 25 hours of use per month. I haven&#39;t used shinyapps.io before but was pleasantly surprised how easy the process was. After signing up I needed to run some code locally to upload it to the website but it talked me through exactly what code I needed to run.

## Full R Shiny app

And this is [the result!](https://gaskyk.shinyapps.io/baby_names/)

<embed src="https://gaskyk.shinyapps.io/baby_names/" width="640" height="480">


We are looking forward to browsing this in the evening to help narrow down our choices!

## Get the code

My code is available on [Github](https://github.com/gaskyk/baby_names) and I always welcome comments or suggestions for improvements.

[Post updated on 27 August 2020 as a result of publication of the 2019 data]
