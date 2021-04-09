---
layout: post
title:      "Lights!  Camera!  Action!"
date:       2021-04-09 15:20:25 +0000
permalink:  lights_camera_action
---


# THE PROJECT
I am a bit of a movie buff and given that many of us have spent most of the last year in quarantine watching movies I thought developing an app around movie recommendations would be a fun idea for my Ruby on Rails project for Flatiron School.  

I named my app “Cinophile” which is an amalgamation of the word *cinephile*, defined as a person who is fond of movies, and my last name.

Users of the app can view a list of movies with a summary of the movie details and filter the list of movies by genre and/or whether the movies are recent releases.  They can read comments about the movie from other users and post comments of their own.  I also give users the ability to create named watchlists and add movies to their watchlists.  

In addition to creating the ability for users to create an account on Cinophile manually through a signup action, I also integrated the ability to log in using credentials that a user already has with Facebook or Google.  This was accomplished through the Ruby gem named “**omniauth**” and those specifically designed for Facebook and Google (“**omniauth-facebook**” and “**omniauth-google-oauth**”, respectively.)

When I was first adding the functionality, I had only intended to add Facebook authorization.  My integration initially didn’t work and I was having difficulty identifying what was causing the problem.  I decided I would try Google authentication instead.  During that process, I discovered that my .env environment file (needed for the Facebook authorization to work) had inadvertently gotten moved out of the root directory.  As a learning experience, this was a fortunate circumstance because once I corrected my mistake I ended up having two functioning OmniAuth login methods!

One of the beautiful things about Rails is that it is easy to protect users’ passwords.  Utilizing the “**bcrypt**” gem combined with the “**has_secure_password**” method assigned to the User model, passwords are never stored in plain text in the user table of the database.  Bcrpyt instead stores passwords in a salted hash format in the database in a field named “**password_digest**.”  This prevents anyone who might gain access to the database from being able to read users’ passwords.

Rails makes it very simple to perform validations on Active Record models to prevent creating invalid data in an application’s database.  During development, I created an unusual error for myself as it relates to password validation.  In addition to setting “**has_secure_password**” on the User model, I also included in my validations not only that the user name and email address must be present (**validates :name, :email, presence: true** ) but that a password had to be present as well.  This is not necessary as “**has_secure_password**” already inherently requires that a password must exist in order to save a User record.

What made the error unusual is that I only encountered the error when OmniAuth was invoked to log in via the Facebook or Google integrations.  To complicate matters further, if it was the first time the user was accessing Cinophile (i.e. creating a new account) it worked as intended.  It was only on subsequent attempts to log in using Facebook/Google that it failed because it was checking for the presence of a password that wasn’t there due to method being used to validate the user.  A valuable lesson learned!

One of the important characteristics of any web-based app is ensuring the integrity of a user’s credentials when interacting with the application.  In the case of Cinophile, we wouldn’t want users to be able to add comments about a movie without being logged in nor would we want people to be able to post comments by impersonating another user.  I added “**before_action**” methods to each of the models to confirm that a user was logged in before watchlists or comments could be created or edited.  This can be done at the application level (in the **application_controller.rb** file) or in the controllers for the specific models you wish to control.  In my sessions_controller, I added  “**skip_before_action, only: [:new, :create, :omniauth**]” to allow those actions to be performed without the user being logged in, since those methods are involved in the login process itself.  I also utilized a current_user method to ensure that comments and watchlists were only assigned to the user id of the person currently logged in.

This was a fascinating learning experience and demonstrated that sometimes mistakes lead to new vistas of knowledge!
