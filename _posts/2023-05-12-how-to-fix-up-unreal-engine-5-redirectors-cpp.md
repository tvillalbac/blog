---
date: 2023-05-12 20:05
layout: post
title: Fix up Unreal Engine 5 redirectors by c++ code
subtitle: Learn how to fix up Unreal Engine referencers by code
description: How to fix up Unreal Engine 5 redirectors by c++ code
image: https://tvillalbac.github.io/blog/assets/img/posts/fix-up-unreal-engine-redirectors-by-code-cpp.jpg
category: Unreal Engine 5
category-url: unreal-engine-5
tags: unreal-engine cpp
author: toni-villalba-corominas
paginate: true
recommended: https://tvillalbac.github.io/blog/how-to-fix-up-unreal-engine-5-redirectors-cpp-2/
---

Note:Main explanation and link to the post of how to fix redirectors by hand in UE5
Link: <https://tvillalbac.github.io/blog/how-to-esxi-update/>

## AssetTools module: A module for managing assets

Note:AssetTools module explanation and how to get it for using

```bash
FAssetToolsModule& AssetToolsModule = FModuleManager::Get().LoadModuleChecked<FAssetToolsModule>(TEXT("AssetTools"));
```

or

```bash
IAssetTools& AssetTools = FModuleManager::Get().LoadModuleChecked<FAssetToolsModule>(TEXT("AssetTools")).Get();
```

## Fix up Referencers 

Note:Link to UE5 documentation. In which file do we could find the FixUpReferencers function

```bash
AssetToolsModule.Get().FixupReferencers(RedirectorsToFix);
```

or

```bash
AssetTools.FixupReferencers(RedirectorsToFix);
```

## Extend Fix up referencers in Blueprints and Python

Note:Explanation that we can easily create our own custom redirectors function and a link to an article on how to make our fixing redirectors function available in python and blueprints.