---
date: 2023-05-12 20:05
layout: post
title: How to create a renaming tool for Unreal Engine 5 in blueprints (search and replace) 
subtitle: Learn how to create asset action utilities using blueprints
description: How to create asset action utilities in Unreal Engine 5 using blueprints
image: https://tvillalbac.github.io/blog/assets/img/posts/rename-asset-action-utility-blueprints-full-unreal-engine-5.jpg
category: Unreal Engine 5
category-url: unreal-engine-5
tags: unreal-engine blueprints
author: toni-villalba-corominas
recommended: https://tvillalbac.github.io/blog/how-to-fix-up-unreal-engine-5-redirectors-cpp/
---

## What's an Asset Action Utility?

Scripted actions as the <a href="https://docs.unrealengine.com/5.0/en-US/scripted-actions-in-unreal-engine/">official documentation</a> states, are Editor Utility Blueprints that you launch in the Unreal Editor by right-clicking Assets in the Content Browser, or by right-clicking Actors either in the Level Viewport or in the World Outliner.

With this said, we can image this is a very helpful way of building tools for managing assets and actors quickly using only blueprints. Althought you can build them using c++ too, as I will explain in a next post.

Scripted actions give us support for getting the assets or actors selected at the time you run the action and we can use them for any logic inside the blueprint graph.

## Renaming Tool in blueprints

We are going to create a renaming tool that searches for a selected string in selected assets names in Content Browser and replaces that string for another one of our selection. We'll be using Unreal Engine 5.2 but this procedure is tested in every later versions from 5.0. The tool UI will look like this:

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/posts/rename-asset-action-utility-blueprints-ui-unreal-engine-5.jpg" alt="Rename Assets asset action utility in blueprints ui">

## Create the Asset Action Utility in Blueprints

Text...


