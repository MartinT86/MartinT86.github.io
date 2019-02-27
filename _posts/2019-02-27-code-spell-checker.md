---
layout: post
title: "VS Code - Code Spell Checker"
description: "Code Spell Checker is an awesome VS Code extension for spell checking"
tags: [VS Code, extensions]
---

I was looking for a spell check extension for VS Code to make writing this blog easier. After finding [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker), I recommend it as a must have extension.

Once a spelling mistake is identified, you get the classic green squiggle, then Ctrl + . will bring up the spelling suggestions menu.

<div class="center">
<figure>
	<a href="{{ site.url }}/images/spellcheck.PNG"><img src="{{ site.url }}/images/spellcheck.PNG" alt="Expo device testing"></a>
	<figcaption>Spell checking in VS Code!</figcaption>
</figure>
</div>

The extension has made writing in VS Code an awful lot easier. I didn't look for a spell checker to make coding easier, but it has had that bonus side effect.

I've never really thought about spelling mistakes in code before. Obviously if I spot a spelling mistake I'll fix it, but I've never really thought about the impact on speed of development. However, recently I've been doing a lot more work with Javascript. A couple of times already, Code Spell Checker has caught a misspelled variable name. Code Spell Checker will even catch spelling mistakes in camel cased names. With JS being dynamic, these spelling mistakes would have only been caught at run time and I would have had to track down the bug.