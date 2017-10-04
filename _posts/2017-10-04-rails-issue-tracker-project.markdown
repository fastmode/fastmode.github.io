---
bg: "sorry-imkirk-261041.jpg"
layout: post
title:  Rails Issue Tracker
summary: "Keep track of all your Tickets and Issues"
date:   2017-10-04 12:01:00 -0400
categories: posts
tags: ['full-stack', 'projects']
author: fastmode
---

I have just completed building the Rails Issue Tracker application.  This is a huge submission to complete the Ruby on Rails section for Flatiron School.  This project really pushed me to my limits and forced me to try many new things, troubleshoot a ton, and practice calmness to not throw my keyboard at something.  All joking aside, this was a truly amazing experience where I realized that I have actually learned a ton of new skills and I can actually meet the requirements for these final projects.

I chose to build Rails Issue Tracker to meet a gap I experienced with software tools in my previous career in Information Technology.  I never really had an easy, intuitive tool that would help me track Tickets and Issues.  This application makes it very easy to track these items.  The application allows a user to create a parent Ticket item and subsequently add unlimited children Issues to it.  The Ticket items allow the user to indicate Due Dates and Status.  Once one creates a Ticket, they can create Issues which contain more granualar data.  This data includes Description, Due Date, Status, and who it is Assigned To.  With this information, the user can accurately keep track of their ongoing Tickets.

The project was built using Ruby on Rails along with multiple gems.  For authentication, the application utilizes Devise and OmniAuth.  This allows a user to keep their Tickets secure and private.  The user has the ability to create a user account directly from the site by indicating a password.  The user may also opt to utilize Github for authentication, which is where OmniAuth kicks in.  

Rails Issue tracker is built to follow REST standards.  The application utilizes Nested Resources to accomplish this.  Issues are nested within Tickets.  This allows for RESTful URLs to display in the browser, for example '/tickets/1/issues/3'.  POST and GET commands are also pushed through these nested resources to allow the data to post and route to correct paths.  

Reports were also created which give the user more insight into their data.  When the user logs into their account, they are presented with a Dashboard that contains current Open Tickets.  They also have the option to click to view Overdue and Closed Tickets.  

The process to create this application followed the same as in the many other projecs created throughout the Rails Learn.co lessons.  I tried to always map out on paper how I would want my models to look and how the database tables would interact with each other.  Once I have a good draft on this, I can wrap my head around how it will be built and function.  Routes are created to allow the Controllers to interact with their Views. I tried to use the lowest overhead when utilizing Rails Generators, mostly keeping it to the creation of Models and Controllers.   My biggest struggles where in getting the Nested Resource to functions as designed.  I also struggled to get the Delete/Destroy functionality to work for a while.  

Finally, there is a lot more features that could be added to this application.  There is probably more refactoring that could be done and I will probably have more commits that do exactly that in the coming days.  Again, this application project really made me realize that there is still a ton to learn about Rails and programming in general.  But it also made me realize that putting in the work, researching misunderstood concepts, and keeping at it can truly help you build amazing things.  It has made me realize that I'm actually a developer now!

Hope you enjoy the application.  You can view a demo here:  [Video Demo](https://youtu.be/BesY6Pgm3HI)

Feel free to contribute and collaborate via the project's [Github](https://github.com/fastmode/rails-issue-tracker) page.  

