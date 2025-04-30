---
title: What Are Mixels?
date: 2025-04-20 13:19:20
tags:
---

No, like really, what are they?

This article is a programmer's guide to working with pixel art. Particularly, I'm writing for programmers who think they know what they're doing in general, but want to have a more rigorous approach to pixel art. Working on *Fields of Mistria*, at the beginning (more than half a decade ago), I'd constantly be told "that's a mixel, we can't have those" and I'd have no idea what artists were talking about. Eventually, I developed an intrinsic sense of what a "mixel" was, mostly visually, but I wanted to have a more rigorous understanding of it. This article is my attempt at exactly that.

We'll start by trying to rigorously define pixel art and hopefully find that a reasonable definition of a "mixel" falls out of these other definitions. Afterwards, we'll walk through how, as a programmer, you can avoid making mixels in your own games. If all you've heard is to "avoid non-integer resizing", keep reading, as there's quite a lot more to it than that!

Let's start with a very basic definition of a "mixel" -- in "pixel art" games (whatever that means), a mixel is generally seen as a pixel of an "incorrect" size. This incorrect size is most definitely seen when games mix "high resolution" art and "pixel art" together, such as in *Celeste*:

![A screenshot of *Celeste* showing both high and low resolution artwork](celeste.png)

There are generally agreed to be "mixels" in the above image -- though I'm not sure if the in-game artwork is the mixel or if the User-Interface (UI) is the mixel, but no matter what, they are "mixed" together. *Celeste* will be a very interesting case going forward as they are, in some ways, more of a pixel purist than any other game we'll go over.

![A screenshot of up-coming game *TetherGeist* showing both high and low resolution artwork](tethergeist.jpg)

*TetherGeist*, an upcoming game (which I've contributed a small amount of work to), also mixes "high resolution" UI screenshots with "lower resolution" pixel art.

> If it's not clear, I'm pretty disatisfied with the loosiness of these definitions and terms. We'll be making these much more concrete as we go forward.

*Stardew Valley* is also widely understood to have mixels. Rather than mix UI and gameplay assets, the game itself widely has "mixels" in it:
