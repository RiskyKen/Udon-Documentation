# Documentation - Permission System

[Main](../) > Documentation - Permission System

# Contents

- [Script Info](#script-info)
  - [Features](#features)
- [Installation](#installation)
  - [Creator Companion](#creator-companion)
  - [Unity Package](#unity-package)
- [Examples Location](#examples-location)
- [Setup](#)
  - [Permission Manager](#permission-manager)
  - [Groups](#groups)
  - [Permission Item](#permission-item)
  - [Join Audio](#join-audio)
  - [Display Wall](#display-wall)
  - [Guest Access](#guest-access)
  - [Permission Priorities (Advanced)](#permission-priorities-advanced)
# Script Info

Script to handle permissions of players in a world.

## Features

- Custom Groups
- Edit World Items
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
- Display List
- Guest Access
- Join Audio

# Installation

See [Install Guides](https://riskyken.github.io/Udon-Documentation/Install%20Guides/) for installation instructions.

# Examples Location

Some parts of the documentation will refer to files inside the examples directory. See below for how to find them.

Unity Package install examples this will be under: `Assets\RiskyKen\Udon\Utils\Permission System\Examples`  

Creator Companion install examples will be under: `Packages\RiskyKen - Permission System\Examples`  

# Setup

The below steps will teach 
`Examples\Prefabs`
`Examples\Scenes`
[Permission Manager](#permission-manager)
[Groups](#groups)

## Manager & Groups

To get started first we need a manager.

Find the `Permission System - Manager` prefab then drag it into your scene.

Now right click it and select `Unpack Prefab`.  
![cc7182e8171b6f1c4ed75e1be0f5f64a.png](resources/cc7182e8171b6f1c4ed75e1be0f5f64a.png)

Note: There should only ever be 1 permission manager in a world.


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

#### **!!! --- Important Notes --- !!!**  
Some URLs will only work if the player has untrusted URLs turned on, check [here](https://creators.vrchat.com/worlds/udon/string-loading/) for more information.

VRChat replaces the letters is some usernames. (example Full stops are replaced with [One Dot Leader](https://www.compart.com/en/unicode/U+2024)) Because if this I recommend copy pasting usernames form the VRChat website.  
![waterfox_2023-08-11_21-26-45.gif](resources/waterfox_2023-08-11_21-26-45.gif)

## Permission Item

The toggle script lets us edit items in the world depending on the player groups. Here we will setup a basic object toggle
Setup permission item

## Join Audio

Adding group join audio

## Display Wall

Creating a display wall for group users

## Guest Access

Enable guest access to a group.

## Permission Priorities (Advanced)