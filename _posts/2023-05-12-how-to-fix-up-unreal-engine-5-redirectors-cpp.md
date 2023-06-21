---
date: 2023-06-22 08:30
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

## Including AssetTools module in our project or plugin

To work with this module, we need to include the AssetTools module in your plugin .Build.cs file:

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/posts/adding-assettools-module-to-unreal-plugin.jpg" alt="Add AssetTools module in Unreal Engine 5 plugin">

or project .Build.cs file:

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/posts/adding-assettools-module-to-unreal-project.jpg" alt="Add AssetTools module in Unreal Engine 5 project">

depending if you want to use the module in a plugin or in project's source code.

Then, you need to add the proper include in the file we want to load the AssetTools module

```cpp
#include "AssetToolsModule.h"
```

Once this is done, we can define and declare our function in our plugin or project class.

## Redirectors Fixer function

Let's create our public function and place the proper UFUNCTION macro in the line above to make use of the <a href="https://www.unrealengine.com/en-US/blog/unreal-property-system-reflection">Unreal Engine reflection system</a> that will also expose the function to Blueprints and python.

```cpp
public:
    UFUNCTION(BlueprintCallable, meta = (DisplayName = "TVC Redirectors Fixer", Keywords = "TVCRedirectorsFixerPlugin redirector fix fixer"), Category = "TVCRedirectorsFixerPlugin")
	static void TVCRedirectorsFixer(TArray<FString> Paths);
```

I named the function TVCRedirectorsFixer and its input is solely an array of the content browser paths to the redirectors to fix.

As UFUNCTION properties I used BlueprintCallable to expose the function in a Blueprint or Level Blueprint graph and in meta tag, added a proper name, category and keywords for easy finding in blueprints search tool.

I made my function like this, writting the two includes that I needed for it to work (place them on your file at the top properly):

```cpp
#include "AssetToolsModule.h"
#include "EditorAssetLibrary.h"

void UTVCRedirectorsFixerBPFL::TVCRedirectorsFixer(TArray<FString> Paths)
{
	TArray<UObjectRedirector*> Redirectors;
	for (FString& Path : Paths)
	{
		UObject* Object = UEditorAssetLibrary::LoadAsset(Path);
		if (Object)
		{
			auto Redirector = Cast<UObjectRedirector>(Object);
			if (Redirector)
			{
				Redirectors.Add(Redirector);
			}
		}
	}

	FAssetToolsModule& AssetToolsModule = FModuleManager::LoadModuleChecked< FAssetToolsModule>(TEXT("AssetTools"));
	AssetToolsModule.Get().FixupReferencers(Redirectors, true, ERedirectFixupMode::DeleteFixedUpRedirectors);
}
```

To make use of the UEditorAssetLibrary for loading the paths passed to the function, we need to include the header EditorAssetLibrary.h and the module EditorScriptingUtilities in our project or plugin  .Build.cs file as we explained in <a href="https://tvillalbac.github.io/blog/how-to-fix-up-unreal-engine-5-redirectors-cpp/#use-redirectors-fixer-blueprint/#including-assettools-module-in-our-project-or-plugin/">Including AssetTools module in our project or plugin</a> but adding EditorScriptingUtilities.

In our function, first, we create an array of UObjectRedirectors to store the paths corresponding to a redirector.

Then, we iterate over the passed paths and try to cast the object loaded with each path to a redirector. If it's a redirector, we'll store it in our array of redirectors that we'll later pass to the fixup redirectors built-in function. This is a important step, as the execution will crash if we pass not a redirector in the array.

The final step is to load the Asset Tools module, get the IAssetTools class with the Get() function and use the function FixUpReferencers passing the redirectors array to it, the next parameter I set on true is bCheckoutDialogPrompt that manage if the source control dialog should appear in the process, and lastly is the FixupMode, which is an ERedirectFixupMode enum where the values available are DeleteFixedUpRedirectors or LeaveFixedUpRedirectors.

## Extend our function in Blueprints and Python

As we added the UFUNCTION macro at the line above our function declaration, this function now is exposed in blueprints, so we can use that function as a blueprint in our editor blueprints as it can be done with the TVC Redirectors Fixer plugin, explained here <a href="https://tvillalbac.github.io/blog/redirectors-fixer-plugin/#use-redirectors-fixer-blueprint">Use Redirectors Fixer Blueprint</a>

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/posts/redirectors-fixer-node-exposed-in-blueprints.jpg" alt="Redirectors fixer function created in blueprints">

We also have exposed the functions to python API like happens using TVC Redirectors Fixer plugin, explained here: <a href="https://tvillalbac.github.io/blog/redirectors-fixer-plugin/#use-redirectors-fixer-in-python">Use Redirectors Fixer In Python</a>, but modifying the python code:

```python
unreal.NameOfMyClass.tvc_redirectors_fixer(paths_list_of_redirectors)
```

Note that NameOfMyClass must be replaced by the name of the class where the function belongs to, either it's a plugin class or a project class.

Note also how the function name was automatedly converted by the python API. It converts our <a href="https://wiki.c2.com/?PascalCase">pascal case style</a> name to a [snake case style](https://en.wikipedia.org/wiki/Snake_case){:target="_blank"} name.

Tip: If you want to find your class in python in Unreal Engine just type in your python console in Unreal:

```python
import unreal

for python_class in sorted(dir(unreal)):
    print(python_class)
```

It will print a list of the classes available in unreal python in alphabetical order, uppercase letters first. And if you do the same but looking for your class functions:

```python
for function in sorted(dir(unreal.NameOfMyClass)):
    print(function)
```

You could find your python function in the list and see how unreal python has named it.

