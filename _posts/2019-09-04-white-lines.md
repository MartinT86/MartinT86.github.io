---
layout: post
title: "White Lines"
description: "White lines blowing through my code (and what to do about it)"
tags: [Refactoring, Code smells]
---

White space can be very helpful but in the wrong places it can be sign that a bit of refactoring might be helpful.

## Why blank lines in code are a problem

Adding in a blank line often feels like a natural thing to do while programming. Just like adding a full stop at the end of a sentence, a blank line can finish a thought.

However, if a function has these blank lines breaking up the code, that can be a sign that there is more than one thought in a function. If there are clumps of lines together it is usually a sign that methods or classes could be extracted.

In this example, blank lines have been used to separate the logic for the calculating the subtotal and the discounts.

    function CalculateTotal(products, priceList) {
        let subTotal = 0
        products.forEach(product => {
            subTotal += priceList.getPrice(product)
        });

        let discounts = 0;
        if(products.filter(product => product.inDiscount).length == 2) {
            discounts = 20
        }
        if(products.filter(product => product.inDiscount).length > 4) {
            discounts = 40
        }

        const total = subTotal - discounts
        return total
    }

Uncle Bob has a great analogy for why people like to break code up with things such as blank lines. He likens finding your way around a code base like that to recognising features in a landscape. When someone knows an area they might use landmarks such as mountains on the horizon to know where they are. The shape of the code can act in the same way. However if you don't know the area those landmarks offer little help, just like blank lines offer little help in an unfamiliar code base. Well extracted and named functions or classes are a much nicer way to navigate without that tacit knowledge.

## How to deal with blank lines

As I've mentioned, a straightforward refactoring you can do if you have logical groups of lines broken up by blank lines is to extract those groups in to methods.

The example has been refactored by extracting out the logic to new functions.

    function calculateTotal(products, priceList) {
        const subTotal = calculateSubTotal(products, priceList)
        const discounts = calculateDiscount(products)
        const total = subTotal - discounts
        return total
    }

    function calculateSubTotal(products, priceList) {
        let subTotal = 0
        products.forEach(product => {
            subTotal += priceList.getPrice(product)
        });
        return subTotal
    }

    function calculateDiscount(products) {
        let discounts = 0;
        if(products.filter(product => product.inDiscount).length == 2) {
            discounts = 20
        }
        if(products.filter(product => product.inDiscount).length > 4) {
            discounts = 40
        }
        return discounts
    }

Further refactoring should be done on this example, but by extracting the logic clumps to their own functions, rather than using blank lines, the intent is much clearer.

If you have several groups of lines and they are sharing data, it might make sense to extract a class during your refactoring.

I have seen some push back against this advice. I've heard comments like, "these functions are too small now" or "that's too many files in the project". But for me, many small, well named things are much easier to navigate my way around though.

I loved Martin Fowler's example of a small function though. In his book, Refactoring, he tells of the example from Smalltalk of a single line function called Highlight which only calls the function Reverse. While this is a single line function, it still made the code easier to understand. 

So like all code smells, I wouldn't say blank lines in themselves are a problem, but they might be a sign that a useful refactoring may be a good choice.
