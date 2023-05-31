---
layout: page
menu: true
date: '2023-02-27 01:53:59'
title: Unreal Engine Redirectors Fixer Plugin
description: How to use the TVC redirectors plugin for Unreal Engine
permalink: /redirectors-fixer-plugin/
---

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/posts/plugin-fix-up-unreal-engine-redirectors-automated-system.jpg" alt="TVC redirectors plugin for Unreal Engine 5 right click menu">

# TVC Redirectors Fixer Plugin Guide for Unreal Engine 4.27 & 5 (All versions)

#### *How to fix up redirectors right after renaming or moving files or folders in Unreal Engine 5 and 4.27 in an automated way using this cool plugin*
{: .about-title }

1. <a href="https://tvillalbac.github.io/blog/redirectors-fixer-plugin/#install-plugin">Install plugin</a>
2. <a href="https://tvillalbac.github.io/blog/redirectors-fixer-plugin/#activate-plugin">Activate plugin</a>
3. <a href="https://tvillalbac.github.io/blog/redirectors-fixer-plugin/#configure-shortcut-for-renaming-assets-fixing-redirectors">Configure shortcut for renaming assets fixing redirectors</a>
4. <a href="https://tvillalbac.github.io/blog/redirectors-fixer-plugin/#basic-usage">Basic Usage</a>
5. <a href="https://tvillalbac.github.io/blog/redirectors-fixer-plugin/#rename-files-and-folders-fixing-redirectors">Rename files and folders fixing redirectors</a>
6. <a href="https://tvillalbac.github.io/blog/redirectors-fixer-plugin/#move-files-and-folders-fixing-redirectors">Move files and folders fixing redirectors</a>
7. <a href="https://tvillalbac.github.io/blog/redirectors-fixer-plugin/#use-redirectors-fixer-blueprint">Use Redirectors Fixer Blueprint</a>


## Install plugin

This is a guide on how to activate and use TVC Redirectors Fixer plugin for Unreal Engine 4 and 5 and it is suposed that the plugin is properly purchased and installed through Unreal Engine Marketplace.

If you want to purchase it or don't know how to install it, you can search for "Redirector" in Marketplace search bar to find the plugin and refer to this link from official documentation: <a href="https://docs.unrealengine.com/5.0/en-US/working-with-plugins-in-unreal-engine/#installingpluginsfromtheunrealenginemarketplace">Installing Plugins from the Unreal Engine Marketplace</a>. It also applies to Unreal Engine 4.27 version.

## Activate plugin

For activating the plugin, you can refer to this <a href="https://tvillalbac.github.io/blog/how-to-activate-unreal-engine-plugin/">blog post</a> to know how activate the plugin for your project.

Once this step is done, we can continue to next configuration stage.

## Configure shortcut for renaming assets fixing redirectors

There's a shortcut for renaming assets fixing redirectors that you need to configure as it's not by default.

For that go to Editor Preferences window by clicking on Edit menu and Editor Preferences button in its submenu.

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/open-editor-preferences-window-unreal-engine.jpg" alt="Open Editor Preferences window in Unreal Engine 5">

Once the window is open, click on Keyboard Shortcuts in the left section and search for "tvc" in the search bar. You can configure it as your taste as it's empty by default. Personally, I set it as Ctrl+Alt+Shift+R as it's pretty easy to remember and I don't have any other assigned as this for Content Browser context.

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/tvc-redirectors-fixer-plugin-shortcut-setup.jpg" alt="Setup shortcut for TVC Redirectors Fixer plugin in Editor Preferences window in Unreal Engine 5">

Success! Now you can select any asset or folder in Content Browser and click on your shortcut to display the "TVC Renaming File Fixing Redirectors" window if the selection is an asset

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/rename-asset-fixing-redirectors-using-shortcut.jpg" alt="Rename asset by shortcut using TVC Redirectors Fixer plugin in Unreal Engine 5">

Or the "TVC Renaming Folder Fixing Redirectors" window if selection is a folder.

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/rename-asset-fixing-redirectors-using-shortcut-in-folder.jpg" alt="Rename folder by shortcut using TVC Redirectors Fixer plugin in Unreal Engine 5">

## Basic Usage

In essence, what this plugin does, is adding another contextual menu entry in Unreal Engine Content Browser, next to "Rename" and "Move Here" entries, which are actions able to cause redirectors creation, with extended functionality of fixing created redirectors right after the move or rename action has finished.

## Rename files and folders fixing redirectors

You can rename any folder or asset in Content Browser by right clicking on it and the context menu will show the "Rename File Fixing Redirectors" menu entry next to the default "Rename" menu, if selection is an asset.

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/rename-asset-fixing-redirectors-plugin-contextual-menu.jpg" alt="Rename asset contextual menu of TVC Redirectors Fixer plugin in Unreal Engine 5">

