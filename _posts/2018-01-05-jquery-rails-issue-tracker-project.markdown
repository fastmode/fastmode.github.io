---
bg: "sorry-imkirk-261041.jpg"
layout: post
title:  Rails Issue Tracker with jQuery Front End
summary: "Keep track of all your Tickets and Issues"
date:   2018-01-05 12:01:00 -0400
categories: posts
tags: ['full-stack', 'projects']
author: fastmode
---

I updated my existing Rails Issue Tracker application and plugged in a jQuery Front End.  This project turned out to be one of the most challenging ones I’ve had take on.  The main issue was that my brain had to switch from strictly writing Ruby on Rails and now deal with many new stacks.  I now had to implement the knowledge and methodology of Javascript and have it play with a working Rails application.  

If you recall, the Rails Issue Tracker application was built with my desire to implement a way to keep track of tickets and issues from my previous positions in the Information Technology field.  After completing the JavaScript section program, I now had the skills to properly implement a JavaScript front end.  The specifications and requirements for this project demanded that I complete a front end with jQuery and that I manipulate the DOM by making various features appear utilizing JavaScript.  

One of the first requirements for this project was that the application must render at least one index page via jQuery and utilize JSON serialization. This required that the application be set up with JSON backend to serve any JSON requests and to properly serialize the data.  I took care of this requirement in my main Dashboard page.  This page displays all open Tickets for each user.  When the page load, the app makes an API call to `/tickets` which returns a JSON object containing all currently Open tickets for the logged in users.  They are then displayed in their own LI.  The backed end is setup with an `ActiveModel::Serializer` file for the Tickets model which allows it to return the indicated data and present it in JSON format.  For this model, JSON will return all the attributes in the Ticket model along with two `has_many` relationships.  These include the `:issues` and `:user_tickets` models.  Below is an example of the JSON that is returned from the /tickets call.

```javascript
[
  {
    id: 9,
    title: "Build a new office",
    status: "Open",
    due_date: "2018-10-04T00:00:00.000Z",
    created_at: "2018-01-04T21:31:06.152Z",
    updated_at: "2018-01-04T21:31:06.152Z",
    issues: [
      {
      id: 34,
      title: "Hire a designer",
      description: "Hire designer for new office designs.",
      status: "Open",
      due_date: null,
      assigned_to: null,
      ticket_id: 9,
      created_at: "2018-01-04T21:31:06.160Z",
      updated_at: "2018-01-04T21:31:06.160Z"
      },
      {
      id: 35,
      title: "Department of Buildings",
      description: "Get permits.",
      status: "Open",
      due_date: "2018-02-04T00:00:00.000Z",
      assigned_to: "",
      ticket_id: 9,
      created_at: "2018-01-04T21:31:57.155Z",
      updated_at: "2018-01-04T21:31:57.155Z"
      }
    ],
    user_tickets: [
      {
      location: "USA"
      }
    ]
  }
]
```

A second requirement was to render at least one show page via jQuery and again use JSON serialization.  I implemented a similar application for this requirement as in the first requirement.  In this case, this was done in the Tickets show page.  In this page, all the information for the Ticket is viewable.  In addition, all Issues belonging to the Ticket are listed.  These Issues are also loaded using a from data received via a JSON call. The data is serialized via the ActiveModel::Serializer file and then rendered onto the page.

Another requirement was that the API reveal one `has-many` relationship in the JSON that was rendered to the page. This was also implemented in the Tickets show page.  Tickets are setup with a `has_many :issues` relationship.  When the Ticket show page is loaded, all corresponding Issues are provided via the JSON object. These are then rendered on the Ticket show page.

One more requirement was that my rails API be used in conjunction with a form to create a resource and render the response without a page refresh. I implemented this requirement in the Ticket show page.  When this page is loaded, a list of Issues belonging to the loaded Ticket are displayed.  Below this Issue list is a `Add Issue` button.  When this button is pressed, the page utilizes jQuery to display the New Issue form directly on the page without having a page reload.  When the form is completed and submitted, the New Issue is automatically appended to the existing Issues list, again, with no reload.

Finally, the last requirement was that JSON requests be translated into model objects and that a prototype exist on one of the objects. I utilized the Handlebars library to implement this requirement.  I chose to do this on my Tickets page.  The final product is that when a user navigates to the main Dashboard, the page will list all the open Tickets displaying the title and a badge which indicates Issues.  

The way this works is that when the Dashboard page is loaded, a function is called which makes a jQuery call to getJSON from the `/tickets` JSON API.  Once the data is received, the data is iterated over and each element is loaded on the the page.  During each iteration, the object is broken down and a new Ticket object is created according to the Ticket Model Object function.  Once the Ticket object is created, it is used in conjunction with Handlebars to pump it in to the `#ticket-template` that lives in the `_jumbotron` partial. You can see the code below.

```javascript
// Uses JSON to render all open tickets with Handlebars
  $(function () {
    $.getJSON('/tickets', function(data) {
      data.forEach(function(el){
        // Create Ticket prototype
        Ticket.prototype.renderLI = function() {
          return Ticket.template(this);
        }
        // Finds template in html and compiles it to Handlebars object
        Ticket.templateSource = $("#ticket-template").html();
        Ticket.template = Handlebars.compile(Ticket.templateSource);
        // Creates new Ticket object
        var ticket = new Ticket(el)
        // Takes new Ticket object and renders with with Handlebars
        var ticketLi = ticket.renderLI();
        // Adds newly rendered LI to HTML
        $("#open-tickets").append(ticketLi);
      });
    });
  });

  // Creates Ticket model object
  function Ticket(attributes) {
    this.id = attributes.id;
    this.title = attributes.title;
    this.status = attributes.status;
    this.issue_count = attributes.issues.length;
  }
 ```

Implementing this jQuery front end was challenging.  But it gave me the opportunity to really push myself and put into play all the various techniques learned from the Javascript section.  I had to do a ton of researching and test out various patterns in order to get the functionality I needed into play.  My Javascript debugging skills definitely increase during this project.  I feel like I got way more errors here than I did with Rails.  I also had to do more work to figure out what exactly I had either typed wrong or entered incorrect syntax.  Overall, this helped me get better at coding with JS and got me in the practice of testing multiple times after making changes.

You can view a demo of this application by navigating to: [Video](https://youtu.be/1L-CVN6CKes)

Feel free to fork my repo, open any issues, or contribute on [Github](https://github.com/fastmode/rails-issue-tracker)