---
title: What Are Mixels?
date: 2025-04-20 13:19:20
tags:
---

No, like really, what are they?

This article is a programmer's guide to working with pixel art. Particularly, I'm writing for programmers who think they know what they're doing in general, but want to have a more rigorous approach to pixel art. Working on *Fields of Mistria*, at the beginning (more than half a decade ago), I'd constantly be told "that's a mixel, we can't have those" and I'd have no idea what artists were talking about. Eventually, I developed an intrinsic sense of what a "mixel" was, mostly visually, but I wanted to have a more rigorous understanding of it. This article is my attempt at exactly that.

We'll start by gathering examples of what people tend to call "mixel" art. After that, I will try to rigorously define pixel art, where we'll find that a reasonable definition of a "mixel" naturally emergees. Afterwards, we'll walk through how, as a programmer, you can avoid making mixels in your own games, and why sometimes, you'll want to have mixels anyway.

## Mixel Gallery

There are many games with mixels, but interestingly, the phenomenon is mostly a modern one, so let's go over some indie games that are commonly said to have "mixels".

> That mixels largely appear in modern titles is a *hint* as to their true nature.

![A screenshot of *Celeste* showing both high and low resolution artwork](celeste.png)

There are generally agreed to be "mixels" in the above image -- though I'm not sure if the in-game artwork is the mixel or if the User-Interface (UI) is the mixel, but no matter what, they are "mixed" together. *Celeste* will be a very interesting case going forward as they are, in some ways, more of a pixel purist than any other game we'll go over.

![A screenshot of up-coming game *TetherGeist* showing both high and low resolution artwork](tethergeist.jpg)

*TetherGeist*, an upcoming game (which I've contributed a small amount of work to), also mixes "high resolution" UI screenshots with "lower resolution" pixel art.

> If it's not clear, I'm pretty disatisfied with the loosiness of these definitions and terms. We'll be making these much more concrete as we go forward.

*Stardew Valley*, one of the best games ever made, is also widely understood to have mixels. Rather than mix UI and gameplay assets, the game itself has "mixels" in it:

![A gif of a character in Stardew Valley breathing.](./stardew_valley_breathing.gif)

This *Stardew* example is obviously different than the above *Celeste* and *TetherGeist* examples, but both are often described as mixels! Whereas *Celeste* and *TetherGeist* have two different "resolutions" they're working with (once again, whatever that means), *Stardew Valley* only has one resolution. However, it's willing to distort its pixel art within that resolution by altering sizes.

Sometimes programmers will claim that all you need to know for pixel art is to avoid non-integer scaling,or sometimes they're more onerous and it's power-of-two scaling that's required, and all will be good, but even these methods would produce mixels in my opinion:

![A gif of a character in Stardew Valley going from 1x to 2x to 4x next to another character](./stardew_valley_mockup.gif)

(The above GIF has been artificially created by me and is not part of *Stardew Valley*).

Okay, that's enough for resizing problems, but let's stay with *Stardew Valley* (sorry, Eric, your game is popular).

![Rotational mixels on a sword in *Stardew Valley*. The sword should be more pixelated than it is](./stardew_valley_sword.png)

In *Stardew Valley*, rotating objects are "mixels". These examples are from this excellent post by ***USER_NAME*** [here](link_to_post.com). The above image might seem fine, and to millions of *Stardew Valley* players, it was fine, but to several dozen very motivated internet posters (yours truly, included) this rotational mixel was so damaging that it demanded its own name: the "rixel". This "rixel" involves no scaling (*or at least, not yet obvious scaling*), but it is still considered a "mixel".

There is one last mixel which I have not seen anyone else comment about online -- those are the mixels in *Fields of Mistria*.

![Player running around in *Fields of Mistria* doing *Fields of Mistria* things](./fields_of_mistria.png)

The player is currently making a mixel. Don't see it yet?

![Closeup of the player's foot, showing it blocking 1/3rd of a background pixel](./fields_of_mistria_closeup.png)

There it is! Very few pixel art purists would consider the above a mixel, but it is one, as we'll see, though for what it's worth, it is only apparent when the player is *in movement*. When the player is at a standstill in *Mistria*, all is well.

![Closeup of the player standing still in *Mistria*, no mixel positions available](./fields_of_mistria_stationary_mixel_fix.png)

All of the above are mixels. Let's see if we can make a consistent definition for a mixel to capture them all.

## What is Pixel Art?

Our goal here isn't to define "mixels" directly, but to define pixel art and then see if there's something in that definition which we can call "mixels" which captures all of the above behavior.

> An important note: ultimatley, all definitions must be treated as axiomatic and monolothic (see more [here](https://en.wikipedia.org/wiki/Structure,_Sign,_and_Play_in_the_Discourse_of_the_Human_Sciences)). Others might reasonably make different definitions for different needs.
>
> I'm also cognizant that a programmer defining pixel art is a bit much, but I'd ask my readers for some faith.

### Quantization

First, pixel art is *quantized* -- or, to put it another way, each individual unit comes within a *quantum* (plural: *quanta*). Each quantum has a size and every quantum has the same size. This kind of art is what I'll call "quantized art".

There are many examples of quantized art that no one would call pixel art:

![Greek mosaic, showing stones of roughly the size, but which do not fall in a neat grid](./greek_mosaic.png)

This mosaic is quantized to each stone which is used to create it. They aren't quite the same size, but the intended effect is that they are.

![Glass beads, with an oil spill, in a grid pattern. The oil technically makes this not quantized, but let's ignore that for now.](./greek_mosaic.png)

This sculpture is composed of glass beads, all of the same size, creating the appearance of a fine structure. Every bead is the same size.
These beads, and the stones above, roughly "tile the plane" (ie, fill up a 2d space infinitely) in a similar manner to squares, but there are exceptions as well.

![Matchstick art, composed of lots of matchsticks which have been glued together, creates another quantized art-form](./matchstick_art.png)

No doubt, matchstick purists debate whether you can break a matchstick in half in your art (a matchel), but that is beyond the scope of this article.

Finally, there is pixel art, which is obviously quantized:

