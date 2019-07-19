---
layout: post
title:      "Putting it all Together"
date:       2019-07-19 19:21:30 +0000
permalink:  putting_it_all_together
---


One of the most rewarding aspects of the journey to becoming a full-stack web developer is the moment when the big picture starts to come into focus and you realize you now have the knowledge to build a complete, functional web application.  My most recent portfolio project at Flatiron School involved building a Sinatra application utilizing the MVC (Model-View-Controller) design and implementing CRUD (Create-Read-Update-Delete) functionality.  

I built a vacation recommendation app which allows users to view a listing of existing recommendation posts as well as create, edit and delete recommendations of their own.

In addition to writing the base code in Ruby and leveraging the benefits of the Sinatra web framework, the project also includes HTML and CSS for rendering browser views, ActiveRecord for persistence and retrieval of data in a SQL database, and implementing code that utilizes the browser’s session hash to identify the current user and control access to my application’s functionality based on the user’s session info.   For example, users are only able to edit or delete entries that were originally created by them.  To provide security for account passwords, I implemented the bcrypt Ruby gem which creates and stores encrypted passwords as a salted hash.

I implemented a Ruby gem called Sinatra-Flash to display error messages when a user provides invalid input or attempts to take a prohibited action.  This is achieved by assigning an error message string to the flash[:message] hash and then displaying the contents of flash[:message] via the layout file if flash[:message] isn’t empty.

But Sinatra-Flash wasn’t my first attempt to engineer the display of error messages in my app.  In an earlier Flatiron lab, I was introduced to the rack-flash3 gem.  It worked great for the “Sinatra Playlister” lab because the requirements of the lab only needed error handling for one controller.  In my case, I wanted to be able to provide error messages whether they were triggered in either my “vacations” controller or my “users” controller.  My first instinct was to put the line to require rack-flash3 to the application controller and expect that it would function properly through inheritance.  Unfortunately, that didn’t work.  A recommendation from someone on Slack to look into Sinatra-Flash was just what was needed.

This project was both challenging and rewarding as it brought together all of the languages, tools and platforms I’ve learned so far and used them to build an application that performs many of the functions found in commercial applications: user account management and authentication, data persistence to a database, and interaction with the user to create/read/update/delete data.  While my application is basic in function, it’s exciting to have built something from scratch that (at least conceptually) resembles the type of apps that people use every day.
