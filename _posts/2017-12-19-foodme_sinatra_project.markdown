---
layout: post
title:      "FoodMe Sinatra Project"
date:       2017-12-19 07:29:08 +0000
permalink:  foodme_sinatra_project
---


To complete the Sinatra section of the Flatiron Online Web Developer program, you must build your own web application. The requirements are that you build an MVC Sinatra Application. That you use ActiveRecord with Sinatra, use Multiple Models, which have at least one ‘has_many’ relationship. The application must also have user accounts which allows only entries created by that user to be changed or deleted. Finally, the user input should be validated to ensure bad data is not created.

It took me a while to decide what I was going to build my application on. After talking to a few of my friends, it was decided that they could always use an app they could track their favorite dishes on. This app would then allow them to share their page which contains all their favorite dishes. I decided I needed to build FoodMe!

FoodMe is a food review application that focuses primarily on the actual dish and not so much on the restaurant. Most other food review sites focus too much on the restaurant and its hard to find reviews on the actual dishes you are interested in. With FoodMe, you can focus on the dish you ate and provide your review on it. One can also see all the other reviews left from the entire FoodMe community. Lots of times, people will come into town and one of the main things they want to know is, “What can I eat around here?”. Now you can easily send them your profile page containing all the food dishes you have reviewed.

To use FoodMe, you navigate to the site and easily either log in or create a new account. You will be directed to your profile page containing your reviews. You then have the option to navigate to the All Reviews page where you can see all reviews. You can also click on the New Review to review a new dish. The New FoodMe Review page is loaded which allows you to enter information on the Dish Name, Dish Price, Restaurant Name and City, whether the dish is Vegetarian or Gluten-Free, and a textbox for your Review. Once you click on Submit, the review is saved to the database. If you want to edit or delete your entry, you simply click on the dish review entry in your profile page and will be allowed to do so.

This application offers security by only allowing you to edit or delete your own entries. Using Sinatra and Ruby, this site is also setup to only display certain pages or views only if the user is logged in. If you are not logged in, you will be directed either to the login or signup pages.

This application was built using SQL, ActiveRecord, Ruby, and Sinatra. Hope you enjoy the application. Feel free to contribute and collaborate via the project’s Github page.
