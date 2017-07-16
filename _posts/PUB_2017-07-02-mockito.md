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

## RunWith

Using the RunWith annotation, you attach the Mockito test runner to your test class;

    @RunWith(MockitoJUnitRunner.class)
    public class MockitoExampleTest {

    }

The runner helps to cleap your tests clean by 

http://javadoc.io/doc/org.mockito/mockito-core/2.8.47

## Test


## mock


## Captor


## when


## verify 
