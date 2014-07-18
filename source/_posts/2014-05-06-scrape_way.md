---
title: Scrape data the right way Part:1
date: 2014-05-06
tags: [notes]
description: My experience on how to scrape data from web.
---
There is frequently a need to scrape data. Obviously, Python is a good choice for this. The famous libraries like [BeautifulSoup][bs] provides a bunch of functions to do these stuffs. But personally, I prefer [lxml][lxml].
## Why lxml
There already has some [comparison][cp] about pros and cons of each library. As [lxml document] said:
> BeautifulSoup uses a different parsing approach. It is not a real HTML parser but uses regular expressions to dive through tag soup. It is therefore more forgiving in some cases and less good in others. It is not uncommon that lxml/libxml2 parses and fixes broken HTML better, but BeautifulSoup has superior support for encoding detection. **It very much depends on the input which parser works better.**
... ...
The downside of using this parser is that it is **much slower than** the HTML parser of lxml. **So if performance matters, you might want to consider using soupparser only as a fallback for certain cases.**

In short: lxml is faster when parsing well-formed web page.

## Example: Grab data from Craglist
This is a common scenario. First get links of each entries in a `index` page.

For example, find all housing in [http://losangeles.craigslist.org/hhh/index.html](http://losangeles.craigslist.org/hhh/index.html). In Chrome, Inspect Element, get XPath link from one link:
![](http://i.imgur.com/M5twZ1U.png)



The xpath is `/*[@id="toc_rows"]/div[2]/p[1]/span[2]/a/@href`, from p[1] to p[100]. Save these links to a file `crag_link.txt`. 


    from lxml import html
    import requests
     
    with open('crag_link.txt', 'a') as f:
        for i in range(0, 1000, 100):
            pg = 'http://losangeles.craigslist.org/hhh/index' + str(i) + '.html'
            src = requests.get(pg)
            if src.status_code == 404:
                sys.exit(1)
            tree = html.fromstring(src.text)
            print 'Get page', i
            for j in range(1, 100+1):
                x_link = '//*[@id="toc_rows"]/div[2]/p[' + str(j) + ']/span[2]/a/@href'
                links = tree.xpath(x_link)
                for ln in links:
                    f.write( 'http://losangeles.craigslist.org' + ln + '\n')
            
        f.close()

Click into one of the page, for instance, we want to get post id, copy xpath 
like `//*[@id="pagecontainer"]/section/section[2]/div[2]/p[1]`. According to [XPath syntax][xpath], these path add suffix `/text()` is what we need.


    try:
        post_id = tree.xpath('//*[@id="pagecontainer"]/section/section[2]/div[2]/p[1]/text()')
    except:
        # Handle Error

The reason we add try/catch block here is to prevent missing data. Wait a second, what if we have 30 attribute to scrape, do we need to write try/catch 30 times. Definitely no. Wrap them into a function might be a good idea. BTW, hardcode xpath into program is not a good idea, by writing a function, we can pass it as a parameter(Or even better, store attribute names and xpaths in a dictionary).


    def get_attr(tree, xps):
        return attr_name = tree.xpath(xps)
     
    ''' 
    xps_dict look like: 
	{'post_id':'//*<somehing>/p[1]/text()','post_time':'//*<somehing>/p[1]/text()'}
	'''
    for a, x in xps_dict.iteritems():
        attr[a] = get_attr(tree, x)


For the Part 2, I will carry on, talk about encoding problem, prevent duplicates and so forth.

[scrapy]: http://scrapy.org/
[bs]: http://www.crummy.com/software/BeautifulSoup/
[lxml]: http://lxml.de/
[cp]: http://stackoverflow.com/questions/4967103/beautifulsoup-and-lxml-html-what-to-prefer#
[lxml document]: http://lxml.de/elementsoup.html
[web scrape]: http://docs.python-guide.org/en/latest/scenarios/scrape/
[xpath]: http://www.w3.org/TR/xpath/
