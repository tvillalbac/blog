---
date: 2023-05-22 20:05
layout: post
title: Unreal Engine 5 Redirectors Fixer Plugin
subtitle: Learn how to use the TVC Redirectors Fixer plugin in Unreal Engine 5
description: How to use the TVC Redirectors Fixer plugin in Unreal Engine 5
image: https://tvillalbac.github.io/blog/assets/img/posts/plugin-fix-up-unreal-engine-redirectors-automated-system.jpg
category: Unreal Engine 5
category-url: unreal-engine-5
tags: unreal-engine
author: toni-villalba-corominas
recommended: https://tvillalbac.github.io/blog/how-to-fix-up-unreal-engine-5-redirectors-blueprints/
---

Note:Main explanation and link to the post of how to fix redirectors by hand in UE5
Link: <https://tvillalbac.github.io/blog/how-to-esxi-update/>

## AssetTools module: A module for managing assets

Note:AssetTools module explanation and how to get it for using


```cpp
// Aenean lacinia bibendum nulla sed consectetur. Etiam porta sem malesuada magna mollis euismod. Fusce dapibus,
// tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa.
FAssetToolsModule& AssetToolsModule = FModuleManager::Get().LoadModuleChecked<FAssetToolsModule>(TEXT("AssetTools"));
```


## Fix up Referencers 

Note:Link to UE5 documentation. In which file do we could find the FixUpReferencers function


## Extend Fix up referencers in Blueprints and Python

Note:Explanation that we can easily create our own custom redirectors function and a link to an article on how to make our fixing redirectors function available in python and blueprints.