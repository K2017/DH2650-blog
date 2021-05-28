---
layout: post 
title: Designing Objectives is Hard
author: Yannis Paetzelt
---


For Hop to it!, we agreed that we wanted objectives to be one of the main guiding mechanics for the player, and the
main indicator for progression through the game. As such, the objective system had to be robust and flexible enough
to allow us to freely design the player's romp through each level.

Turns out this is a difficult set of requirements to match in practice without limiting how the player may interact with
the game. There are many factors to take into account: can the player interact with things multiple times? Should the
player be able to complete objectives out of order? Can the player fail objectives? How should an objective look in the
UI?

All of these things greatly affect the kind of implementation we would end up with.

### Implementation
As the lead programmer on the team, my job was to put in the work and produce a system that meets our requirements. I 
started by looking at how the previous system I had worked on, the Interactable system, could be tapped into to enable
objectives. The programming pattern I thought would fit best here was something akin to the observer pattern, where the
idea was that an Objective would observe the Interactable it had as a requirement for completion. Once the player
interacts with the correct Interactable, the Objective receives an update and reevaluates its completion status. Rather 
than implement the observer pattern directly using the interfaces provided in C#, I based the implementation on 
event-driven programming by tapping into an event provided by Interacatables.

### Limitations
This kind of one-to-one mapping from Interactable to Objective worked well for most of the things we wanted the player
to do, like having an objective to turn on the light by interacting with a light switch in the level. A limitation of
linking the system to concrete Interactable components was that we could not have objectives that depended on objects
that did not exist in the level at edit time. As an example, we wanted to have an objective where the player must
take a food item out of the fridge or the microwave, and eat it. This was not directly possible since you can't create 
an objective without a reference to an exiting Interactable, in this case the food item. A workaround would be to use 
something like object pooling to certain objects always loaded in the level, and only have them be visible when required.
This way the Interactable could be linked to the Objective.

That previous example with the fridge and the microwave also highlights another limitation of the one-to-one mapping.
You can't have an objective that depends on multiple things being interacted with, or an objective that depends on
one ore another Interactable having been interacted with. Basically disjunctive and conjunctive objectives were not
supported.

For the simple objectives of the first level, this kind of system is sufficient however, and nevertheless it is designed
in such a way that I can extend it with these features if necessary for other levels.
