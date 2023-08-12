# Documentation - Permission System

[Main](../) > Documentation - Permission System

# Contents

- [Script Info](#script-info)
  - [Features](#features)
- [Installation](#installation)
  - [Creator Companion](#creator-companion)
  - [Unity Package](#unity-package)
- [Examples Location](#examples-location)
- [Setup](#setup)
  - [Manager](#manager)
  - [Groups](#groups)
  - [Actions](#actions)
  - [Join Audio](#join-audio)
  - [Display Wall](#display-wall)
  - [Guest Access](#guest-access)
  - [Permission Priorities (Advanced)](#permission-priorities-advanced)

# Script Info

Script to handle permissions of players in a world.

## Features

**Custom Groups**

- Create any number of custom groups for Staff, VIPs, Supporters, Friends or whatever you like.
- Build in instance master and instance owner groups. Ideal for game worlds.

**World Actions**

- Toggle Game Objects
- Change intractability of buttons (script and UI)
- Change Materials
- Change Meshes
- Press Buttons
- Call Events
- Change Tooltips
- Toggle Colliders
- Update Animator Bool
- Change UI Text Colour
- Change UI Image Colour
- Change UI Toggle State

**Join Audio**

- Play different audio file when players from different groups join the world.

**Group Display**

- Displays a list of all the players in a group.
- Highlight group players that are in the world.

**Guest Access**

- Give players temporary access to a group.

# Installation

See [Install Guides](https://riskyken.github.io/Udon-Documentation/Install%20Guides/) for installation instructions.

# Examples Location

Some parts of the documentation will refer to files inside the examples directory. See below for how to find them.

Unity Package install examples this will be under: `Assets\RiskyKen\Udon\Utils\Permission System\Examples`  

Creator Companion install examples will be under: `Packages\RiskyKen - Permission System\Examples`  

# Setup

The below steps will show you how to setup the permission system and use it's features. I recommend fully reading both the [Manager](#manager) and [Groups](#groups) sections before jumping ahead. Most of the sections below also have example scenes in `Examples\Scenes` if you prefer learning that way.

## Manager

To get started first we need a manager.

Find the `Permission System - Manager` prefab then drag it into your scene.

Now right click it and select `Unpack Prefab`.  
![cc7182e8171b6f1c4ed75e1be0f5f64a.png](resources/cc7182e8171b6f1c4ed75e1be0f5f64a.png)

**Notes:**

- There should only ever be 1 permission manager in a world.

## Groups

Now we need some groups to split users into, like Staff, VIPs or Supporters.

Find the `Permission System - Group` prefab and drag it in also and unpack it. You can place your groups anywhere in the hierarchy, I am placing mines as a child of the manager to keep things organised.

You should now rename the group, for this example I am going to name mines Staff.  
![0ff771252ccfec256ca4e35db312221e.png](resources/0ff771252ccfec256ca4e35db312221e.png)

Now select the new group you just created.  
![7cb9e7e8e7a0dca1e8b12b5e74da26e8.png](resources/7cb9e7e8e7a0dca1e8b12b5e74da26e8.png)

The first option here links to the 2nd script on this object. We can use this to link a text file to load usernames from. The text file should have 1 username per line `Examples/User Lists` has some example files. For this example I am going to drag the staff list in.  
![Unity_2023-08-11_21-15-26.gif](resources/Unity_2023-08-11_21-15-26.gif)  
A URL can also be used allowing list to be updated without reuploading the world. If both a file and URL are set the script will use the file contents until the URL is downloaded.

The other option here colour is purely for organization, I recommend setting a different colour for each group but it's not required.

Now that we have created 1 group we can easily make more by right clicking our first group and selecting duplicate. Doing this I have created 3 new groups. Create and groups you need, don't forget to change the text file or URL for the new ones.  
![7d3a8705126c4e89b22904d852265b6d.png](resources/7d3a8705126c4e89b22904d852265b6d.png)

The final thing we need to do is select the manager and press `Auto Fill Groups` all your groups should now show in it's permission groups section.
![adc83bdab273cca4054610352516f29b.png](resources/adc83bdab273cca4054610352516f29b.png)

#### **!!! --- Important Notes --- !!!**  
- Some URLs will only work if the player has untrusted URLs turned on, check [here](https://creators.vrchat.com/worlds/udon/string-loading/) for more information.
- VRChat replaces the letters in some usernames. (example Full Stops are replaced with [One Dot Leader](https://www.compart.com/en/unicode/U+2024)) Because if this I recommend copy pasting usernames form the VRChat website.  
![waterfox_2023-08-11_21-26-45.gif](resources/waterfox_2023-08-11_21-26-45.gif)
- Any time groups are added or removed the `Auto Fill Groups` button should be pressed on the manager to update it's group list.
- There are also 3 build in groups instance master, instance owner and everyone.

## Actions

Now that we have a manager and groups we can add actions to edit the world for users of different groups.

For this example I have create a small world with 3 "rooms", players can only enter the staff and VIP rooms by clicking on the doors to teleport them. We will setup actions to restrict what players can use the teleports.  
![c1c17eb8d498434202b1b63e42cb8119.png](resources/c1c17eb8d498434202b1b63e42cb8119.png)

First create a new object.  (I like creating all my actions inside one object for organization but you can create them anywhere you like)  
![75cccd588d90d35abd18714401e24c44.png](resources/75cccd588d90d35abd18714401e24c44.png)  
Now rename the new object, I am calling mines `Staff Door Action`.

Now select it and press `Add Component` then search for and add `Permission System - Action`.  
![9fee28325f0aa950298067d885927e2e.png](resources/9fee28325f0aa950298067d885927e2e.png)

Now you should see a large number of options available to you.  
![0890a080e4405addc875f4fbea428b9b.png](resources/0890a080e4405addc875f4fbea428b9b.png)  
Most of the options here should be self explanatory, when checked they will also provide some extra information.

There are a few way we could stop players entering the staff room like turning off the door or it's collider. For this example lets turn off it's intractability so the door is still visible and has a collider. First at the top check the groups we want to have access, for me that will be staff. Next check `Change Interacts` and drag the door into the `Enable Interacts` array.

The final result should look like this.  
![13eb20733a848f26bdd062fcba413c66.png](resources/13eb20733a848f26bdd062fcba413c66.png)

Now that we have one action setup we can duplicate it and quickly setup another one for the VIP door.  
![912447b414ca449fbcd370cc01c14842.png](resources/912447b414ca449fbcd370cc01c14842.png)  
This time we let staff and both VIP ranks access the door.

With this you can see the power of the action script and all the options it provides. Try playing about with some of it's different options but I would not recommend changing the priority or forbidden mode options until you have read [Permission Priorities (Advanced)](#permission-priorities-advanced)

**Notes:**

- The teleport I used in this example is part of my core package. Check [here](https://riskyken.github.io/Udon-Documentation/RiskyKen%20Core/#teleport) if you want to learn how to set it up.

## Join Audio

Adding group join audio

## Display Wall

Creating a display wall for group users

## Guest Access

Enable guest access to a group.

## Permission Priorities (Advanced)