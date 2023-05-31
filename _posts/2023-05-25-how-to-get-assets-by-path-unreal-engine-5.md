---
date: 2023-05-21 20:05
layout: post
title: Get Assets by path in Unreal Engine 5 C++
subtitle: Learn how to get assets by path in Unreal Engine 5 in C++
description: How to get assets by path in Unreal Engine 5 in C++
image: https://tvillalbac.github.io/blog/assets/img/posts/plugin-fix-up-unreal-engine-redirectors-automated-system.jpg
category: Unreal Engine 5
category-url: unreal-engine-5
tags: unreal-engine cpp
author: toni-villalba-corominas
recommended: https://tvillalbac.github.io/blog/how-to-fix-up-unreal-engine-5-redirectors-blueprints/
---



```cpp
FAssetRegistryModule& AssetRegistryModule = FModuleManager::LoadModuleChecked<FAssetRegistryModule>("AssetRegistry");
FSoftObjectPath SoftPath = FSoftObjectPath(*Path);
FassetData AssetData = AssetRegistryModule.Get().GetAssetByObjectPath(SoftPath);
```

```cpp
const FAssetData AssetData = UEditorAssetLibrary::FindAssetData(AssetPathName);
```
