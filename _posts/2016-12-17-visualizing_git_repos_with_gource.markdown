---
layout: post
title:  "Visualizing Git Repos with Gource"
date:   2016-12-17 00:10:12 -0500
---


I am fairly new to the world of coding, but already feel like I’m immersed in this world.  As I am going through the Full Stack Web Development Course at Flatiron School, I can’t stop wanting to learn more and more.   I just completed the HTML and CSS portions of the course and have jumped back onto Ruby.  I’ve gotten pretty comfortable with using Git and doing all the cloning, forking, pushing, pulling, and checking out branches. I have come to understand why developers and organizations put so much importance in versioning their code to ensure there is traceability and backup of their source files.  

I had a really good meeting with a fellow developer friend today.  I was able to get a tour of his office and he showed me some of the really neat projects he is currently working on.  One of the really neat things he showed me was Gource. 

## What is Gource?
Here is the visualization of the Evolution of the Ruby programming language.  Check out Matz going to town on his own in the earlier years!

[![IMAGE ALT TEXT](http://img.youtube.com/vi/si-kxnwKvjU/0.jpg)](http://www.youtube.com/watch?v=si-kxnwKvjU "Evolution of ruby (Gource Visualization)")

I found Gource to be pretty neat!  Here was a visualization program that could take any directory using Git and turn it into a beautiful graphical representation.  From the Gourse site, “Software projects are displayed by Gource as an animated tree with the root directory of the project at its centre. Directories appear as branches with files as leaves. Developers can be seen working on the tree at the times they contributed to the project.”

## How do I get it?
I decided I needed to try this on my own Git repositories.  In order to do this I had to first install Gource on my Mac.  I headed over to the Gource page which told me I needed to use Homebrew to install this.  At this point I had no idea what Homebrew was.  So it was time to do a bit of reading and Googling.  

I found that Homebrew is a package manager for Macs.  From their site, “Homebrew installs the stuff you need that Apple didn’t”.  It is also open source, created with git and ruby.  I proceeded with installing Homebrew by running the following command in Terminal:

Code
`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

After this completed, from other articles, they recommend these two commands be run to update and get Homebrew ready:

`brew update`

`brew doctor`

You can get more information by going directly to the [Homebrew site](http://brew.sh/).

I was now ready to install Gource.  Per the instructions you are to:

Install FFMPEG, this is to install the video encoder and its dependencies:
`brew install ffmpeg`

Then install Gource the same way:
`brew install gource`

Now that this is completed, you are ready to try it on your coding directories.  

Navigate with Terminal to one of your coding directories.  Ensure you are on the top level directory and ensure you have a .git directory.  You must be int the folder where you ran git init.  

Run:
`gource`

This will open up a new window and start the video showing you a graphical representation of your work within that directory.  

## How Do I Create Gource Videos?
To create an MP4, you can use the following code:
`gource —hide filenames --seconds-per-day 0.1 --auto-skip-seconds 1 -1280x720 -o - | ffmpeg -y -r 60 -f image2pipe -vcodec ppm -i - -vcodec libx264 -preset ultrafast -pix_fmt yuv420p -crf 1 -threads 0 -bf 0 gource.mp4`

Here is my first video of one of the HTML and CSS projects I coded along to.  I believe I spend a total of 5 days working on it but here its condensed to about 20 seconds:

[![IMAGE ALT TEXT](http://img.youtube.com/vi/aS43-x_lUCM/0.jpg)](http://www.youtube.com/watch?v=aS43-x_lUCM "My First Gource Attempt ")
Git: https://github.com/fastmode/exceptional-realty-bootstrapped

Here is one more of the development of the Learn IDE. I’ve been using the Learn IDE to learn how to code.  You can see its a lot more complex and cooler than my project.  

Learn IDE Dec 2015 - Dec 2016 Development in one minute:

[![IMAGE ALT TEXT](http://img.youtube.com/vi/hwocDc3UYR0/0.jpg)](http://www.youtube.com/watch?v=hwocDc3UYR0 "Learn IDE Dec 2015 - Dec 2016")
Git: https://github.com/learn-co/learn-ide

Check out this [Wiki](https://code.google.com/archive/p/gource/wikis/Videos.wiki) with more information on Gource and on making videos.  

Hope you found this fun and useful. 

