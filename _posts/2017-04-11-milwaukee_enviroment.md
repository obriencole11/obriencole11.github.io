---
layout: post
title: Milwaukee Enviroment
tags:
- shader
date: 2017-04-11 00:00
---


<iframe src="https://player.vimeo.com/video/233412631" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>


### Assets for a shader-animation filled music video
<!--more-->

Milwaukee is an in-progress music video I have been working on with a fellow animator for local artist [CYBERBULLY](https://cyberbullyallcaps.bandcamp.com/album/aby). Each of our sequences will be very different, my part however is built entirely in **Unreal Engine**. 

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

The primary feature of the environment is the anemone grass that fills the landscape. While certainly fitting the surreal tone, the choice of grass was also one of efficiency. As I am not much of an environment modeler, being able to fill the scene with on "model" greatly reduced the workload.

The grass is a static mesh using vertex animation in shader. To keep the field from looking too repetitive, there are several customizations added in shader using world space noise. Here is the full shader graph in unreal:

![Grass Shader Example](\blog\assets\milwaukeescene\grass_shader.gif)

The basic process goes like this:
1. Using vertex position, offset it with a sine wave, using the height mask to create a smooth blend.
2. Adjust the height and positioning a tad using world space noise
3. Add procedural color based on world space noise

A higher resolution version is available [here](\blog\assets\milwaukeescene\grassshader.png).

![Grass Vertex Color](\blog\assets\milwaukeescene\grass_vert.png)

Rather than assembling thousands of separate meshes, anemones are combined into tiles of one hundred. While being easier to manage, in order to animate correctly in shader, each anemone needed to know where its pivot was in the tile. To solve this I wrote a quick script to bake the pivot information of each anemone into the red and green channels of the mesh.

Additionally, the shader needed to be able to distinguish the top of an anemone from the bottom. I stored a simple gradient mask in the remaining blue vertex color channel to pass this information along to the shader.

![Grass LOD](\blog\assets\milwaukeescene\grass_lod.png)

For optimization purposes, I built four additional level of details for the anemones. Additionally, the vertex animation is not calculated at far distances.

#### Anemone Trees

![Trees isolated](\blog\assets\milwaukeescene\tree.gif)

The anemone trees were achieved in a similar way.

![Tree Vertex Color](\blog\assets\milwaukeescene\tree_vert.png)

Again, height information is stored in the vertex color channels. Additionally, I stored a mask for the trunk as well as the position and lengths of each branch.

![Morph Target Example](\blog\assets\milwaukeescene\tree_variations.gif)

To differentiate the trees further, morph targets were stored in the UV channels and blended in shader.

![World Space Seed Example](\blog\assets\milwaukeescene\tree_variations.gif)

All procedural additions use worldspace position as the seed. So by placing the trees around the map, they are naturally randomized.

Here is the shader graph for the trees:

![Tree Shader Example](\blog\assets\milwaukeescene\tree_shader.gif)

Its a bit more complex than the grass as more movement is being calculated. The process looks like this:
1. Rotate the trunk and branches using a sine wave
2. Offset the trunks height and width
3. Lengthen or shorten the branches
4. Bend the tree into different poses using the morph targets
5. Add procedural color

You can find a high res version [here](\blog\assets\milwaukeescene\treeShader.png).

#### Clouds and Distant Mountains

![Skybox isolated](\blog\assets\milwaukeescene\clouds.gif)

The skybox was achieved entirely through procedural noise. No static textures!

The clouds are panning, low-level voronoi noise. The color is clamped to create solid shapes. The mountains are a sphere masked halfway up. The mask is offset by a bit of smooth noise to create the rolling hills.

#### Walkway

![Walkway isolated](\blog\assets\milwaukeescene\walkway.gif)

The walkway uses worldspace noise and tessellation to create organic looking grooves. Because the texture is generated in shader, no uv mapping is necessary, reducing the workload to iterate on the shape and size of the walkway.

![World Texture Example](\blog\assets\milwaukeescene\walkway_worldspace.gif)

Because the texture is generated in world space, there is no need for traditional texturing.

![Walkway Shader](\blog\assets\milwaukeescene\walkway_shader.png)

The walkway shader graph is rather simple in comparison. Noise is generated and then used as both a gradient ramp for the color as well as a height map.

![Shader Clipping Example](\blog\assets\milwaukeescene\walkway_clipping.gif)

In order to meld with the grass easily, I wrote a script to bake the worldspace position of the walkway into a texture. The grass shader then uses this as a mask. Here is an example of the results:

![Shader Texture Sample](\blog\assets\milwaukeescene\walkway_mask.png)