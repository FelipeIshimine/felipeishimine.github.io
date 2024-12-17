---
title: Laugh Little Lamb (Web/PC)
date: 2024-02-02 18:10:00 -0300
categories: [my_games]
tags: [game_jam, portfolio]
author: <felipe_ishimine>
description: Game for the GGJ2024, with the theme, "Make Me Laught"
toc: false
comments: false
image:
  path: /assets/gifs/LaughLittleLamb.gif
  alt: Laugh Little Lamb gameplay
---

# [PLAY HERE](https://kodachigames.itch.io/laughlittlelamb)


# Description 
Game for the Global Game Jam 2024 with the Theme "Make me Laught" in 48hs. 
With this theme we made a puzzle game where you play as a little Lamb, that must reach their home in the middle of the night while 
being chased by hungry laughinb hienas 

## My Roles
Programming and Game Design 

## Core Objectives 

Besides the GGJ24 Theme "Make me Laugh", we also wanted to make a game that could be a "Test ground" for some features we needed to try before adding to our other main project "Legion" (https://twitter.com/PlayLegionGame). Because of that we decided to make a "Turn Based" game where multiple entities could execute "Composed Actions" in order but play their animations in "parallel" (if said animations do not share participants).

On the other hand, I personally, wanted to share an example of how some of this common programming patters could be applied to a "Real Game" instead of the common "Whiteboard examples" that people usually use on classrooms or youtube videos. Something that could have helped me when I started making games on my own 8 years ago. So if you are a beginner or a intermediate programmer this project could be of use for you. Keep in mind, this code is MY interpretation/implementation of these patterns and ideas for this especific game. You will find, bad code and bad design decisions, so take anything you see here with a grain of salt.


## Design Patterns and Ideas explored

- MVC Pattern 
    Clear separation between, Model, View, Controllers, reinforced with Assemplies, allowing for a faster and scalable script builds. This decoupling makes a lot easier to implement many of the following points.

- Command Pattern
    Every "Action" entities can perform(Walk, Rotate, Eat, TurnLightOn,TurnLightOff, etc), are encapsulated in a "Command Instance" that can "o() and Undo().

- Command History
    With Do(), Undo() and Redo() functionality

- Strategy Pattern for the control of entities with the interface IPlayer. 
    - Ai control for the Hyenas (EnemyAiController.cs), 
    - Human control for Sheep (SheepControler.cs). 
    - Ai control for Sheep (AutomaticSheepController.cs,). Only for editor special mode for automated level testing. Doesnt really work, still needs some new heuristic optimizations before it becomes useful, right now is just brute force.

- Independent Animation System which allows for 3 modes:
    - None: No animation is played. (Useful for automated testing)
    - Sequencial: Every animations goes into a Queue, and start only after the previous animation ends.
    - Parallel: Every animation starts the moment it doesnt have any "dependent" animation running. Each animation instance has an array of Participants, which is used for determining dependencies.

- 2D Pathfinding
    - Using A*, for multi destination, path finding.
- UniTask for async programming in some places for convenience.
- Automated Level Playtesting Work in progress
- Unity Tilemap System:
    - Levels are designed using the Unity TilemapSystem then a TilemapController, reads the content of the Tilemap, and generates everything it needs from it, making level making really fast and easy.
- Unity Addressables System.



Free access to the repo
https://github.com/FelipeIshimine/Laugh-Little-Lamb



