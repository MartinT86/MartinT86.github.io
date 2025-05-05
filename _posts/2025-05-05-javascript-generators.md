---
layout: post
title: "Javascript generators"
description: "An overview of using generators in Typescript"
tags: [Javascript, Typescript]
---

Generators are something I've not used much, so in order to understand them more I've been practising using them and here is my overview of them.

## function*

To create a generator function, all you need to do is add a "*" after the function keyword.

```typescript
function* basicGenerator() {
  console.log("This is a generator function");
}
```

By adding the star, the function will now return a ```Generator<never, void, unknown>```

The returned generator will have a ```.next()``` function, which returns an ```IteratorResult<never, void>```

The IteratorResult will be either an IteratorYieldResult or an IteratorReturnResult. Which will have the data returned from either a yield or a return under the value property and a "done" boolean which will return true once the generator has provided all of its results.

```typescript
function* returningGenerator() {
  return 3
}

describe('Returning generator', () => {
  it('should return an IteratorResult', () => {
    const generator = returningGenerator()

    const result = generator.next()
    const secondResult = generator.next()

    expect(result.value).toEqual(3)
    expect(result.done).toBeTruthy()
    expect(secondResult.value).toEqual(undefined)
  });
});
```

## A returning generator

In the example above, the IteratorResult will now have the type of ```IteratorResult<never, number>``` since the generator wil be returning a number.

Again in the above example, the second call of next will have a value of undefined and the done value will be true, as the generator has returned all of its results.

## A yield generator

If you use the yield keyword in a generator, the generator will return results with a value for each use of the yield keyword.

```typescript
function* yieldGenerator() {
  yield 1
  yield 2
}
```

In this example, the first two calls of next() will return the yield values then the third call will return a true value for done.

The result type will now become ```IteratorResult<number, void>``` as the generator is yielding but does not return.

## Passing a value to the generator

Just as with other functions, values can be passed to the generator to be used within them.

```typescript
function* parameterGenerator(input: number) {
  while (input < 2) {
    yield input
    input++
  }
}
```

## Passing a value to next

The next function can also have parameters passed to it. To use the value within the generator, declare a variable on the left of the yield expression: ```const paramValue = yield val```

To declare the type of the value that will be passed to the next function, set it in the third generic type for the generator.

```typescript
function* nextParameterGenerator(input: number): Generator<number, void, number> {
  let val = 0
  let increase = input
  while (true) {
    const newIncrease = yield val
    val = val + increase
    if (newIncrease) {
      increase = newIncrease
    }
  }
}
```

## Iterable

As a generator is iterable it can be used within a for...of loop to loop over the values.

```typescript
let total = 0
for (const value of generator) {
  total = total + value
}
```

You can also use the spread operator to grab all the values from a generator

```typescript
const values = [...generator]
```

## Use cases for generators

Generators are good for lazily doing calculations on demand rather than having to calculate something fully up front. This can be useful for dealing with things like large ranges. Rather than creating a large dataset, holding it in memory, and then iterating over it, you can use a generator to calculate each value on demand.

They can also be helpful for when you don't initially know how many values you will need. The generator will be able to be called on demand each time the next value is needed.

If you want the code to any of these examples, you can check out my repository [here](https://github.com/MartinT86/generator-example)
