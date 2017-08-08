---
layout: post
title: Satellite Love
tags:
- portfolio
- game
- unity
- project
date: 2017-04-27 00:00
---


<iframe src="https://player.vimeo.com/video/197728485" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>



### Satellite Love is a non-linear visual novel
<!--more-->

Built for the [A Game By Its Cover](https://itch.io/jam/a-game-by-its-cover-2016) Game Jam, Satellite love is a visual novel prototype in which the player has conversations with various satellites orbiting earth. This was primarily a solo project, I handled all the programming and art assets. It was built over the course of a month in the Unity engine.

![](/blog/assets/satellitelove/satelliteLove.gif)

Each satellite was unique, using randomly assembled character portraits

### Programming

The premise of the game was built around the idea of doing a procedural visual novel, one where each run would feel new a unique.

<strong>I had several programming tasks:</strong>

* A procedural satellite generator
* A basic dialog system
* Hooking up the game with a spreadsheet for easy content entering
* An event system to handle the game flow

### Shaders and FX

This project was a fun one shader wise. I wanted to emulate a hand-drawn art style, but have as much control as I can. I ended up working most of the hand-drawn effects into custom shaders. Here's a couple of my favorites:


#### Animated fill shader

I created a shader that would give the impression of the art being drawn in real time. The shader takes a texture and a gradient ramp, and uses a 'fill' variable that can animate the drawing.

![](/blog/assets/satellitelove/titleShader.gif)

<strong>The title animation was controlled through a shader
</strong>

![](/blog/assets/satellitelove/portraitDemo.gif)

A similar shader was used for the character portraits

#### Satellite Icon Shader

I wanted more control over the satellite icons as well as have infinitely scaleable textures. To achieve that, I ended up actually calculating the texture and animation all in shader.

![](/blog/assets/satellitelove/satelliteShader.gif)

The satellite sprites were generated entirely in shader

#### Shimmer Shader

To further capture the hand-drawn style, I wanted to emulate the common 2D animation practice of using "shimmer" frames. For textures I used a shader that distorted the uvs based on Gaussian noise. For the outline of the planet I actually used perlin noise on a line renderer. For both instances, time was stepped to be at a slower framerate to give the impression of being traditionally animated.

![](/blog/assets/satellitelove/finalTitle.gif)

Noise was added to assets to create a hand drawn look

![](/blog/assets/satellitelove/noise.gif)

The planet outline used perlin noise on a line renderer