Or the "Rename Folder Fixing Redirectors" menu, if selection is a folder.

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/rename-folder-fixing-redirectors-plugin-contextual-menu.jpg" alt="Rename folder contextual menu of TVC Redirectors Fixer plugin in Unreal Engine 5">

As you will see, when the "TVC Renaming File Fixing Redirectors" or "TVC Renaming Folder Fixing Redirectors" window appears, you can write the new name in the New Name section and click on "Ok".

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/rename-asset-fixing-redirectors-window.jpg" alt="Rename asset window of TVC Redirectors Fixer plugin in Unreal Engine 5">

Then, the asset will be renamed to the selected name and the redirector generated, if any, will be fixed. A couple of notification messages will show if those two actions were successful.

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/rename-asset-fixing-redirectors-plugin-success-message.jpg" alt="Rename asset success notifies messages">

If the selection is a folder, it also fixes all the redirectors in the selected folder and subfolders and removes the old folders, keeping your content browser clean of redirectors and empty folders.

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/rename-folder-fixing-redirectors-plugin-success-message.jpg" alt="Rename folder success notifies messages">

There is another option for renaming any file or folder by selecting it and pressing the defined keyboard shortcut.
If you don't know how to set and enable this keyboard shortcut, refer to this section about <a href="https://tvillalbac.github.io/blog/redirectors-fixer-plugin/#configure-shortcut-for-renaming-assets-fixing-redirectors">how to configure shortcut for renaming assets fixing redirectors</a>.

## Move files and folders fixing redirectors

To move any files or folders to any other folder, you just drag and drop them as usual on top of another folder and it will show the "Move Fixing Redirectors Here" menu entry next to the default "Move Here" menu.

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/move-here-fixing-redirectors-plugin.jpg" alt="Move here assets contextual menu of TVC Redirectors Fixer plugin in Unreal Engine 5">
<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/move-here-fixing-redirectors-plugin-contextual-menu.jpg" alt="Move here assets contextual menu of TVC Redirectors Fixer plugin in Unreal Engine 5">

Then the plugin will move the dropped selection to the selected location and fix the redirectors generated, if any.

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/move-files-fixing-redirectors-notify-messages.jpg" alt="Move here assets notify messages">

If the dropped selection includes any folder, the plugin will also fix the redirectors generated for the assets inside the folders, if any, and will remove the old folder location.

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/move-here-fixing-redirectors-plugin-contextual-menu-multiselection.jpg" alt="Move here assets and folders contextual menu">
<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/move-folder-and-files-fixing-redirectors-plugin-success-messages.jpg" alt="Move here assets and folders success messages">

## Use Redirectors Fixer Blueprint

There's also a blueprint node called TVCRedirectorsFixer included with the plugin for fixing redirectors that you can use in your editor blueprints. You can find it by looking for "tvc" or "redirectors" in blueprint nodes creation search bar.

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/redirectors-fixer-blueprint-node.jpg" alt="TVC Redirectors Fixer blueprint node">

Let's supose that we have a simple asset action utility for searching and replacing asset names in blueprints as the one we developed in this <a href="https://tvillalbac.github.io/blog/how-to-create-renaming-tool-in-blueprints/">blog post</a> and we want to fix redirectors after the renaming action has finished.

We could save the paths of the selected assets in an array of strings before being renamed and, after that, we could pass the array of paths to the blueprint node and it will fix them only if any of this paths has become a redirector. Blueprint node checks if there's an exiting asset in each path passed and, if it's a redirector, it will be fixed.

<img class="img" src="https://tvillalbac.github.io/blog/assets/img/pages/RedirectorsFixerGuide/redirectors-fixer-blueprint-node-applied.jpg" alt="TVC Redirectors Fixer blueprint node applied">

## Use Redirectors Fixer in python

As TVCRedirectorsFixer blueprint node is exposed in python, we can make use of it for our python scripts.

We can call this python method by writting:

```python
unreal.TVCRedirectorsFixerBPFL.tvc_redirectors_fixer(paths_list_of_redirectors)
```

Actually, as this is the same blueprint functionality, we know already that we can pass any asset path to this function and it will check if it's a redirector before trying to fix it.

If we want to make a function to fix up selected redirectors in content browser in python, we could make:

```python
def get_selected_assets_paths():
    selected_assets = unreal.EditorUtilityLibrary.get_selected_assets()
    paths = []
    for asset in selected_assets:
        path = asset.get_path_name()
        paths.append(path)
    return paths

def fix_selected_redirectors():
    paths = get_selected_assets_paths()
    # This is the call to our blueprint function in python
    unreal.TVCRedirectorsFixerBPFL.tvc_redirectors_fixer(paths)
```

