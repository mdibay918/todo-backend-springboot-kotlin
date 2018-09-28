**Back End Todo**
This project is inspired by [Todo MVC project](http://todomvc.com/).  Developers these days are spoiled with choice when it comes to selecting an appropriate set of tools (Programming Language, Frameworks, Database, API Gateways, etc.) for a microservice architecture. 



Project Description:
--
+ This is a simple todo app.  
+ User adds a Todo to  the list
+ There is a Worker robot which can complete the task for you on a scheduled time.
+ Once the task is completed, TODO app moves the todo item to the done list.


Design:
---
+ Todo Service (Jsnow)
	+ It creates a Todo item with name, and time associated with that
	+ It notifies the scheduler service that Todo is created
	+ In case it receive a message from Scheduler on Todo item completion, it removes the Todo from it’s DB

  

+ Scheduler Service (Tyrion)
	+ Receive a Todo created message from Todo service, it adds it to it’s list for constantly checking the timestamp
	+ Keep checking the list, if a time stamp is reached for a todo, it notifies the Worker service to complete the Todo.
	+ In case it receives a completion message from Worker Service on a Todo, it removes the Todo from it’s list and notifies the Todo Service to remove the Todo as well.

+ Worker Service (Arya)
	+ Very lightweight service.
	+ It receive the notification from scheduler service
	+ After a 1 minute delay, it notifies the scheduler service that Todo is completed.
