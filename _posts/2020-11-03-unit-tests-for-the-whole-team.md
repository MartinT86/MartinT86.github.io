---
layout: post
title: "Unit tests for the whole team"
description: "Unit tests should provide value for the whole team as living documentation"
tags: [jest, Unit Tests, documentation]
---

I don't think it's possible to overstate the importance of unit tests. Ideally they'd be created through following test driven development but that's a whole different conversation. 

But by sharing your unit tests with your team, through HTML reporters you can get even more value out of them as living documentation.

## What unit tests do

A strong set of unit tests gives several huge benefits to a system.

For example, unit tests allow for small feedback loops of testing the whole system, reducing the need for full manual regression tests for each code change. In turn, this increases the confidence that code changes won't break the system.

Similarly, refactoring would be very difficult without unit tests. Without your tests to rely on, you would be spending a lot of time manually testing your system after every code change.

A sometimes overlooked benefit of unit tests is the living documentation that they can form. By reviewing the test suite it should be clear what the system does.

## Living documentation

Often, tacit knowledge and knowledge silos grow over time within a team. Moving that knowledge out the developer's head into a more public realm is hugely useful.

Documentation is great, with one major caveat, only when it is kept up to date. Keeping documentation up to date is easier said than done. For every change to the system, making sure it is reflected in the documentation can be a considerable overhead. Especially when changes need to be made quickly, this overhead is easily and often overlooked. Incorrect, or outdated documentation can be very damaging.

An ideal situation is where the documentation is based on the code itself. A strong set of tests that test the behaviour of a system can form living documentation. You should be able to read through your test suite and know exactly what the system does and how it will behave in various scenarios.

## Jest reporters

A strong set of tests that form living documentation of the team should benefit more than just developers. All members of the team should have access and be able to benefit from the documentation.

If you're using Jest as your testing framework, you can help all members of the team use the tests through using a Jest reporter.

There are various types of jest reporters that are available. Dot reporters, reporters that show the slowest tests, reporters that show skipped tests, etc. You can even write your own reporter. Check out [awesome-jest](https://github.com/jest-community/awesome-jest#reporters) for a list of useful reporters, and other great jest tools.

For making a test suite available and useful to the whole team I was interested in the html reporters. The three I played with were;

* [jest-html-reporter](https://github.com/Hargne/jest-html-reporter)
* [jest-stare](https://github.com/dkelosky/jest-stare)
* [jest-html-reporters](https://github.com/Hazyzh/jest-html-reporters)

Honestly, I was impressed by them all. They were all easy to setup, and all produced a nice html report that was easy to share and read. 

To set up a reporter and use the defaults, all you need to do is import the package 

    npm install jest-stare --save-dev

Then add the reporter to the list of reporters in the jest config, for example

    module.exports = {
        verbose: true,
        reporters: ["default","jest-stare"]
    };

Once your tests have run, the reporter will output an overview of the tests. 

<div class="center">
<figure>
	<a href="{{ site.url }}/images/jest-stare-example.png"><img src="{{ site.url }}/images/jest-stare-example.png" alt="Example html test report"></a>
	<figcaption>Example html test report</figcaption>
</figure>
</div>

## Collaboration

So you've got your test suite, your tests are well named and test the behaviour of the system (not just a reflection of the code), and now you've got your nice html report for your tests. Make sure you use it!

Share it with the wider team, ideally as part of your CI process. Maybe email it on each deployment? Maybe host the report somewhere so people can access it? However it would work for your team, but make sure all members of the team can see it some how.

This effort of transparency of the system should give a lot of value. If anyone has any questions about what the system does, they now have living documentation they can refer to!