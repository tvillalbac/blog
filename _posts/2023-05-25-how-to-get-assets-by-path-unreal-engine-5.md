---
date: 2023-05-23 20:05
layout: post
title: Get Assets by path in Unreal Engine 5 C++
subtitle: Learn how to get assets by path in Unreal Engine 5 in C++
description: How to get assets by path in Unreal Engine 5 in C++
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
FAssetRegistryModule& AssetRegistryModule = FModuleManager::LoadModuleChecked<FAssetRegistryModule>("AssetRegistry");
FSoftObjectPath MaskSoftPath = FSoftObjectPath(*OMaskPath);
FassetData OMaskAsset = AssetRegistryModule.Get().GetAssetByObjectPath(MaskSoftPath);
```


## Fix up Referencers 

Note:Link to UE5 documentation. In which file do we could find the FixUpReferencers function


## Extend Fix up referencers in Blueprints and Python

Note:Explanation that we can easily create our own custom redirectors function and a link to an article on how to make our fixing redirectors function available in python and blueprints.