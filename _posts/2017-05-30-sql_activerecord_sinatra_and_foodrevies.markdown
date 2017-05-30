---
bg: "goran-ivos-245581.jpg"
layout: post
title:  SQL, ActiveRecord, and Sinatra
summary: "Loving Sinatra and ActiveRecord"
date:   2017-05-30 11:01:00 -0400
categories: posts
tags: ['full-stack']
author: fastmode
---

Its been a while since I have updated that blog.  I have continued working hard toward the completion of the Learn program.  There have of course been very highs and lows, times where some concepts were very hard to understand and wrap my head around.  I have found that asking people for help goes a long way and for any code issue, there are many different ways you can resolve it.  I find this very intriguing, at times it can tell you how different people think through issues as they express it via code.  I hope to continue learning as much as possible and to continue reaching out to others to either learn or help them learn a concept.  

Since my last entry, I have now reached another milestone in my Learn track.  I have now completed my Sinatra project.  Getting here was no walk in the park.  In the process I had to learn all about SQL, ORMs, ActiveRecord, Rack, and Sinatra.  This was a lot of material to digest but I have actually enjoyed the process.  

SQL made a lot of sense to me and I truly enjoyed learning how each table can be and should be relational to the other.  This goes such a long way in helping structure how an application will be able to persist and extract data.  I liked how the Learn curriculum made me learn all about writing Ruby models and connectors to interact with the SQL databases.  The fun part was that right after finishing the SQL track, you learn all about ORMs which pretty much make writing your own database methods obsolete.  ORMs or ActiveRecord in this case are almost magical.  The ability to just inherit methods, create your own migration files, indicate what relationship each table will have with the other via models, makes this such a powerful tool.

Finally, I jumped into the world of Rack.  Essentially this is the base platform that Sinatra and Ruby on Rails run on.  In this case, I dove into Sinatra to learn the capabilities it offers.  This has been my first time working in a MVC, Model/View/Controller, environment.  Once you fully understand this framework, you just get a feel of how modular and flexible it is.  One can get a web application up and running pretty easily. 

One of the final projects was to create a Twitter clone we have named Fwitter.  This took everything I had learned and setup the challend to build this CRUD (Create, Read, Update, Delete) application.  The web application is pretty similar to the core functionality of Twitter without all the bells and whistles.  It lets a user create or log into their account.  Then they can create a new tweet, edit or delete and existing, and read theirs and others existing tweets.  I went one step further and put it up on Heroku to have it up and running outside my local computer build.  

The application is live here:  [Fwitter](https://fwitter-arturo.herokuapp.com/)
The Github repository is here: [https://github.com/fastmode/sinatra-fwitter-group-project-v-000](https://github.com/fastmode/sinatra-fwitter-group-project-v-000)

To finalize the Sinatra section of my curriculum, I now have to create my own entire web application.  I have a few ideas of what to build, but I think I'm going to do a Food/Dish review site.  This site will allow users to login and document the food they ate.  Stay tuned for when that is released! 



