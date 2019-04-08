# Template View

A template allows generating the UI in the backend. This means the HTML will be generated in the server, and sent to the user.

Any dynamic component of the view, such as paginated tables requiring asynchronous messaging, are handled with a frontend technology such as Javascript. But this means that the project may require three languages: one for the backend, one for the frontend and one for the templates.

## Architecture

This combines frontend and backend, creating a more monolithic architecture.

## State

The server will need to handle the user's information through sessions, meaning the backend takes care of the state.

## AJAX

Asynchronous messaging between the user's client and the server is handled with AJAX.

## Example

A Spring MVC application using Thymeleaf for the templates will make use of the following languages:

* Java for the backend
* HTML + Thymeleaf notation for the templates
* Javascript for AJAX

Each view will be built from Thymeleaf templates, and mapped to a URL. This means that going from the employee's page to the vacations administration view will require leaving the old view and loading a new one.

## Advantages

* Light frontend
* Views are easy to generate
* Can have a good control over the session

## Disadvantages

* Reduces user interaction
* Changing the view may require reloading
* Dynamic views can make the frontend over-complicated
* Three languages \(frontend, backend, templates\)

