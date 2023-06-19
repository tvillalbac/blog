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
recommended: https://tvillalbac.github.io/blog/how-to-fix-up-unreal-engine-5-redirectors-cpp-2/
---

<a href="https://docs.unrealengine.com/5.2/en-US/asset-redirectors-in-unreal-engine/">Redirectors</a>, in Unreal Engine, are objects that redirect references for moved (or renamed) assets from their old location to their new location.
In example, if an asset is referenced in a level and then we move and rename that asset, Unreal leaves a redirector in the asset old location indicating the new location for the level to find the proper asset.

In this <a href="https://docs.unrealengine.com/5.2/en-US/asset-redirectors-in-unreal-engine/#:~:text=in%20for%20you.-,Caveats,-Renaming">Unreal Engine Redirector's official section</a> there's a deeper explanation about the common issues involved to them.

Luckily we already have <a href="https://tvillalbac.github.io/blog/redirectors-fixer-plugin">TVC Redirectors Fixer Plugin</a> to help us to fix up redirectors at the same time we move or rename files or folders avoiding errors forgetting to fix redirectors after any of those operations.

But in this article, I'll explain how to create a function in Unreal Engine C++, exposed in Blueprints and python for your script tools, if you want to make your own.

## AssetTools module: A module for managing assets

<a href="https://docs.unrealengine.com/5.2/en-US/API/Developer/AssetTools/">AssetTools</a> module, is a collection of structs and classes dedicated to managing assets in our Unreal project, in content browser and in our version control systems.

<a href="https://docs.unrealengine.com/5.2/en-US/API/Developer/AssetTools/IAssetTools">IAssetTools module</a> is part of the AssetTools module, and is a class including a set of functions specially created for assets oparations like creation, duplication, renaming, and many other. I encourage you to check them in the last link shared to see them all.

To work with this module, we need to include the AssetTools module in your plugin .Build.cs file:

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/adding-assettools-module-to-unreal-plugin.jpg" alt="Add AssetTools module in Unreal Engine 5 plugin">

or project .Build.cs file:

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/adding-assettools-module-to-unreal-project.jpg" alt="Add AssetTools module in Unreal Engine 5 project">


depending if you want to use the module in project's source code or in a plugin.





```cpp
FAssetToolsModule& AssetToolsModule = FModuleManager::Get().LoadModuleChecked<FAssetToolsModule>(TEXT("AssetTools"));
```

or

```cpp
IAssetTools& AssetTools = FModuleManager::Get().LoadModuleChecked<FAssetToolsModule>(TEXT("AssetTools")).Get();
```

## Fix up Referencers 

Note:Link to UE5 documentation. In which file do we could find the FixUpReferencers function

```cpp
AssetToolsModule.Get().FixupReferencers(RedirectorsToFix);
```

or

```cpp
AssetTools.FixupReferencers(RedirectorsToFix);
```

## Extend Fix up referencers in Blueprints and Python

Note:Explanation that we can easily create our own custom redirectors function and a link to an article on how to make our fixing redirectors function available in python and blueprints.