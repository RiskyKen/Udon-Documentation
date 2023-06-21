# Documentation - Audio Zones

## Contents

- [Contents](#contents)
- [Installation](#installation)
- [Prefabs Location](#prefabs-location)
- [Audio Occlusion](#audio-occlusion)
  - [Adding Audio Occlusion](#adding-audio-occlusion)
  - [Custom Audio Settings](#custom-audio-settings)
- [Audio Channels](#audio-channels)
- [Audio Boost](#audio-boost)
  - [Area](#area)
  - [Pickup](#pickup)
- [Toggleable Audio Barrier](#toggleable-audio-barrier)
- [Toggle Audio Zones System](#toggle-audio-zones-system)
- [Audio Blocking Layer (Advanced)](#audio-blocking-layer--advanced-)
  - [Audio Block Only](#audio-block-only)
  - [Wall Replacement](#wall-replacement)

## Installation

<mark>!!!</mark> - **Import install [RiskyKen - Core](https://payhip.com/b/cg4tN) first** - <mark>!!!</mark>

Creator Companion Install: [Package Install - VRChat Creator Companion](https://docs.google.com/document/d/1u4XdBijIuOShECT0Nvwb43c_BHeK4vfTMugFvlvQO54/edit)

Unity Package Install: [Package Install - Unity](https://docs.google.com/document/d/1yboKFSFRh2EmqESxKq5EaR8c1rdlEN4MOUtkxcWexD8/edit)

## Prefabs Location
Some parts of the documentation will refer to prefabs that come with Audio Zones. See below for how to find them.

Package install prefabs this will be under: `Assets\RiskyKen\Udon\Utils\Audio Zones\Examples\Prefabs`  
![ab2b35533f99fa923b3b95249f4624de.png](/resources/ab2b35533f99fa923b3b95249f4624de-1.png)


Creator Companion install prefabs will be under: `Packages\RiskyKen - Audio Zones\Examples\Prefabs`  
![Unity_2023-06-13_01-29-52.png](/resources/Unity_2023-06-13_01-29-52.png)


## Audio Occlusion

Audio occlusion will block the sound of player voices and avatars if they are behind a solid object like a wall.

### Adding Audio Occlusion

Find the `Audio Zones - Manager` prefab then drag it into your scene.

Now right click it and select `Unpack Prefab`.  
![117b4676690e7d1302e249d30ce5c75a.png](/resources/117b4676690e7d1302e249d30ce5c75a-1.png)

Lets select the manager and look over some of the options.  
![6a1faa21c86da410c29d05bf424185e7.png](/resources/6a1faa21c86da410c29d05bf424185e7-1.png)

**Update Rate Fast & Slow**  
How long in seconds between player's getting their audio settings updated. Default value `0.00625 = 0.5 / 80` so in a world of 80 players it will take 0.5 seconds for every players audio to get updated. Slow default 0.025 is 2 seconds.

**Target Frame Rate**  
If the frame rate falls below this value the slow update rate will be used otherwise the fast update rate is used.

**Default Audio Channel**  
Default audio channel for players.

**Occlusion Mask**  
What layers Audio Zone will check when determining if a player is behind a wall. *(note adding a lot of layers may hurt performance)*

**Default Audio Settings**  
Audio settings applied to remote players that are **not** occluded.

**Occluded Audio Settings**  
Audio settings applied to remote players that are  occluded.

**Effectors**  
List of audio effectors in the world.  
<mark> Any time an effector *(audio area or audio pickup)* is added or removed from the world, "Auto Fill Effectors" must be pressed.</mark>  

### Custom Audio Settings

Select `Default Audio Settings` under the audio zones manager.  
![346dd857d82182fc1cd53853fb1c1197.png](/resources/346dd857d82182fc1cd53853fb1c1197-1.png)

Here we can adjust player voice and avatar audio settings. The settings here are the VRChat defaults. If you ever want to change the audio settings for your world change them here, Audio Zones will override settings from other scripts.  
![cdfd388de8df179314a631d47ef789cb.png](/resources/cdfd388de8df179314a631d47ef789cb-1.png)

You can find a detailed description of each option on the VRChat wiki [player audio page](https://docs.vrchat.com/docs/player-audio) or by reading the tooltips.

Next select `Occluded Audio Settings`.  
![4c9253931592fbfac530ef5db53eb3e5.png](/resources/4c9253931592fbfac530ef5db53eb3e5-1.png)  

These are the settings used when a player is behind an audio blocking object like a wall. If you would like the player's voice to still be slightly audible when occluded, increase the voice far and voice gain values by a small amount otherwise leave everything at 0.  
![204c710da52c37733008834eeeff0c6d.png](/resources/204c710da52c37733008834eeeff0c6d-1.png)

## Audio Channels

Audio channels can segregate audio between players without the need for a wall between them. By default all players start in audio channel 0, this can be changed on the audio zone manager if you like.

First drag in the `Audio Zones - Area` prefab into your scene, unpack the prefab then move it to the location you want.  

When selecting the object we can see all the settings for this audio area. Change the audio channel value to a new number like 1. The edit collider button on the box collider can be used to change the size of the zone.  
![fa3092c918014dcf791196af8be78677.png](/resources/fa3092c918014dcf791196af8be78677-1.png)

Finally select the manager object and press the `Auto Fill Effectors` button.  
![1fb0a7ad928963275a67d6258b93265c.png](/resources/1fb0a7ad928963275a67d6258b93265c-1.png)

## Audio Boost

An audio boost or dampen can be applied to areas or pickups, this is ideal or event staff, DJs or a quiet zone.

### Area
First drag in the `Audio Zones - Area` prefab into your scene, unpack the prefab then move it to the location you want.

Now drag in an `Audio Zones - Audio Settings` prefab. Increase the voice gain and voice far on the audio settings. I am using gain 20 and far 100 for this example but you should experiment with different values to find ones that work for your use case.  
![Unity_2023-06-12_23-40-08.png](/resources/Unity_2023-06-12_23-40-08.png)

Now select the area and drag the audio settings we just created into its `Audio settings Override` slot. Remember to set a higher priority value if this area is overlapping with others.  
![Unity_2023-06-12_23-41-39.png](/resources/Unity_2023-06-12_23-41-39.png)

Finally select the manager object and press `the Auto Fill Effectors` button.  
![Unity_2023-06-12_22-34-32.png](/resources/Unity_2023-06-12_22-34-32.png)

### Pickup

There is a pickup prefab included called `Audio Zones - Microphone`, you can drag this in or add the script to an existing pickup by selecting it and pressing Add Component and searching for `Audio Zones - Pickup`.  
![Unity_2023-06-12_23-51-01.png](/resources/Unity_2023-06-12_23-51-01.png)

Now drag in an `Audio Zones - Audio Settings` prefab. Increase the voice gain and voice far on the audio settings. I am using gain 20 and far 100 for this example but you should experiment with different values to find ones that work for your use case.  
![Unity_2023-06-12_23-40-08.png](/resources/Unity_2023-06-12_23-40-08-1.png)

Now select the pickup and drag the audio settings we just created into its `Audio Settings Override` slot and drag the VRC Pickup component into the `Pickup` slot. Because pickups can be moved around the world, set a high priority value so no other effectors will interfere with it.  
![Unity_2023-06-12_23-55-50.png](/resources/Unity_2023-06-12_23-55-50.png)

Finally select the manager object and press the `Auto Fill Effectors` button.  
![1fb0a7ad928963275a67d6258b93265c.png](/resources/1fb0a7ad928963275a67d6258b93265c-1.png)


## Toggleable Audio Barrier

An audio barrier can be used to toggle audio occlusion in an area, please read the [Audio Channels](#audio-channels) section first.

To set up we will need a script that can toggle objects, I will be using my free [Object Toggle Tool](https://payhip.com/b/vWHRJ) script but any toggle script will work.

First drag setup an audio channel area the same as in [Audio Channels](#audio-channels). Place it over the area you want the audio toggled. (normally a room to block the sound of people outside and vice versa)

In my example below players on the white floor can’t hear others in the rest of the world.  
![Unity_2023-06-13_00-47-16.png](/resources/Unity_2023-06-13_00-47-16.png)

Now all we need to do is make a toggle button to toggle the audio zone area.

For my example I will create a basic button using a cube, scaled down to 0.1 size and its layer set to walkthrough.  
![2023-06-13_00-49-32.png](/resources/2023-06-13_00-49-32.png)
![Unity_2023-06-13_01-04-21.png](/resources/Unity_2023-06-13_01-04-21.png)

Now add the toggle script to the button.  
![Unity_2023-06-13_00-55-16.png](/resources/Unity_2023-06-13_00-55-16.png)

Finally we will add the audio area to the toggle objects. I also added some interaction text and set materials for the buttons on and off state.  
![Unity_2023-06-13_00-58-20.png](/resources/Unity_2023-06-13_00-58-20.png)

## Toggle Audio Zones System

The audio zones manager can be toggled to shut off the audio occlusion system. This can be a nice option to provide to players in your world.

If you already have a toggle script then simply toggle the manager object, below I will show making a toggle button using my free [Object Toggle Tool](https://payhip.com/b/vWHRJ) script.

I will create a basic button using a cube, scaled down to 0.1 size and its layer set to walkthrough.  
![2023-06-13_00-49-32.png](/resources/2023-06-13_00-49-32.png)
![Unity_2023-06-13_01-04-21.png](/resources/Unity_2023-06-13_01-04-21.png)

Now add the toggle script to the button.  
![Unity_2023-06-13_00-55-16.png](/resources/Unity_2023-06-13_00-55-16.png)

Finally we will add the audio zone manager to the toggle objects. I also added some interaction text and set materials for the buttons on and off state.  
![Unity_2023-06-13_01-06-33.png](/resources/Unity_2023-06-13_01-06-33.png)

## Audio Blocking Layer (Advanced)

**<mark>This section is unfinished.</mark>**

By default Audio Zones will use objects on the default layer to block audio between players.

Using the default layer is fine for worlds with simple geometry or that will only have a small number of players. However if you are building a world with complex geometry, a large player cap or strict performance requirement, a custom audio blocking layer can be used for better performance and control of Audio Zones.

There are 2 ways a custom audio layer can be setup.

### Audio Block Only



### Wall Replacement


![2023-06-13_01-08-15.png](/resources/2023-06-13_01-08-15.png)

![Unity_2023-06-13_01-09-18.png](/resources/Unity_2023-06-13_01-09-18.png)

![2023-06-13_01-10-02.png](/resources/2023-06-13_01-10-02.png)

![2023-06-13_01-10-57.png](/resources/2023-06-13_01-10-57.png)

![Unity_2023-06-13_01-12-02.png](/resources/Unity_2023-06-13_01-12-02.png)
