---
layout: single
title:  "Tips for aspiring data scientists"
date:   2017-11-13 08:38:07 +0000
---
There are often tales in the press discussing the need for data
scientists in business, government and the voluntary sector, and the
scarcity of such people which pushes up average salaries in the sector.
According to [GlassDoor](https://www.glassdoor.co.uk/Salaries/index.htm)
the average data scientist salary in the UK is £42,000 (at the time of
writing), with much higher salaries in London. This is leading to people
converting to data science or undertaking courses in the subject. I
thought it might be helpful for me to give some tips about how I became
a data scientist given my background in statistics and maths.

There seem to be two broad routes to becoming a data scientist:

-   Doing a masters or conversion course. This is the more expensive
    route and in the case of a Masters (which are increasingly being
    offered by universities) will take at least a year. Conversion
    courses (such as offered by [Step
    Function](https://stepfunctioncoaching.co.uk/) can take six
    weeks full-time) but can be costly

-   Learning by yourself. This is the cheapest route and in most cases
    is free as long as you have a computer. But it can be confusing to
    know where to start, to keep motivated and to find a community to
    chat with if you get stuck. This is the bit I’ll talk about during
    the rest of this piece.

## Learn by doing

Sounds simple doesn’t it? But where on earth to start? Monica Rogati, a
data science advisor in the USA came up with [this excellent
summary](https://medium.com/@mrogati/how-do-i-become-a-data-scientist-f8074232608e).
I won’t repeat it here but essentially it involves choosing a topic
you’re passionate about, finding some data, analysing it then
summarising what you’ve found and why it’s important. I think this is a
brilliant idea as you’ll then learn the data science skills you need,
when you need them.

## Free online courses

There are a plethora of free online courses offered by
[Coursera](https://www.coursera.org/), [EdX](https://www.edx.org/),
[Udacity](https://www.udacity.com/) and others. Often people start by
thinking about where they can learn R or Python as this is the gateway
to exploring other subjects such as machine learning or web scraping.
The ones I’ve done and would recommend are:

-   [CodeSchool for R](https://www.codeschool.com/courses/try-r). This
    can be done in the browser at one's own pace

-   [CodeAcademy for
    Python](https://www.codecademy.com/learn/learn-python). Again this
    can be done on the browser at one’s own pace

-   [Programming for Everybody for
    Python](https://www.coursera.org/learn/python). This
    course runs for 7
    weeks with 2-4 hours of study per week

## Moving on from learning R and Python

Over time I learned R and Python and tried to apply them and try other
data science techniques on projects I was already doing at work. I was
lucky that (1) I worked in an analytical role where I already had access
to data and (2) my employer was keen for employees to upskill in data
science. For example:

-   I had access to some small scale data from electricity smart meters
    where people had opted in to supplying this data (for example open
    data from
    [data.gov.uk](https://data.gov.uk/dataset/energy-consumption-for-selected-bristol-buildings-from-smart-meters-by-half-hour)).
    I used R to analyse and visualise it, then wondered what would
    happen if you had a lot of smart meter data. I scaled up the data to
    try to find the point at which R would break (as it typically holds
    data in memory), then thought about how else I could deal with
    analysing a larger volume of data

-   I discovered that there was an Application Programming
    Interface (API) for collecting a small amount of data about
    properties for sale or rent from [Zoopla](https://www.zoopla.co.uk/)
    and thought this might be useful for a work project. I’d never used
    an API before so found out how to do this online, then tried using
    machine learning (which I had also never done before) to predict
    what properties are likely to be caravan homes (using information
    about the property’s price, number of bedrooms etc.) I have the code
    for that project [here](https://github.com/gaskyk/housing-websites).

## Finding a community to learn from

I was lucky in that there were a number of people in my team who were
learning data science at the same time, so we were able to share our
successes and frustrations as we went along. If you’re not in that
position, I think the following would be helpful:

-   [Becoming a data scientist](https://www.becomingadatascientist.com/)
    is a website set up by Renee Teate in the USA who was trying to
    become a data scientist. She interviews data scientists for her
    podcast, bookmarks useful articles and her community rate online
    courses they’ve done

-   [Kaggle](https://www.kaggle.com) provides data and is a competition
    website where you can compete to build the best machine
    learning algorithms. There is also a helpful
    [tutorial](https://www.kaggle.com/c/titanic) on using one of their
    datasets (about survivors on the Titanic) to learn machine learning
    basics using R or Python and the community seem friendly and keen to
    help each other

-   Meet people in person. There are
    [meetups](https://www.meetup.com/find/tech/) in larger cities,
    particularly London, on different aspects of data science

-   Attend a hackathon. I went to a hackathon organised by
    [DataKind](http://www.datakind.org/chapters/datakind-uk), which
    pairs data scientists with charities needing data science skills.
    Although intimidating at first as I presumed everyone would be
    super-clever and experienced data scientists, I actually found that
    people had a wide variety of skills and with my statistical and
    coding experience, I fitted in well.

Many people come in to data science from many different fields and
avenues, but I hope that sharing at least a bit of my experience will be
useful for someone else.
