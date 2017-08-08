---
layout: post
title: Milwaukee Enviroment
tags:
- shader
date: 2017-04-26 00:00
---

<!-- VIDEO Thumbnail
<iframe src="https://player.vimeo.com/video/167897879" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
-->

### Assets for a shader-animation filled music video
<!--more-->

Milwaukee is a long-term project I have been working on with a fellow traditional animator [John F. Quirk](https://www.johnfquirk.com/). The project will be a music video for local artist [CYBERBULLY](https://cyberbullyallcaps.bandcamp.com/album/aby). Each of our sequences will be very different, my part however is built entirely in **Unreal Engine**. 

So far, environment assets for the first scene have been finished; a bright and dreamlike field of anemones.

## Design

![Environment Beauty Shot](\blog\assets\milwaukeescene\beauty1.gif)

![Environment Beauty Shot 2](\blog\assets\milwaukeescene\beauty2.gif)

The first half of the video is designed to be peaceful and idyllic. A dreamlike space in which the main character blissfully explores. The world was built to resemble the real world, but should definitely feel surreal.

As a result for this first scene I decided to replicate a wide open field where all vegetation is made of tube-like anemones:

![Anemone Tree Concept Art](/blog/assets/milwaukeescene/treeConcept.png)

## Shaders

From a creative direction I wanted the world to feel alive, so idle vertex animation made perfect sense. From a technical side, I am a much better programmer than 3D artist, so procedural shader art allowed me to fill a full space with very few base assets. As a result, nearly every asset in the scene contains a procedural element and some sort of shader-based animation.

#### Anemone Grass

![Grass isolated](\blog\assets\milwaukeescene\grass.gif)

![Grass Shader Example](\blog\assets\milwaukeescene\grass_shader.gif)

![Grass Vertex Color](\blog\assets\milwaukeescene\grass_vert.png)

![Grass LOD](\blog\assets\milwaukeescene\grass_lod.png)

#### Anemone Trees

![Trees isolated](\blog\assets\milwaukeescene\tree.gif)

![Tree Shader Example](\blog\assets\milwaukeescene\tree_shader.gif)

![World Space Seed Example](\blog\assets\milwaukeescene\tree_variations.gif)

![Tree Vertex Color](\blog\assets\milwaukeescene\tree_vert.png)

#### Clouds and Distant Mountains

![Skybox isolated](\blog\assets\milwaukeescene\clouds.gif)

![Mountain Shader](\blog\assets\milwaukeescene\mountain_shader.png)

![Cloud Shader](\blog\assets\milwaukeescene\clouds_shader.png)

#### Walkway

![Walkway isolated](\blog\assets\milwaukeescene\walkway.gif)

![Walkway Shader](\blog\assets\milwaukeescene\walkway_shader.png)

![World Texture Example](\blog\assets\milwaukeescene\walkway_worldspace.gif)

![Shader Clipping Example](\blog\assets\milwaukeescene\walkway_clipping.gif)

![Shader Texture Sample](\blog\assets\milwaukeescene\walkway_mask.png)