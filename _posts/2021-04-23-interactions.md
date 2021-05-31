---
layout: post 
title: Interaction Scripting
author: Yannis Paetzelt
---

After working on the game's camera for a few weeks, it's time to start adding some logic to the first level. For planning,
our team set up a flowchart with how the players should progress through the level; what obstacles they will face, and how
they may overcome them. Having this information organised in this way makes it super easy to implement in code, because
the architecture is almost right there on the page. For reference, it took about an hour to get the basis of an interaction
system working, allowing the players to activate anything that is set up in the system. We wanted to have a really generic
system that will work all the time and allow any kind of interaction _effect_. Interaction effects are really core to the
gameplay and the progression, driving everything in the player's prance through the level.

Interactions will also tie into the objective system we have planned. We imagine a little checklist in the corner listing the
current objectives for the level; similar to the questing system in Borderlands. Objectives will be updated as the player
progresses through the level.
