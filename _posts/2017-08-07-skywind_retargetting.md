---
layout: post
title: Retargetting Tools For Skywind
tags:
- tool
- maya
- gamedev
- animation
- portfolio
date: 2017-04-26 00:00
---


<iframe src="https://player.vimeo.com/video/167897879" width="640" height="360" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>


### Pipeline tools for animation generation
<!--more-->

![Nixhound example](\blog\assets\retargeter\nixhound.gif)

As the animation lead on [TESR Skywind](https://www.youtube.com/watch?v=PewuaPKnhnc), part of my role is overseeing the animation pipeline for the team. These tools were built to accelerate the animation retargetting portion of the rigging pipeline, as well as to reduce the workload for animators on the team. 

## Background
[Skywind](https://www.youtube.com/watch?v=PewuaPKnhnc) is a full recreation of the 2002 game [Morrowind](https://en.wikipedia.org/wiki/The_Elder_Scrolls_III:_Morrowind) in the Skyrim engine with updated visuals and gameplay. The project is a massive undertaking and involves over 100 active volunteers. My role is head of the animation department, leading a small but dedicated team of animators, riggers, and programmers. In addition to functioning as a producer and recruiter I also work on animation asset creation and pipeline tools.

By far the vast majority of work that goes through the department is creature-focused. Morrowind has a large and diverse cast of creatures that were not included in Skyrim. At the same time, we are one the smallest departments on the project, and as it is a volunteer project, all development is done in our free time. With very few animators with equally little time, we needed a solution to expedite the animation process to prevent it from becoming a bottleneck for the department. 

As a result of course we determined our best option was to work off of animation retargetted from existing Skyrim animations, for roughly 90% of our assets. 

## Core Features

In total I developed three separate tools for the retargetting stage of development. I have released open source versions for each of these, available on my [Github](https://github.com/obriencole11).

### Animation Retargetter

![Netch example](\blog\assets\retargeter\netch.gif)

![Retargetter UI](\blog\assets\retargeter\retargeterui.png)

The core tool in the set is my custom animation retargetting solution. In short this tool creates **bind nodes** that connect a **bind source** and a **bind target**. A bind source and target can be anything that can receive animation data, so typically a skeleton and a control rig. The bind node itself is a simple control, which is used to offset the **source** data and apply it to the **target**. 

![Retargetter timelapse](\blog\assets\retargeter\retargetertimelapse.gif)

The tool is relatively simple in action. The user selects a source and a target, and then chooses either to bind translation, rotation, or both. In a skeleton to skeleton based use case, typically only rotation data is needed, with just the root storing both. It is recomended that the user only transfer what is needed, as unwanted data transfer can distort the final retarget. Translation binding is typically more useful for retargetting from a rig, such as for ik or pole vector controls.

The bind is best done when both the source and target are in an idle pose, or at least are in similar stances. To better accommodate vastly different body structures, addition offsetting may be required. Which can be done non-destructively through the bind nodes themselves. The Yellow control controls translation offset, and the blue diamond controls rotation offsets.

![Node Offset Example](\blog\assets\retargeter\nodeoffset.gif)

This separation of translation and rotation is pivotal under the hood. As combining both translation and rotation offsets from the same source ruin the data, as rotation will be affected by translation.

To test the bind, the easiest method is to use an FBX import to apply animation directly onto the bind source. This method makes batch operating on the scene a bit easier to manage. 

When the bind is tested, the user can bake the bind targets directly from the tool. This way the tool cleans up all bind nodes and constraints.

![Dreugh example](\blog\assets\retargeter\dreugh.gif)

I found the results to be quite versatile, and greatly expanded the catalogue of animations we could draw from. In this extreme example, for the Dreugh, an underwater enemy, we were able to retarget data from Skyrim's Flame Astronach, with minimal cleanup required.

The design of the retargeter is based roughly on Mark Jackson's techniques for animation binding from his [Live Animation Binding](https://vimeo.com/31046583) master class. In this class he gives an overview of the technique that he has since included in his [Red9](http://red9-consultancy.blogspot.com/) toolset.

While I studied his solution, I found that for our use case it would need to be improved on. First off the tool generally **assumes technical knowledge** of the inner workings of the tool. As such, many of the settings were not explicit in their purpose, and I ultimately found unnecessary. Additionally, the tool **is hierarchy-based.** The tool stores bind nodes themselves inside the skeletal hierarchy making it difficult to locate specific nodes in the outliner. Lastly, there was **no solution for offset translation *and* rotation.** While most nodes work fine with just rotation bound, root controllers introduced a problem of requiring both translation and rotation data to be transferred. With Mark's tool root nodes would need to be snapped to the target to transfer both.

For my custom version I implemented the following improvements:
* **Flat Hierarchy Structure.** The nodes are stored in a group rather than inside the skeleton. This made accessing nodes and debugging far easier.
* **Explicit UI terms.** Settings are kept minimal, and wording accurately describes their function. This is handy when handing the tool off to less-technical artists.
* **Translate and Rotate Binding.** The solution here just required a more complex hierarchy. Using additional transform buffers on each control allowed for a better separation of the data.
* **Node Scale Control.** Simple setting that allows for control of the base scale of the node. Useful for projects with different base units.

Complete source code for the retargetter can be found [here]().

### Auto Overlapping Action

![Dreugh Tentacle Example](\blog\assets\retargeter\dreughjiggle.gif)

While retargetting works well as a base, inevitable creative differences between characters means some amount of animation cleanup will always be necessary. The amount of cleanup greatly depends on the differences in structure between the targets. 

For Skywind, a decent amount of that extra work was for secondary motion on details the source target did not have. To save a bit of this extra time, I developed a tool for automatically generating this secondary motion through a particle sim.

It has since been incorporated into a separate toolset called [Riggle]().

![Riggle Demo](\blog\assets\retargeter\riggledemo.gif)

The tool works by creating a particle goal and constraining the target to generate the motion. Then the motion is baked into the joints, and constraints removed.

![Riggle UI](\blog\assets\retargeter\riggleui.png)

At the time of writing, there are two functions available. **Point Jiggle** bakes a position based simulation to the target(s). **Aim Jiggle** is a bit more complex and add rotation based simulation by aiming at its child. If no child is in the selection, the tool places a dummy target and uses that.

![Netch Head Example](\blog\assets\retargeter\netchjiggle.gif)

![Nix Hound Antenae Example](\blog\assets\retargeter\nixjiggle.gif)

This technique was inspired by the video [Overlapping Action Through the Miracle of Physics](https://vimeo.com/196234485) by Richard Lico. However Richard has no public code available but instead provides [this source](https://www.youtube.com/watch?v=BTBZgLYO6eo&feature=youtu.be&t=490) on how the technique works. 

Using those sources as a base, I built a full tool that automatically add the effect, with additional quality of life improvements:
* **Multi-Target Baking**. Richard's custom tool appears to only work on a single target, mine will operate on any amount of joints selected.
* **UI with weight options**. Not only does mine feature a ui, it also contains setting for controlling the weight of the motion.
* **Weight Decay**. This option allows for consecutive targets in a chain to receive more or less weight. This is helpful for creating natural looking chains.
* **Looping Animation Support**. This option solves the problem of generating motion for looping base animations. This is solves by running the simulation an extra amount of times equal to the 'iterations' setting.

The full source code is available [here]().

### Batch Exporter

![Exporter UI](\blog\assets\retargeter\batchui.png)

The final tool developed for the pipeline was a versatile batch export tool. While the actual batch processing code is relatively simple, for this workflow, I needed a way to add custom commands to each batch. The solution was to add an **optional python script** that will be run for each batch iteration.

The optional script should be simple, the tool merely requires it to contain a `run()` function, that will run every command needed. For Skywind, this script contains the commands to bake bind nodes and apply the auto overlap.

![Exporter Timelapse](\blog\assets\retargeter\batchtimelapse.gif)

To save time in the future, I also abstracted this method to work for future batch scripts. I used a generic **batch config** class containing my basic batch export code. Then to create the config for Skywind, I merely inherit from the class and create a custom config.

The full source code and skywind example is available [here]().


