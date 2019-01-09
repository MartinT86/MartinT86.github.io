---
layout: post
title: "Planet proto solution"
description: "My solution to the Planet Proto nodeschool lesson on prototypes"
tags: [Javascript, Nodeschool]
---

Continuing to work through the awesome [nodeschool.io](http://nodeschool.io/) tutorials I decided I needed
to know more about the javscript object model, so here are my solutions to the [Planet Proto](https://github.com/sporto/planetproto)
workshop.

This was a really useful set of tutorials, it felt like it filled in a big gap in my javscript
knowledge.

<figure>
	<a href="{{ site.url }}/images/planetproto.jpg"><img src="{{ site.url }}/images/planetproto.jpg" alt="Planet proto lessons"></a>
	<figcaption>The lessons available in Planet Proto.</figcaption>
</figure>

Each lesson in this tutorial comes with a handy boilerplate file that explains what is required and you
need to fill in the results in the test assertions.

## Simple Objects

Lesson one explains the easiest way to create an object in javascript; using object literals.

    // -> Create an object called 'robot' using an object literal
    // -> robot should have a property 'smart' with value true
    var robot =  {
        smart: true
    }

    // -> Claim the result robot.smart
    claim(robot.smart, true);

    // ------------------------------------------------
    // Common JS exports for verification, don't modify
    module.exports = {
        robot: robot
    }

## Proto

Lesson two goes on to explain about the &#95;_proto__ object. While usually supported, its behaviour has only been standardised in ECMAScript 6 as a legacy feature and changing an objects prototype is a very slow operation. So while its not advised to use, its good place to start learning about the object model.

One object can be set as the prototype of another. This allows for the properties of the prototype to be
available on the parent object.

You can check the prototype of an object with the .isPrototypeOf() function which returns true/false.

    /* global claim */
    // -> Create a machine object
    //    with a property motors = 4
    var machine = {
        motors: 4
    }

    // -> Create a robot object
    //    with a property friendly = true
    var robot = {
        friendly: true
    }

    // -> Create a robby object
    var robby ={}

    // -> Make machine the prototype of robot
    robot.__proto__ = machine;

    // -> Make robot the prototype of robby
    robby.__proto__ = robot;

    // -> What is `robby.motors`?
    claim(robby.motors, 4);

    // -> What is `robby.friendly`?
    claim(robby.friendly, true);


    // ------------------------------------------------
    // Common JS exports for verification, don't modify
    module.exports = {
        machine: machine,
        robot:   robot,
        robby:   robby
    }

## Dynamic Lookups

Properties can be added to the prototype at any time and those properties will be available
on the parent object.

    // -> Let's define three objects: 'machine' 'vehicle' and 'robot'
    var machine = {}
    var vehicle = {}
    var robot = {}

    // -> Make machine the prototype of vehicle
    // -> Make machine the prototype of robot
    vehicle.__proto__ = machine;
    robot.__proto__ = machine;

    // -> What is `vehicle.motors`?
    claim(vehicle.motors, undefined);

    // -> What is `robot.motors`?
    claim(robot.motors, undefined);

    // -> Define a 'motors' property on machine, set this to 4
    machine.motors = 4;

    // -> What is `vehicle.motors` now?
    claim(vehicle.motors, 4);

    // -> What is `robot.motors`?
    claim(robot.motors, 4);


    // ------------------------------------------------
    // Common JS exports for verification, don't modify
    module.exports = {
        machine: machine,
        vehicle: vehicle,
        robot:   robot
    }

## Property assignments

Properties that are updated on the parent object are assigned to the object and don't update 
the prototype.

    // -> Define three objects: 'machine', 'robot' and 'vehicle'
    //    In the definition of machine add a property 'motors' set to null.
    var machine = {
        motors: null
    }
    var robot = {}
    var vehicle = {}

    // -> Let's make machine the prototype of robot and vehicle
    vehicle.__proto__ = machine;
    robot.__proto__ = machine;

    // -> What are `machine.motors`, `robot.motors` and `vehicle.motors`?
    claim(machine.motors, null);
    claim(robot.motors, null);
    claim(vehicle.motors, null);

    // -> Set `robot.motors` to 4 by direct assignment
    robot.motors = 4

    // -> What are `machine.motors`, `robot.motors` and `vehicle.motors` now?
    claim(machine.motors, null);
    claim(robot.motors, 4);
    claim(vehicle.motors, null);


    // ------------------------------------------------
    // Common JS exports for verification, don't modify
    module.exports = {
        machine:  machine,
        vehicle:  vehicle,
        robot:    robot
    }

## Arrays and Objects

Strangely arrays and objects don't behave in the same way. If you update an array or object 
property on a parent object they are updated on the prototype.

    // -> Create three objects: 'machine', 'robot' and 'vehicle'
    // -> In the definition of machine set a property 'parts', set it to an 
    //    empty array `[]`
    // -> In the definition of machine set a property 'capabilities', set it to 
    //    an empty object `{}`
    var machine = {
        parts: [],
        capabilities: {}
    }
    var robot = {}
    var vehicle = {}

    // -> Let's set the prototype of both robot and vehicle to machine
    robot.__proto__ = machine;
    vehicle.__proto__ = machine;

    // -> What is `robot.parts`?
    claim(robot.parts, []);

    // -> What is `vehicle.parts`?
    claim(vehicle.parts, []);

    // -> What is `robot.capabilities`?
    claim(robot.capabilities, {});

    // -> What is `vehicle.capabilities`?
    claim(vehicle.capabilities, {});

    // -> Let's add a 'core' part to robot
    robot.parts.push('core');

    // -> What is `robot.parts` now?
    claim(robot.parts, ['core']);

    // -> What is `vehicle.parts` now?
    claim(vehicle.parts, ['core']);

    // -> Let's set an ability to vehicle
    vehicle.capabilities.fly = true;

    // -> What is `robot.capabilities` now?
    claim(robot.capabilities, {fly:true});

    // -> What is `vehicle.capabilities` now?
    claim(vehicle.capabilities, {fly:true});


    // ------------------------------------------------
    // Common JS exports for verification, don't modify
    module.exports = {
        machine: machine,
        vehicle:    vehicle,
        robot:    robot
    }

## Object Create

So by setting &#95;_proto__ directly it has easier to see how it behaves, however it is not
yet fully supported. A more supported method is to pass the prototype to Object.create(). 

    // -> Let's create an object called 'machine'
    var machine = {}

    // -> Use Object.create to create another object called 'robot' with 'machine' 
    //    set as the prototype
    var robot = Object.create(machine)

    // -> Use Object.create to create another object called 'robby' with 'robot' 
    //    as the prototype
    var robby = Object.create(robot)

    // -> What is the result of `machine.isPrototypeOf(robby)`?
    claim(machine.isPrototypeOf(robby), true);

    // -> What is the result of `robot.isPrototypeOf(robby)`?
    claim(robot.isPrototypeOf(robby), true);

    // -> Which object is the direct prototype of robby?
    claim.same(Object.getPrototypeOf(robby), robot);


    // ------------------------------------------------
    // Common JS exports for verification, don't modify
    module.exports = {
        machine:  machine,
        robot:    robot,
        robby:    robby
    }

## Dot new

A nice way of using Object.create() is to create a function on an object called new(). 
When new() is called return Object.create(this).

    // -> Define an object called 'Robot'
    // -> Define a method called 'new' in Robot
    // -> When Robot.new is called it should return a new object with Robot as its prototype 
    //    e.g. var robby = Robot.new();
    //    Robot should be the prototype of robby

    var Robot = {}

    Robot.new = function(){
        return Object.create(this)
    }

    var robby = Robot.new()


    // ------------------------------------------------
    // Common JS exports for verification, don't modify
    module.exports = {
        Robot: Robot
    }

## Constructor functions

A popular way of creating prototype chains is to use constructor functions. This works by
creating a function that has statements like this.{propertyName} = x. Then you call the function
with new. The return object is linked to the function by its prototype.

    // -> Define a 'Robot' constructor function
    // -> Inside the Robot constructor assign a property 'motors' on 'this',
    //    set motors to 2
    // -> Create an instance of Robot called 'robby'

    function Robot(){
        this.motors = 2
    }

    var robby = new Robot()

    // -> What is the result of `(robby instanceof Robot)`?
    claim((robby instanceof Robot), true);

    // -> What is `robby.motors`?
    claim(robby.motors, 2);


    // ------------------------------------------------
    // Common JS exports for verification, don't modify
    module.exports = {
        Robot:  Robot,
        robby:  robby
    }

## Implicit This

When a constructor function is called with "new", Javascript has an implicit reference to the new object
being created with the "this" keyword. So it's important to remember the "new". To help remember
to use "new" it is common to capitalise the first letter of the constructor function. 

With my background in C# this is the method of creating instances of objects that is the most natural to me.

    // -> Define two constructor functions: 'Robot' and 'Vehicle'
    // -> When called with 'new', the Robot constructor function should return 
    //    the implicit 'this'
    // -> When called with 'new', the Vehicle constructor function should return 
    //    an object of your own making, not the implicit 'this'.

    function Robot(){
        
    }

    function Vehicle(){
        return {}
    }


    // ------------------------------------------------
    // Common JS exports for verification, don't modify
    module.exports = {
        Robot:    Robot,
        Vehicle:  Vehicle
    }

## The function prototype

So this one took a bit to get my head around. 

Every function in Javascript has a property called prototype. This is not the same as &#95;_proto__. It
is the object that an instance created by the function will have as its own &#95;_proto__.

So any property added to functionName.prototype will be available to all instances created by that
function.

    // -> Define a 'Robot' function constructor
    // -> Create two instances of Robot: 'robby' and 'cranky'
    // -> Both robby and cranky should respond to 'parts' and 'capabilities', these 
    //    should be empty arrays at first

    function Robot(){
        this.parts = []
    }

    Robot.prototype.capabilities = []

    var robby = new Robot()
    var cranky = new Robot()



    // -> Claim the result of robby.parts
    claim(robby.parts, []);
    // -> Claim the result of cranky.parts
    claim(cranky.parts, []);
    // -> Claim the result of robby.capabilities
    claim(robby.capabilities, []);
    // -> Claim the result of cranky.capabilities
    claim(cranky.capabilities, []);

    // -> Add 'core' to robby.parts, cranky.parts should still be empty
    // -> Add 'fly' to robby.capabilities, after doing that cranky.capabilities must 
    //    also have 'fly' without adding to it directly, so this property has to be 
    //    shared

    robby.parts.push('core')
    robby.capabilities.push('fly')

    // -> Claim the result of robby.parts
    claim(robby.parts, ['core']);
    // -> Claim the result of cranky.parts
    claim(cranky.parts, []);
    // -> Claim the result of robby.capabilities
    claim(robby.capabilities, ['fly']);
    // -> Claim the result of cranky.capabilities
    claim(cranky.capabilities, ['fly']);


    // ------------------------------------------------
    // Common JS exports for verification, don't modify
    module.exports = {
        Robot:  Robot,
        robby:  robby,
        cranky: cranky
    }
