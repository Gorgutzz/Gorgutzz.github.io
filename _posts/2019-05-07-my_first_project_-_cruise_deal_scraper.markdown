---
layout: post
title:      "My First Project - Cruise Deal Scraper"
date:       2019-05-07 18:07:09 -0400
permalink:  first_project
---


The first project required to program a CLI Data Gem. I used the resources that were provided in the project to get and idea of how to structure my gem.My idea was to scrape a site for cruise deals which had different cruise deal categories ranging from cheap to last minute deals. In addition to other variables like ship name, port name, number of nights etc, there was a cool itinerary that showed all the stops the ship would make on its voyage. I thought it would be useful to display an additional itinerary to the data already provided.

Using the structure of the video and the example project, I got an idea of how I want to structure my CLI. After trial and error I got the application working where it was succesfully scraping the correct fields using nokogiri and XPath. It took quite a while to clean up the look of the CLI in the terminal due to spacing issues from the content I scraped. The content I scraped had whitespace before every string. I looked for various ways to remove the whitespaces (which turned out to be quite simple). Through my research I find out about [lstrip](https://ruby-doc.org/core-2.2.0/String.html#method-i-lstrip) and [gsub](https://ruby-doc.org/core-2.1.4/String.html#method-i-gsub
). I also had to add `\n` in the CLI.rb file in various output statements to format the itinerary output properly.

Here is how the code turned out for the scraper paths: ![](https://i.imgur.com/nuJasgG.jpg)

I was quite satisfied with my gem when I applied these fixes. This was quite a fun project to do as it challenged me. I got to learn more about classes and scraping html which is very useful to collect data.

- Leo






