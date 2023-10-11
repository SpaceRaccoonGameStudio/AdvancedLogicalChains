# Advanced Logical Chains
Tired of the monotonous creation of entity binding logic? Constantly thinking about replication? Saving states? With our plugin you will forget about this.

**Advanced Logic Chains is a plugin that combines several components to create complex logic based on event-like signals and states**

Spend your time making the game, not solving problems

📺Trailer: [Click here to watch on YouTube](https://youtu.be/ORbq8y8v53c)

📂Demo project: [Click here to download](https://drive.google.com/drive/folders/1iB-wzi5HbQ1Z6RaKk9LkEErb7-Z9iFu6?usp=sharing)

📂Example project for owners: [Click here to download](https://drive.google.com/drive/folders/1H2EZMnxkOb9KNYtfeYfUN-U6V6ydbAlO?usp=sharing)

📝Changelog: [Click here to see](https://github.com/SpaceRaccoonGameStudio/AdvancedLogicalChains/blob/main/CHANGELOG.md)

➡️Roadmap: [Click here to watch on YouTube](https://github.com/orgs/SpaceRaccoonGameStudio/projects/2/views/1)

🚧Issue tracker: [Click here to watch on YouTube](https://github.com/SpaceRaccoonGameStudio/AdvancedLogicalChains/issues)

💬Support Discord group: [Click here to join](https://discord.gg/4FtCJnMuxb)

✅Our other plugins: [Click here to see](https://www.unrealengine.com/marketplace/en-US/profile/Space+Raccoon+Game+Studio?count=20&sortBy=effectiveDate&sortDir=DESC&start=0)

# Table of content:
 - [Features](#features)
 - [How it is work?](#how-it-is-work)
 - [Instalation](#installation)
 - [Components](#components)
 - [Editor mode](#editor-mode)
 - [Project settings](#project-settings)
 - [Console commands](#console-commands)
 - [Examples](#examples)

# Features

* Fast and easy construction of gameplay logic
* Custom editor mode for easy creation and debugging
* Full multiplayer support
* Accelerated creation of logic in blueprints
* Easy integration
* Not need use soft/hard references pointers
* Fully written in C++
* Optimized for big worlds (full world partition support)
* Production ready


# How it is work?

## Simplified scheme of work
![alt_text](images/sheme_v.jpg "sheme")

## Core

The plugin is based on three components - **Logical state**, **Logical receiver** & **Logical generator** components. 
Components are connected to each other using signals and states. 

![alt_text](images/image_1.png "components")


## Signal
![alt_text](images/signal_desc.png "signal")

Signal are a structure containing:

1) **Type** (e.g. Logical, Electricity, Wind, etc) - This is a special gameplay tag that describes the type of signal. By default there are several ready-made types, but they can be easily extended by adding new tags
2) **Channel** (e.g. 0, 1, etc) - Channels are necessary in order not to use a huge number of unique signal types. At their core, they are gameplay tags and can also be expanded by adding new tags.
3) **Format** - Signal format: Infinity or Impulse, currently only Infinity type is supported.

## State

# Installation

First you need to install the plugin on the engine. You can do this through the official epic games launcher.

![alt_text](images/image_2.png "Installation")


## Using plugin as project plugin

If you want use plugin as project plugin you can manually copy plugin from “**Engine/Plugins/Marketplace/LogicalChains**” folder to you “**Project/Plugins/LogicalChains**” folder

**WARNING: FOR SUCCESSFUL PACKAGE BUILD - YOU NEED USE C++ PROJECT!**

# Components
## Logic State Component
Basic element in the construction of chains. The component settings specify an array of states in which the actor can be.
It is used to switch the states of actors - it can happen manually (for example from blueprints), based on replication, or using a **Logical receiver component**. 

**Logical state component is required for all actors that want to receive or send signals**, it serves to connect signals and logic inside the actor.

**For example:**

**Light bulb**: activated, deactivated, broken

**Sun**: day, night, morning, evening

**Door**: open, closed, locked

## Logical Signal Generator Component
Generates signals based on the state of the actor.

**For example:**

**Diesel generator**: when activated, it generates noise and electricity. When deactivated, it generates nothing. When broken, it generates only noise.

## Logical Signal Receiver Component
Changes the actor's states based on received signals from other actors.

**For example:**

**Light bulb**: when it receives electricity, it changes state to activated. If the electrical signal is lost, it switches to a deactivated state (provided that the light bulb is not in the broken state).

# Editor mode

The mode is used to conveniently configure logical signal chains with support for real-time debugging

![alt_text](images/editor_mode.png "Editor mode")

**Enable logical chains editor mode:**

![alt_text](images/editor_mode_enable.png "Enable editor mode")

**Easy draw debugging controls inside editor mode:**

![alt_text](images/editor_mode_debug.png "Editor mode debug")

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


# Examples

## Create simple logic

We will consider the work with the plugin by example.

Create two new actors and name it **BP_Generator** and **BP_Light_Bulb**

![](images/examples/example_1/1.png)

Create new **LogicalStateDataAsset** and name it **DA_States_Default**

![](images/examples/example_1/2.png)

Add two new lines to the data asset: **Activated** and **Deactivated**

![](images/examples/example_1/3.png)

Add Logical State and Logical Signal Generator components to BP_Generator

![](images/examples/example_1/4.png)

In the **Logical State** component settings, select **DA_States_Default** as **Parent States** and **Deactivated** as **Initialization State**

![](images/examples/example_1/5.png)

In the **Logical Signal Generator** component settings, add a new Generator Signal.

In the signal settings, add a new element to the **Activation States** array - Activated (This is the state in which the signal will be generated).

Add a new item to the Signals array and select your signal type tag and signal channel tag.

![](images/examples/example_1/6.png)

Add **Point Light**, **Logical State** and **Logical Signal Receiver** components to **BP_Light_Bulb**

![](images/examples/example_1/7.png)

In the **Logical State** component settings, select **DA_States_Default** as **Parent States** and **Deactivated** as **Initialization State**

![](images/examples/example_1/8.png)

In the **Logical Signal Receiver** component settings, add new Signals to Receive.

In the signal settings, set **Activated** to **State on Signal** and **Deactivated** to **State on Lost Signal**.

Add a new item to the Signals array and select the same signal type tag and signal channel tag.

![](images/examples/example_1/9.png)

Add a new event to the **Logical State** component **OnStateChanged**

![](images/examples/example_1/10.png)

Add a switch node

![](images/examples/example_1/11.png)

In the switch node settings, click the **Add All States** button

![](images/examples/example_1/12.png)

Add **Set Visibility** for **Point Light**

![](images/examples/example_1/13.png)

Add our two actors to the map and switch the editor to **Logical Chains mode**.

![](images/examples/example_1/14.png)

![](images/examples/example_1/15.png)

![](images/examples/example_1/16.png)

To test it, let's add some code to the level blueprint (If you have an interact system in your project, you can use it)

![](images/examples/example_1/17.png)

Now we can check

![](gifs/Gif1.gif)

Now let's try adding a switch and extra bulbs to our circuit

Create new actor and name it **BP_Switch**

Add **Logical State** and **Logical Signal Generator** components

![](images/examples/example_1/18.png)

**Logical State Component** settings

![](images/examples/example_1/19.png)

**Logical Signal Generator** settings

![](images/examples/example_1/20.png)

It's the same **BP_Generator** that generates a different signal, but in it, we'll add a visual display of the toggle. In the State component, select OnStateChanged event

![](images/examples/example_1/21.png)

And add your logic, in my example we just change the color of the cone

![](images/examples/example_1/22.png)

On the map in the settings of the bulb, change the conditions, adding a new signal required to turn on the bulb

![](images/examples/example_1/23.png)

Add **BP_Switch** to the map and code to check work in level blueprint

![](images/examples/example_1/24.png)

![](gifs/Gif2.gif)

We can also add additional bulbs, and each bulb can be configured to behave separately. (in the example, the top bulbs are connected only to the generator, the right one to the switch and the generator).

![](gifs/Gif3.gif)

## Example in demo project

