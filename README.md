# simpleMenuWizard

Hide default context menu items in Firefox 57 and later

---

This project is inspired by [this post on reddit](https://www.reddit.com/r/firefox/comments/7dvtw0/guide_how_to_edit_your_context_menu/) and by [an issue](https://github.com/Aris-t2/CustomCSSforFx/issues/76) in the great [CustomCSSforFx](https://github.com/Aris-t2/CustomCSSforFx/issues/2) project.

## Instructions

To **remove entries from the context menu** you need to

1. Find your **profile folder** (profile names are different for everyone):  
   Address bar > Enter `about:support` > Click `Open Folder`  
   or `Shift + F2` to open Firefox's command line, then enter the command `folder openprofile`.

2. [Download this project](https://github.com/stonecrusher/simpleMenuWizard/archive/master.zip) and unzip it.

3. Move `userChrome.css` and `simpleMenuWizard` into *[...]\\**profile.folder**\chrome\\* directory.  
   If chrome folder doesn't exist, create it.  
   If `userChrome.css` already exists, do *not* overwrite and proceed [here](https://github.com/stonecrusher/simpleMenuWizard#using-simplemenuwizard-together-with-other-custom-modifications).

4. Open `userChrome.css` with a texteditor for a general overview and some options.

5. Open the `simpleMenuWizard` directory and edit each .css file (except beginning with `opt_`) to customize them to your needs.  
  **Activate** option to **remove** menu item: Remove `/*` at the beginning of the line.  
  **Deactivate** option to **leave** menu item: Add `/*` at the beginning of the line.

    Each file is for another context:

    * `blank-context.css`	when right-clicking on a blank area or text
    * `frame-context.css` when right-clicking on an iframe
    * `image-context.css` when right-clicking on an image
    * `input-context.css` when right-clicking on an input-field
    * `link-context.css` when right-clicking on a link
    * `main-hamburger.css` when left-clicking on the menu **hamburger on top right**
    * `media-context.css` when right-clicking on media like audio or html5 video
    * `select-context.css` when right-clicking on selected text or object
    * `sidebar-context.css` when right-clicking on items in bookmark- or history sidebar
    * `sidebar-header.css` when left-clicking the sidebar dropdown menu
    * `source-context.css` when right-clicking a blank area on view-source pages
    * `tab-context.css` when right-clicking on a tab
    * `toolbar-context.css` when right-clicking on toolbar or tabbar
    * `urlbar-context.css` when right-clicking on the addressbar
    * `urlbar-pageaction.css` when left-clicking the three dots in the addressbar
	* `main-menubar.css` when left-clicking the old-school menu bar (File, Edit, ...)

6. Restart Firefox to make changes work.  
   Hint: A nice way to restart is via Firefox's command line. Press `Shift + F2`, type `restart`, press enter.

Important notes:
 * All options are disabled by default, so if you don't edit the files, nothing will happen.
 * Items that appear in different contexts with the same ID will disappear in all those contexts when activated. This is because many menus internally share the same very big context menu and are separated here for more convenience.  
   For specific problems please [open an issue](https://github.com/stonecrusher/simpleMenuWizard/issues), there may be workarounds.

## Hide Pocket / Sync / Screenshots
If you don't use either of those "internal addons" at all, you can just disable them, which will also remove their context menu entries everywhere. So you don't have to do it manually.

How to do it: Set the respective value in `about:config`.

- For Pocket, load `about:config?filter=extensions.pocket.enabled` into addressbar and switch to `false`.
- For Sync, load `about:config?filter=identity.fxaccounts.enabled` into addressbar and switch to `false` (only available in FF60 or higher).
- For Screenshots, load `about:config?filter=extensions.screenshots.disabled` into addressbar and switch to `true`.

## Using simpleMenuWizard together with other custom modifications

Easiest thing to do is renaming the `userChrome.css` that came with the zip package of simpleMenuWizard.
Rename it to `simpleMenuWizard.css` and put it into `chrome` directory next to the already existing `userChrome.css`.

Open the old `userChrome.css` which is filled with foreign code and add `@import url("./simpleMenuWizard.css");` to the very top. That's it!

You can now edit `simpleMenuWizard.css` for a general overview and some options or continue with [step 5](https://github.com/stonecrusher/simpleMenuWizard#instructions).

## Uninstall simpleMenuWizard

Delete all the files and folders that came with this project.  
So if you don't use other modifications, you can simply delete the whole *[...]\\**profile.folder**\chrome\\* directory.

## To do
Menus not included yet:
* Main titlebar menus (oldschool menu opening with `alt` key) (`#main-menubar`)

## Contribute
For bugreports and missing items you're welcome to [open an issue here](https://github.com/stonecrusher/simpleMenuWizard/issues) or make a pull request.
