---
layout: post
title: "SOLID User Stories?"
description: "Is it possible to apply the SOLID principles to user stories?"
tags: [User Stories, SOLID]
---

As a developer it can be very useful to use principles such as SOLID and the Four Rules of Simple 
Design to help me write better code. But it struck me that it might be helpful to apply the SOLID
principles to writing effective user stories.

## SOLID Principles

So a quick recap of what the SOLID Principles are firstly. They are a list of principles to help
create easily maintainable object-orientated code introduced by Robert Martin. Thanks Uncle Bob!

* Single responsibilty principle
* Open/closed principle
* Liskov substitution princple
* Interface segregation principle
* Dependency inversion principle

### Single Responsibilty Principle

A class should only have one responsibility.

It struck me that user stories can become overly complicated and try to cover too many requirements.
If a user story is broken down to its smallest possible size I think it helps the story to move
across a kanban board more easily. 

The developer working on it will have a clearer idea of what is expected of them. Testing time should
shorter as it will be clearer if it has succeeded or not. Risk of deployment should also be reduced
smaller changes will be going to production.

Just as a single class can have many tests, a single responsibilty user story can have many 
acceptance criteria.

If a user story adds value once complete, then I can't really see how a user story could ever be too
small. For example if a form is required, I would be tempted to identify which fields are absolutely
required then they would be one user story. Each added value such as email validation or user name
checking should be a user story in their own right. This is because value can be gained without them
and more value will be gained with them.

### Open Close Principle

A software entity should be open to extension but closed to modification.

So new features in software should be able to be implemented by adding new code to
extend the currect functionality, by using inheritance for example. You shouldn't need to modify the
existing code.

I think user stories can behave in a similar fashion. When slicing a new feature each story should
keep adding value on top of the value from previous tickets. If a user story conflicts with a previous 
story and means a previous story needs to be modified then waste is being created.

### Liskov substitution princple

The Liskov substitution principle states that if S is a subtype of T, then objects of type T may be 
replaced with objects of type S without altering the properties of the program.

While this doesn’t directly compare with user stories, I feel that user stories can often extend 
other stories. As in, build upon or modify existing functionality. When creating user stories that 
do this, it may be helpful to keep the Liskov substitution principle in mind. By thinking if the 
modification in the new user story will alter or conflict with existing functionality, unpredicted and 
undesirable side effects may be avoided. That isn’t to say that changing functionality is a bad 
thing, just that as you move towards more granular user stories, taking a step back and thinking 
of the wider user story can be useful. 

### Interface segregation principle
 
Its better to have many specific interfaces than one large general one.

By following this principle, code can be much easier to read as the smaller, specific interfaces
are much better at conveying the intent of the code over a large interface with many methods that
might not even be used. Furthermore, the increased coupling that will come from a large interface 
will make the software less flexible.

Larger user stories can come with the same issues as large interfaces. When there are multiple
requirements the intent of the story can become confusing. Smaller user stories better convey the 
intent, and will be easier to assess if the desired value has been achieved.

Also, smaller and separate user stories have less chance of coupling the solutions together. Much in
the same way as to pass a unit test you should do the smallest amount necessary, you should also do
the smallest amount needed to get the value from a story. If more requirements arise, these should
form new user stories.
 
### Dependency inversion principle

Dependency inversion means that high level components should not have dependencies on lower level
components. This inversion can be achieved through abstracting the lower level components behind
interfaces.

While user stories don't have dependencies in the same way that a class can, I think it could be
helpful to ensure higher level user stories don't have reference to and depend on lower level 
stories. For example, a user story for a new checkout form to increase conversion wouldn't need the
details of a lower level story for the email validation on the form. If it did, it would be over
complicating the form story and slowing down getting value. However the lower level story would 
obviously need to have knowledge of the higher level story.

### SOLID User Stories?

After thinking how the SOLID principles can be applied to user stories I can't see them 
becoming the new standard to assess user stories anytime soon. However, thinking of why the 
SOLID principles are useful has definitely made me think more about what makes a good user story
and how I can improve ay I write in the future. 