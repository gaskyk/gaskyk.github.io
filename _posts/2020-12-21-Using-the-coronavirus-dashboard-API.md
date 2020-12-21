---
layout: single
title:  "Using the coronavirus dashboard API"
date:   2020-12-21 08:38:07 +0000
---

During the course of this COVID-19 pandemic statistics and data have shown their huge importance in society. Members of the public have become armchair statisticians, passing comment on the latest rates and using phrases such as &quot;flatten the curve&quot;.

## The coronavirus dashboard

The government has also become much better at publishing statistics, and the go-to place to find out what is happening in your area is [Public Health England&#39;s coronavirus dashboard](https://coronavirus.data.gov.uk/). This is updated daily with data on testing, cases, hospital admissions and deaths. It will soon incorporate data about vaccinations undertaken.

![Screenshot of coronavirus dashboard front page]({{site.url}}/assets/covid_frontpage.png)

## About the dashboard&#39;s API

As part of this, an Application Programming Interface (API) has been developed so that people can automatically download the latest data programmatically, possibly incorporating the latest data into a web page or app. Building an API for such important information is best practice, especially at this time. Packages have been developed for R, Python and javascript so that developers don&#39;t need to build their own package from scratch.

I have used the [R package](https://github.com/publichealthengland/coronavirus-dashboard-api-R-sdk), ukcovid19, to develop an [R Shiny app](https://gaskyk.shinyapps.io/covid_area/) to compare local areas case rates with the national rate.

<embed src="https://gaskyk.shinyapps.io/covid_area/" width="640" height="480">

## Some comments on the API

There is a lot of information about [how to use the API](https://coronavirus.data.gov.uk/details/developers-guide). The R, Python and javascript packages also incorporate functions that would be a faff to implement yourself, such as ensuring that all the requested data is returned in one go.

There are also elements of the API which could be improved, for example not all data is available for all geographical areas but it is not clear which data is available for which area types, unless you iterate through all possible combinations. In addition, there is now a &#39;download data&#39; tab which contains more data for manual download than is available in the API (for example, data by Middle Layer Super Output Area, a geography containing between 5,000 and 7,500 people).

However, overall I am still impressed that this data is available by API, and impressed at the [openness of the team](https://twitter.com/Pouriaaa) building the API to comments and suggestions on Twitter.

## Get the code

As ever, my code is available on [Github](https://github.com/gaskyk/covid_area) and I always welcome comments or suggestions for improvements.