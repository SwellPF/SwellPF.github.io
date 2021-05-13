---
layout: post
title:      "DOM Manipulation and API Calls: Two Sides of the Same Coin"
date:       2021-05-13 11:54:30 -0400
permalink:  dom_manipulation_and_api_calls_two_sides_of_the_same_coin
---


For the JavaScript student project, the primary requirement was to build an application which consists of a Rails API backend and a JavaScript frontend.  Asynchronous JavaScript (AJAX) requests allow for communication between the front and back ends. 

In the browser, the contents of the page are commonly referred to as the document.  The Document Object Model (DOM) is a representation of the objects and structure of the webpage.  Developers can modify what is displayed on the page through a process called DOM manipulation.  By executing JavaScript functions, elements can be added, changed or removed from the page the user sees.  It is important to understand that the DOM is a representation of the page and any changes to the page through DOM manipulation are not persisted.  Clicking the refresh button on the browser would restore the page to its original appearance (as written in the program code) before any changes were made to the DOM.

My project is a simple recipe manager designed as a single-page app that allows users to view a list of recipes and add or delete recipes from a database managed through the Rails backend.  A recipes controller was configured with methods for displaying the recipe index, creating a new recipe and deleting a recipe.  The frontend utilizes HTML and JavaScript to populate the DOM with the information that the user sees in the browser and provide the interface for adding and removing recipes.  In order for the Rails backend to communicate with the frontend, JSON and fetch API calls are made to pass data between the two.

When the page initially loads, a fetch GET call is made to the index route in the Rails server which requests the index of recipes.  The returned data, referred to as a promise response, is then passed to an Object Oriented JavaScript class and its constructor method to create an object for each item and another function renders the appropriate HTML which is then inserted into the DOM.

A form is also present within the DOM for adding a new recipe.  When a user fills out the new recipe form and clicks the form’s submit button, a fetch POST call is made which takes the form data and converts it into “stringified” JSON sends it to the Rails server’s create method in the controller. 

After a new entry is successfully added to the database, the task still remains to update the DOM.  A JavaScript function is executed to identify the appropriate location in the DOM to insert the HTML for the new recipe so it is immediately visible to the user.  (If we didn’t update the DOM a simple browser refresh would display the newly added recipe as it was persisted to the database via the fetch POST API call.)  It was interesting during testing to see in real time how this is truly a two-stage process (the persisting of data and what is rendered to the user).

A similar process was followed to delete an unwanted recipe.  Each recipe is assigned a delete button in the DOM that has an event listener assigned which triggers a function to make a fetch DELETE call to the Rails server which deletes the record from the database.  A JavaScript .remove() method removes the element from the DOM so the user gets immediate visual confirmation.

One of the most interesting – and challenging – aspects of the project was learning how to use serializers to structure data in JSON and also to control which attributes of a data object to include in the serialized JSON string.  For my project I used the FAST JSONAPI which was developed by Netflix.  A little experimentation (and copious use of console.log) will help you understand how the serializer structures the data and therefore how you should reference it.  But once you get the hang of it, you really appreciate the power and flexibility it provides.

Happy coding!

