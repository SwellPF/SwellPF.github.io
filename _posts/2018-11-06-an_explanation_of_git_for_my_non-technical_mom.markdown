---
layout: post
title:      "An Explanation of Git for my Non-technical Mom"
date:       2018-11-06 16:47:25 +0000
permalink:  an_explanation_of_git_for_my_non-technical_mom
---


When I was a kid, my mom had a box of family recipes she kept on the kitchen counter.  During the holidays, we could count on some of our favorite recipes being selected from the box in preparation for the big meal.  In many ways, computer programs are analogous to recipes.  They both contain ingredients (objects in the world of object-oriented programming) and instructions (methods/procedures/APIs, etc. in programming).  

One of the best things about family recipes is sharing them with friends and family.   Occasionally, someone will tinker with ingredients -- adding a dash of extra spice or omitting an ingredient to account for someone’s dietary preferences or to accommodate someone who has a food allergy.  Sometimes these variations improve on the recipe and sometimes they don’t.   The same principle applies to software development.

Git is a distributed version control system which allows people to store, retrieve and share files (usually computer code) with others.  One of the key benefits of this cloud-based system is that it makes it easy to allow others to make a copy of a file repository (a process called “forking”)  which protects the original repository from modification.  After all, you don’t want people changing your recipes without your knowledge!

To make our file repository portable, we clone a repository to a location on our hard drive.  This allows us to work with these files without having a persistent connection to the repository in the cloud.  Also helpful if grandma doesn’t have Internet access in her kitchen!

Unless some version control systems, Git works by storing snapshots of repositories instead of simply logging changes to files.  That means that if something should happen to the original repository it can be restored from an intact copy stored on any of the computers that have accessed the repository.

But the best part of Git has to do with branching – a process that allows users to make modifications to repositories of files that can be kept separate and distinct from the master repository in the cloud.  

In my recipe analogy, let’s say you fork and clone my mom’s delicious Thanksgiving stuffing recipe.  You decide to experiment by adding toasted walnuts to the recipe.  When you make it, it turns out amazing and you want to suggest that mom modify her recipe.  You “push” your changed recipe repository to the cloud and then initiate a “pull” request to mom to evaluate you suggested change.  If mom likes the change she can accept the changes.  If she doesn’t, you can still maintain your version as an independent branch.  

This is common with software development with programmers maintaining different versions of code which can be deployed or rolled back if needed.  These versions can all coexist and be reviewed and retrieved as needed.

Git and the online host GitHub provide an incredible platform for the software development community to collaborate and share code with others in a robust and efficient manner.

