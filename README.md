# Advanced Logical Chains
Do you need to create complex game logic? Then this plugin is made for you.

Forget about soft references, "actor picker", manual creation of links and other things - now this is a thing of the past.

**Create complex gameplay logic based on states and signals in a couple of clicks!**

# Features

* Fast and easy construction of gameplay logic
* Custom editor mode for easy creation and debugging
* Full multiplayer support
* Accelerated creation of logic in blueprints
* Easy integration
* Not need use soft/hard references pointers
* Fully written in C++

# Table of content:
 - [How it is work?](#how-it-is-work)
 - [Instalation](#installation)
 - [Project settings](#project-settings)
 - [Console commands](#console-commands)
 - [FAQ](#faq)
 - [Support](#support)


# How it is work?

The plugin is based on three components

![alt_text](images/image_1.png "components")

# Logic State Component
Basic element in the construction of chains. The component settings specify an array of states in which the actor can be.

**For example:**

**Light bulb**: activated, deactivated, broken

**Sun**: day, night, morning, evening

**Door**: open, closed, locked

# Logical Signal Generator Component
Generates signals based on the state of the actor.

**For example:**

**Diesel generator**: when activated, it generates noise and electricity. When deactivated, it generates nothing. When broken, it generates only noise.

# Logical Signal Receiver Component
Changes the actor's states based on received signals from other actors.

**For example:**

**Light bulb**: when it receives electricity, it changes state to activated. If the electrical signal is lost, it switches to a deactivated state (provided that the light bulb is not in the broken state).


# Installation

First you need to install the plugin on the engine. You can do this through the official epic games launcher.

![alt_text](images/image_2.png "Installation")


## Using plugin as project plugin

If you want use plugin as project plugin you can manually copy plugin from “**Engine/Plugins/Marketplace/LogicalChains**” folder to you “**Project/Plugins/LogicalChains**” folder


## Example project

Also if you want you can download an [example project](https://github.com/SpaceRaccoonGameStudio/AdvancedLogicalChains)


# Project settings

The project settings contain the main settings for debugging the plugin. You can find it in "**Project settings -> Game -> Advanced logical chains**"

![alt_text](images/image_3.png "Project settings")

**Dashed Line Color** - setting the color of the dotted line connecting generators and receivers.

**Draw Lines** - whether or not to display connecting lines.

**Dashed Line Speed** - speed at which the dashed line will move.

**Offset Between Dashed Lines** - vertical offset between signal lines.

**Debug Draw Max Distance** - the distance from the camera at which to stop drawing lines.

**Draw Sprites** - whether or not to display components sprites.

**Draw Component States** - whether or not to display component states in runtime debug.

# Console commands

**LogicalChains.ToggleStatesDebug** - text debug for actor state

**LogicalChains.ToggleRuntimeDebug** - dashed line debug

**LogicalChains.DebugDraw.OnlyActiveSignals [true/false]** - only display active dashed lines

![alt_text](images/debug_states.png "debug states")

# FAQ

Q: **Does the plugin support multiplayer?** 

A: Yes, all the logic works on multiplayer.

# Support

If you have any additional questions or suggestions, do not hesitate to express them. You can

do it through our official discord group or via email

**Discord** : [https://discord.gg/4FtCJnMuxb](https://discord.gg/4FtCJnMuxb)

**Email** : [support@space-raccoon.com](mailto:support@space-raccoon.com)
