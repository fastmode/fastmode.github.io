---
bg: "boderwait.png"
layout: post
title:  "On Scraping, Object Orientated Ruby, and Border Waits"
summary: "How long will I wait in line?!"
date:  2017-03-17 07:11:13 -0400
categories: posts
tags: ['full-stack', 'projects']
author: fastmode
permalink:  on_scraping_object_orientated_ruby_and_border_waits
---

My journey through Flatiron School's Learn program continues.  So far, Object Oriented Ruby has been the more challenging concept to understand.  At this point, I finally have a good grasp of the fundamentals and some additional skills that allow me to create effective and functional applications.  One of the hardest concepts to understand is that you can abstract pretty much everything into an object.  By turning items into objects in programming, you are provided with tools that let you collect data, iterate through it, and present specific data you need.   By using the tools taught in the Object Oriented portion of the curriculum, I now feel confident in using these skills.  

Scraping (or web scraping) is a technique used to extract data from websites by pulling information directly from the HTML code.  Tools like Open-URI and Nokogiri make the collection of this data very easy.  Although identifying and finding the correct data you want to extract can be challenging, once you are able to pull that data, you can use Object Oriented practices to make it functional.

I decided to use the OO Ruby and Scraping to build simple Command Line Interface (CLI) program to pull information from the US Border Patrol Wait Times website.  This can be used to quickly see current wait times at all US ports of entry along the Canadian and Mexican borders.  I grew up in the border town of San Luis, AZ, and I remember one of the main deciding factors for going into Mexico was how long would we have to wait in line to cross back into the US.  Using the program, the traveler can be better informed prior to making their travel into Canada or Mexico.

The program is pretty straight forward.  Once you launch it, you have four options.  The first two options are to pick between a list of ports in the Canadian or Mexican borders.  You will then be asked to select one of the ports which will provide you with details on that particular port.  The details contain information about each particluar port, including port status, hours, last updated time, commercial, passenger, and pedestrian lane informationa and wait times.  Third is to see a list of all ports with details.  Finally, fourth is to exit the program.

You can review, collaborate and provide feedback to the code by navigating over to the Border Wait repo at: https://github.com/fastmode/border_wait

While building this program, I felt empowered knowing I was building a tool that many people would benefit from.  It was great to know I was creating something.  I feel learning OO Ruby and Scraping have cleared some of the doubts I had about whether I could learn how to code.  I feel like I'm on a great path.  Next up is SQL!


