---
bg: "jesse-orrico-94169.jpg"
layout: post
title:  Heroku | Upgrade Database from Dev to Basic
summary: "For when that data starts coming in!"
date:   2018-02-13 12:01:00 -0400
categories: posts
tags: ['backend', 'database', 'heroku']
author: fastmode
---

Heroku its a great tool for developers.  It allows you to easily deploy your applications without having to worry about setting up servers, networking, hosting.  Essentially, you don't need to be an IT pro to get your app on on the web so others can use it.  

## Why Upgrade?

There does come a time when you will deploy an application that requires a database to persist some data.  I ran into this very recently when I maxed out the free database provided to developers.   Heroku allows you to create a free **Heroku-Dev** database that you can persist up to 10,000 rows.  My app currently pulls in data from an external source and persists this info into the database, I reached the 10K row limit pretty soon.  It was time to upgrade to the next tier.

Luckily, Heroku offers many plans but the next logical one for me was to upgrade to **Heroku Basic**.  This tier allows 10,000,000 rows!  Heroku has a guide that it offers but unfortunately, it doesn't capture how to exactly upgrade to the Basic plan.  It offers an explanation for their more Enterprise plans, but doesn't clearly outline how to just make the next jump.

## How Do I Upgrade?

After some researching online with some trial and error, I was able to move from **Heroku-Dev** to **Heroku-Basic**.

### Provision a **Heroku-Basic** Postgres Database. 
* Log into your Heroku account and click into your app. 
* Navigate to the Resources tab
* Click on the "Find more add-ons" button
* In the new window, click on Data Stores, then find and click on Heroku Postgres.
* Click on Install Heroku Postgres
* Select your Application from the dropdown
* Select the Plan Name, here you will select **Heroku Basic**, which at the time of this post is $9.00 per month
* Then click on the Provision button

This will take a short amount of time provision.  In the mean time, open up your Terminal and navigate to your app's folder repo.  

If you run `heroku pg:info` you will now see the new database there.

```
Dev/espera/espera-app  master ✔                                    
▶ heroku pg:info
=== DATABASE_URL
Plan:                  Hobby-dev
Status:                Available
Connections:           1/20
PG Version:            10.1
Created:               2017-12-21 00:33 UTC
Data Size:             13.0 MB
Tables:                4
Rows:                  14194/10000 (Write access revoked)
Fork/Follow:           Unsupported
Rollback:              Unsupported
Continuous Protection: Off
Add-on:                postgresql-octagonal-19000

=== HEROKU_POSTGRESQL_GOLD_URL
Plan:                  Hobby-basic
Status:                Available
Connections:           0/20
PG Version:            10.2
Created:               2018-02-13 18:33 UTC
Data Size:             7.6 MB
Tables:                0
Rows:                  0/10000000 (In compliance)
Fork/Follow:           Unsupported
Rollback:              Unsupported
Continuous Protection: Off
Add-on:                postgresql-perpendicular-27024
``` 
As you can see, my original Hobby-dev database is called `DATABASE_URL` and my new Hobby-basic database is called `HEROKU_POSTGRESSQL_GOLD_URL`

At this point, you can very easily follow the Heroku provided guide:  <https://devcenter.heroku.com/articles/upgrading-heroku-postgres-databases>.  You can also follow along since you are already here and I give you the real deal.

## Copying your data to new databse

I went ahead and used the `pg:copy` method.

### Maintenance Mode

My next step was to put my app into Maintenance Mode.  I did this by running `heroku maintenance:on`

```
Dev/espera/espera-app  master ✔                                    
▶ heroku maintenance:on
Enabling maintenance mode for ⬢ espera-app... done
```

### Copy the Data

The next step is to actually copy all the data from my original Dev database over to the new Basic database.  I did this by running the `pg:copy` command.  This takes the name of your Dev and new Basic databases.  You can find these by running `pg:info`.  In my case, the original database was simply called `DATABASE_URL` and the new one was `HEROKU_POSTGRESQL_GOLD_URL`.

I successfully ran `pg:copy`, and entered my app name to verify and proceed, as you can see below:

```
Dev/espera/espera-app  master ✔                                    
▶ heroku pg:copy DATABASE_URL HEROKU_POSTGRESQL_GOLD_URL --app espera-app
 ▸    WARNING: Destructive action
 ▸    This command will remove all data from GOLD
 ▸    Data from DATABASE will then be transferred to
 ▸    GOLD
 ▸    To proceed, type espera-app or re-run this
 ▸    command with --confirm espera-app

> espera-app
Starting copy of DATABASE to GOLD... done
Copying... done
```

### Promote Your New Database

After this completed, you will need to promote your new Basic database.  You can do this by running `heroku pg:promote <name of new basic database>`.  

```
Dev/espera/espera-app  master ✔                                     
▶ heroku pg:promote HEROKU_POSTGRESQL_GOLD_URL
Ensuring an alternate alias for existing DATABASE_URL... HEROKU_POSTGRESQL_BLUE_URL
Promoting postgresql-perpendicular-27024 to DATABASE_URL on ⬢ espera-app... done
```

### Turn off Maintenance Mode

Once this completed, you can turn off Maintenance mode by running `heroku maintenance:off`

```
Dev/espera/espera-app  master ✔ 
▶ heroku maintenance:off
Disabling maintenance mode for ⬢ espera-app... done
```

You can then run `heroku pg:info` to see the updated status of your databases.  You can see the my GOLD database is now at the top and primary.

```
Dev/espera/espera-app  master ✔  
▶ heroku pg:info
=== DATABASE_URL, HEROKU_POSTGRESQL_GOLD_URL
Plan:                  Hobby-basic
Status:                Available
Connections:           1/20
PG Version:            10.2
Created:               2018-02-13 18:33 UTC
Data Size:             12.8 MB
Tables:                4
Rows:                  23381/10000000 (In compliance)
Fork/Follow:           Unsupported
Rollback:              Unsupported
Continuous Protection: Off
Add-on:                postgresql-perpendicular-27024

=== HEROKU_POSTGRESQL_BLUE_URL
Plan:                  Hobby-dev
Status:                Available
Connections:           2/20
PG Version:            10.1
Created:               2017-12-21 00:33 UTC
Data Size:             13.0 MB
Tables:                4
Rows:                  14146/10000 (Write access revoked)
Fork/Follow:           Unsupported
Rollback:              Unsupported
Continuous Protection: Off
Add-on:                postgresql-octagonal-19000
```

### Deprovision Old Database

The final step is to deprovision (destroy) your old primary database.  You can do that by running `heroku addons:destroy <original dev database name>`

```
Dev/espera/espera-app  master ✔                                     
▶ heroku addons:destroy HEROKU_POSTGRESQL_BLUE_URL
 ▸    WARNING: Destructive Action
 ▸    This command will affect the app espera-app
 ▸    To proceed, type espera-app or re-run this
 ▸    command with --confirm espera-app

> espera-app
Destroying postgresql-octagonal-19000 on ⬢ espera-app... done
```
### Woot You Did It!!!!

Success!!! If you run `heroku pg:info` you will notice that your **Heroku-dev** database is now gone.  

