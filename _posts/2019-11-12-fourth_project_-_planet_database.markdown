---
layout: post
title:      "Fourth Project - Planet Database"
date:       2019-11-13 03:43:47 +0000
permalink:  fourth_project_-_planet_database
---


For my fourth single page application JavaScript and Rails project, I decided to create a planetary database. The user can post create a star system and subsequently add planets (exo planets specifically as I seeded the database with recently discovered planets) with quite a few parameters. Since I do not have many model classes (having just the planet and star models) my rails backend is quite simple but the frontend is it got a bit complex and where I had some problems. 

The Javascript portion was problematic since it was my first project with JS and I had to think and rethink the way that my forms and event listeners should look like. I also took much longer than I thought because I encountered an issue where none of my seeded data was rendering on the web page which resulted me in just restarting and redoing what I did bit by bit to find the problem. Alas I didn't find what was wrong the first time around but had no issues after the second. As mentioned before, I did have to get use to the way forms are handled and the use of event listners to display data but I seem to prefer this method to the previous way of having all this in the views folder.

I did like that the html portion of this project would turn out not to be so clustered and in my view 'messy' as my previous projects since most of the code was generated in the JS component files. For example most of the code was in a container I called 'stars-data'  and it was represented on the html page in 3 simple lines, while in the star.js it contained almost everything as it was set to the container which had inside it a whole lot of funcitons. I also had to learn to use the console.logs as they helped debug as I was building more nested functions.

Another issue that took a while to fix was rendering the display of the newly added planets and appending to them the html structure I wanted. So I decided to make constants for all the parameters in my submitPlanet function have the same structure as the rendered seeded params are in renderStarBlock. It might not be the most elegant way to do it but it works The nature of all the nested functions inside the larger ones was also a bit daunting and took a while to figure out since they have to logically depend on each other.

Overall this was a good learning experience and I did like using a new language in addition to rails to build an appliaction. Of course there is still much to learn but this was a good learning base for future projects with JS. 


