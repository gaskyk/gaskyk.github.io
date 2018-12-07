---
layout: post
title:  "What I have learned from web scraping the Coast website"
date:   2017-12-14 08:38:07 +0000
categories: jekyll update
---
## Overview

Web scraping (the automatic collection of data from a website through programming code) is a commonly cited skill of a data scientist. Last year I was looking to develop these skills at the same time as wanting a new dress for an upcoming wedding. There was one particular dress I liked, made by Coast, so I decided to try to learn web scraping using the Coast website as a test.

## Previous experience

Although I hadn&#39;t done any web scraping before, I had collected data from APIs (Application Programming Interfaces), and I had done a couple of short courses on html and CSS through the [CodeAcademy website](https://www.codecademy.com/) for free. I think that knowing a little about html was very useful and would recommend others start with this before web scraping.

I then searched for online resources about how to learn web scraping. I&#39;m now unable to find the resource I used but there appear to be lots of other suggestions and resources online.

## Other options to writing code

I am aware that so-called &#39;point and click&#39; web scraping exists (such as through [import.io](https://www.import.io/)) which don&#39;t involve any programming, but I&#39;m a data scientist so I wanted to write code and find out how it all works.

## Ethical web scraping

In my learning I ensured that I was adhering to the [terms and conditions of the Coast website](https://www.coast-stores.com/page/legal) (as some websites don&#39;t allow web scraping). I also ensured that I was only collecting a minimal amount of information to ensure that I wasn&#39;t placing a heavy burden on the website. I think this is really important. There are other things that can be done such as respecting the [robots.txt](https://www.coast-stores.com/robots.txt) protocol (which lists what pages on a website you can&#39;t web scrape) and ensuring a specific time lapse (such as 5 seconds) between accessing different pages.

## The web scraping

I started by looking at a particular dress on the website and trying to programmatically obtain certain information about the dress (name, colour, price and stock availability for different sizes) by using the Python package Beautiful Soup and ascertaining which html tags were relevant for these different bits of information.

I then generalised this by picking up a list of urls (one for each dress) from the [Coast website dresses page](https://www.coast-stores.com/c/all-dresses) and iterated over the urls to get the relevant information for each dress, converted this to a pandas data frame and eventually outputted it to a csv file for analysis in R. I&#39;ve re-run this web scraping four times so now I have a time series of dresses from the website during 2016 and 2017. When I re-run it, I usually have to slightly update the code as the website has changed structure.

## Analysing the dresses information

I analysed a variety of information such as colours, stock availability and price, and have the following observations:

The average price of a dress on the website is between £100 and £200, but the median price is coming down over time

![Box plots of prices of dresses by date]({{site.url}}/assets/price_by_time.png)

An increasing number of dresses by size are either not in stock or have low stock over time. In this chart there is one count per dress / size so each dress is counted seven times (once for each of size 6, 8, 10, 12, 14, 16 and 18)

![Stock levels of dresses over time]({{site.url}}/assets/stock_by_time.png)

There&#39;s more chance of finding a dress having low stock or not being in stock in the smallest sizes (6 and 8) and the largest sizes (16 and 18). The middle sizes (10, 12 and 14) have the greatest stock availability

![Stock levels of dresses by size]({{site.url}}/assets/stock_by_size.png)

## Get the code

My code is available on [Github](https://github.com/gaskyk/coast-dresses) and I always welcome comments or suggestions for improvements.
