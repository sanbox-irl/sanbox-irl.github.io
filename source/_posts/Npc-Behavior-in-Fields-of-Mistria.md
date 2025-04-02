---
title: Npc Behavior in Fields of Mistria
date: 2025-03-22 16:40:38
tags:
---

I received this email many months ago:

> Huge fans of what you and your team have done!...
>
> We have been having a problem in our game with parsing out NPC paths and schedules; how to break apart what they will do on a given day based on the weather and the calendar...But I was wondering if you had a design philosophy that has worked best for you? Do the schedules change dynamically throughout the day or are they static for the calendar and weather conditions? What has worked best when it comes to storing schedule data on the dev side?...
>
> Thank you for reading!
>
> Best,
>
> Ryan M

First of all, Ryan, opening with flattery was the right move. Secondly, this response is long overdue, but your question is large and will take more than a few blog posts.

There are three elements to this (well, really two, but I'm going to be long-winded):

1. How do NPCs behave within their 2D environment?
2. How do NPCs decide what to do on a given day or on a given time?
3. Finally, the unasked question, but how do NPCs decide what to say?

These three questions are divided between the micro and macro levels, which maps neatly to the *database* level and the *gameplay* level. It's simpler to start with the gameplay, so let's start there.

## How do NPCs Behave

NPCs like to be 

In my opinion, Npc behavior in farming sims is by far the most difficult problem. A significant amount of paper cuts can occurs in the player experience was farming sims complexify. This difficulty comes from a few constraints:

- Farming sims are *hairy* or *shaggy*: they have a large number of sub-features which combine to create many shallow gameplay features.
- Farming sims have a large amount of user-generated content, particularly around placing furniture and decorating.
- Farming sims feature lots of long-lived AI agents who players can have a romantic relationship with. This creates a need for *verasimilitude*, or the pursuit of realism, since players want to believe that these AI agents are real people.

There are a few general principles to achieve these effects, which I'll go over, and then I'll dive into how we generate schedules with Npcs in *Fields of Mistria*. Later, I'd like to make a blog post explaining how we choose conversations for Npcs as well.

First, **Npcs should avoid teleportation.** This rule is effectively meant to be broken, since you will constantly need to teleport Npcs, but the more you avoid it, the more Npcs will feel realistic and the less they'll feel like a construct. For example, if an Npc needs to get from one room to another room, they should walk there, rather than teleport there when out of sight of the player. Players should therefore be able to follow Npcs everywhere they go.

Secondly, Npcs should react to the changing world around them, especially at a realistic delay. To follow the first rule, you may have made a node-based path system, so Npcs would walk a predefined set of paths. This approach unfortunately fails to take account changes in the environment. The most obvious environmental effect is, of course, the player, who can stand in the way of Npcs. Npcs can just walk through the player of course, but when we do that, we hurt the verasimilitude of the world -- the Npcs will feel fake. Moreover, if you have placable furniture anywhere the Npcs can walk, then you will need to handle their reactions to that furniture's placement, either walking through the furniture (perhaps destroying it as they do), or pathfinding around the furniture.
