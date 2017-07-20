---
layout: post
title: "Mockito example"
description: "Here is an example of how to use the Java testing framework Mockito"
tags: [Tests, TDD, Java, Android]
---

Yet another post about testing.

Recently I've been working mainly on Android projects using Java so I decided I needed to learn how to write tests in Java.
Here is example of how to use Mockito.

## Dependency

To start using Mockito, you need to add it in as a test dependency to your gradle script.

    dependencies {
      testCompile "org.mockito:mockito-core:2.8.47"
    }

Further details on Mockito can be found [here](http://site.mockito.org/).


## RunWith

To help keep your tests clean, use the Mockito test runner annotation with your test class;

    @RunWith(MockitoJUnitRunner.class)
    public class MockitoExampleTest {

    }
    
Further details on the test runner can be found [here](http://javadoc.io/doc/org.mockito/mockito-core/2.8.47).

## Test

Creating a test is pretty straight forward; you just need to add the Test annotation to method within the test class.

    @Test
    public void MyTest(){
        
    }

## mock

To create a mock, there is the static mock method.

    IExampleInterface exampleInterface = mock(IExampleInterface.class);

## when

If you need to setup the mock to return values there is the static when method.
You first specify which method you are setting up then use thenReturn to set which value you want 
to return.

    int expectedInt = 1;
    when(exampleInterface.GetNumber()).thenReturn(expectedInt);

When the method being setup has parameters, you can use exact values as the expected parameter.

    String expectedString = "a string";
    int inputNumber = 2;

    when(exampleInterface.getString(inputNumber)).thenReturn(expectedString);

If you don't need to be exact with the expected parameter, you can use the Mockito matchers.
For example;

    String expectedString = "a string";
    when(exampleInterface.getString(anyInt())).thenReturn(expectedString);

## Assert

Mockito plays nicely with JUnit assertions, so you can just use the standard JUnit assertions.
For example;

    ExampleClass exampleClass = new ExampleClass(exampleInterface);
    String result = exampleClass.getResult(inputNumber);

    Assert.assertEquals(expectedString, result);

## verify 

Verify is used to assert against the methods on a mock. You can check if a certain method was 
called, how many times, and with what parameters.

    verify(exampleInterface, times(1)).getString(anyInt());

## Captor

Captors can be use to capture the values that are passed as arguments to your mocks for further assertions.
I have found them to be pretty useful for testing callbacks as you can capture the callback value, then call it in your test.

////!!!!!!!!!!
main class to implement an interface
pass self to a dependency
use captor to capture the class as an argument
get value from captor
call method
verify another dependency called.





