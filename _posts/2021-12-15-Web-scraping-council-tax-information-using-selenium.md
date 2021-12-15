---
layout: single
title:  "Web scraping council tax information using selenium"
date:   2021-12-15 08:38:07 +0000
---


We recently moved house and a casual check of the council band for our house revealed that we&#39;re in a higher council tax band than our neighbours, despite living in a house of similar size. To correct this we need to put a case to the Valuation Office Agency (VOA) showing houses of similar size and age but in a different band. Unfortunately for us, this isn&#39;t as simple as just comparing to our neighbours houses as their homes were built in the 1950s (and have had significant extensions and renovations since then), while ours was knocked down and rebuilt in 2011 so according to the VOA these aren&#39;t comparable. In order to collect the information about council tax bands and ages of properties, we need to web scrape the [VOA website](https://www.tax.service.gov.uk/check-council-tax-band/search).

## Why selenium?

To search for council tax bands of properties you first need to search by postcode or street and town or &quot;advanced&quot; (for example the unique property reference number or property name). This provides a list of addresses, which need to be clicked on to see the required information. The python package [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) can be used to extract required information from a static website but if you need to enter information (such as a postcode) or click on any buttons (such as &quot;Search&quot;), this can&#39;t be done in Beautiful Soup and [selenium](https://selenium-python.readthedocs.io/) is required.

## How selenium works

Selenium works by launching the Chrome web browser and entering information or clicking items such as buttons or drop-down menus, then closing the browser. The entering of information and clicking is done programmatically, allowing us to collect a lot of information in a short period of time. [ChromeDriver](https://chromedriver.chromium.org/downloads) must be downloaded for selenium to work and its location on your computer specified in the code. Once on the required page, Beautiful Soup can be used to extract the elements needed.

For example, I used selenium to enter a postcode and click the &quot;Search&quot; button by using

	postcode = "SW1A 0AA"
	driver.find_element_by_id("postcode").send_keys(postcode)
	driver.find_element_by_id("submitsearch3").click()

I then used Beautiful Soup to extract information such as the council tax band

	page = requests.get(url)
	soup = BeautifulSoup(page.content, 'html.parser')
	
	# dd is the HTML tag used to show the information we want to collect
	other_tag = soup.find_all("dd")

	# Council tax band
	council_band = other_tag[2].get_text().title()
	council_band = council_band.strip("\n").strip(" ").strip("\n")

## What the code does

There are four functions in the code. They:

1. Collect council tax information from individual property URLs
2. Collect a list of property URLs through a search of a single postcode
3. Collect council tax information from individual postcodes, by iterating over the property URLs generated from (2) and applying the function from (1)
4. Collect council tax information from a list of postcodes by applying the function in (3) over a list of postcodes. This saves the council tax information in a CSV file for all the properties in that list of postcodes.

I collected a list of postcodes for the area I&#39;m interested in from the [Open Geography Portal](https://geoportal.statistics.gov.uk/).

## Next steps

Now that I have collected this information, I need to filter it down to properties of a similar age to mine, but in a lower council tax band to understand whether we have a sufficiently strong case to put to the VOA.

## Get the code

As ever, my code is available on [Github](https://github.com/gaskyk/council_tax) and I always welcome comments or suggestions for improvements.