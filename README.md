# simpleMenuWizard

Hide default context menu items in Firefox 57 and later (latest FF release version)

---

## Instructions

To **remove entries from the context menu** you need to

1. Find your **profile folder** (profile names are different for everyone):  
   Address bar > Enter `about:support` > Click `Open Folder` (second one, not the "Update Folder").

2. [Download this project](https://github.com/stonecrusher/simpleMenuWizard/archive/master.zip) and unzip it.

3. Move `userChrome.css` and `simpleMenuWizard` into _[...]\\**profile.folder**\chrome\\_ directory.  
   If `chrome` folder doesn't exist, create it.  
   If `userChrome.css` already exists, do _not_ overwrite and proceed [here](https://github.com/stonecrusher/simpleMenuWizard#using-simplemenuwizard-together-with-other-custom-modifications).

4. Open `userChrome.css` with a texteditor for a general overview and some options.

5. Open the `simpleMenuWizard` directory and edit each .css file (except beginning with `opt_`) to customize them to your needs.  
   **Remove menu item**: Remove `/*` at the beginning of the line.  
   **Leave menu item**: Add `/*` to the beginning of the line (by default every option is deactivated).

   Each file is for another context:

   - `blank-context.css` when right-clicking on a blank area or text
   - `frame-context.css` when right-clicking on an iframe
   - `image-context.css` when right-clicking on an image
   - `input-context.css` when right-clicking on an input-field
   - `link-context.css` when right-clicking on a link
   - `main-hamburger.css` when **left**-clicking on the three lines on top right
   - `main-menubar.css` when **left**-clicking on the main menubar (open with ALT key - file, edit, view, ...)
   - `media-context.css` when right-clicking on media like audio or html5 video
   - `select-context.css` when right-clicking on selected text or object
   - `sidebar-context.css` when right-clicking on items in bookmark- or history sidebar
   - `sidebar-header.css` when **left**-clicking the sidebar dropdown menu
   - `source-context.css` when right-clicking a blank area on view-source pages
   - `tab-context.css` when right-clicking on a tab
   - `toolbar-context.css` when right-clicking on toolbar or tabbar
   - `urlbar-context.css` when right-clicking on the addressbar
   - `urlbar-pageaction.css` when **left**-clicking the three dots in the addressbar

6. Load `about:config` into addressbar. Search for `toolkit.legacyUserProfileCustomizations.stylesheets` and make sure the value is `true`.

7. Restart Firefox to make changes work.

**Important notes:**

- All _options and items are disabled by default_, so if you don't edit the files, nothing will happen.
- Items that appear in different contexts with the same ID will disappear in all those contexts when _activated only once_. This is because many menus internally share the same very big context menu and are separated here for more convenience.  
  For specific problems please [open an issue](https://github.com/stonecrusher/simpleMenuWizard/issues), there may be workarounds.

## Hide Pocket / Sync / Screenshots

If you don't use either of those "internal addons" at all, you can just disable them, which will also remove their context menu entries everywhere.

How to do it: Load `about:config` into addressbar and set the respective value.

- Pocket: Search for `extensions.pocket.enabled` and switch to `false`.
- Sync: Search for `identity.fxaccounts.enabled` and switch to `false`.
- Screenshots: Search for `extensions.screenshots.disabled` and switch to `true`.

## Using simpleMenuWizard together with other custom modifications

Easiest thing to do is renaming the `userChrome.css` that came with the zip package of simpleMenuWizard.
Rename it to `simpleMenuWizard.css` and put it into `chrome` directory next to the already existing `userChrome.css`.

Open the old `userChrome.css` which is filled with foreign code and add `@import url("./simpleMenuWizard.css");` to the very top. That's it!

You can now edit `simpleMenuWizard.css` for a general overview and some options or continue with [step 5](https://github.com/stonecrusher/simpleMenuWizard#instructions).

## Uninstall simpleMenuWizard

Delete all the files and folders that came with this project.  
So if you don't use other modifications, you can simply delete the whole _[...]\\**profile.folder**\chrome\\_ directory.  
Restart your browser.

## Contribute

For bugreports and missing items you're welcome to [open an issue here](https://github.com/stonecrusher/simpleMenuWizard/issues) or make a pull request.

## Motivation

Tidy up your context menus, be faster, have a cleaner UI!

This project is inspired by [BubiBalboa's post on reddit](https://www.reddit.com/r/firefox/comments/7dvtw0/guide_how_to_edit_your_context_menu/) and by [an issue](https://github.com/Aris-t2/CustomCSSforFx/issues/76) in the great [CustomCSSforFx](https://github.com/Aris-t2/CustomCSSforFx/issues/2) project.

---

---

---

## **[CustomCSSforFx README.md](https://github.com/Aris-t2/CustomCSSforFx/blob/master/README.md)**

## Downloads for Firefox Quantum (60+)

**[CustomCSSforFx releases & changelog](https://github.com/Aris-t2/CustomCSSforFx/releases)** --- **[Custom JavaScript for Firefox](https://github.com/Aris-t2/CustomJSforFx)** --- **[NoiaButtons CSS tweaks](https://github.com/Aris-t2/NoiaButtons)**  
**[List of CTR, CTB, GMF & Noia4 CSS tweaks & link to FOXSCAPEuC theme by Michael Walden](https://github.com/Aris-t2/CustomCSSforFx/issues/2)**

## Want to support this project?

**[[ Paypal Me ]](https://www.paypal.me/tkpay)**

## Instructions / Howto / Readme

- [Unlock custom CSS usage in Firefox 69 and newer](#unlock-custom-css-usage-in-firefox-69-and-newer)
- [WebExtensions can not modify Firefox Quantums appearance properly](#webextensions-can-not-modify-firefox-quantums-appearance-properly)
- [Where to find Firefox profile folder? The correct location for user styles.](#where-to-find-firefox-profile-folder-the-correct-location-for-user-styles)
- [How to use custom user styles?](#how-to-use-custom-user-styles)
- [How to find item ids and attributes?](#how-to-find-item-ids-and-attributes)
- [How to modify custom user styles?](#how-to-modify-custom-user-styles)
- [Suggested ui tweaks](#suggested-ui-tweaks)
- ['about:config' tweaks](#aboutconfig-tweaks)

## Unlock custom CSS usage in Firefox 69 and newer

`about:config` > `toolkit.legacyUserProfileCustomizations.stylesheets` > `true`

## WebExtensions can not modify Firefox Quantums appearance properly

The only way to modify ui is adding custom CSS code to **userChrome.css** and **userContent.css** files inside browsers profile folder.  
Keep in mind CSS code can not create entirely new items, buttons or toolbars. It only can modify already present ui items.

## Where to find Firefox profile folder? The correct location for user styles.

**1.** Find your profile folder ('profile names are different for everyone').  
`about:support > Profile Folder > Open Folder`  
or `about:profiles > Root Directory > Open Folder`

**2.** User styles belong into `\chrome\` folder. Create it, if there is none yet. It should look like this afterwards:  
`\ PROFILE FOLDER NAME \chrome\`

**3.** Copy `userChrome.css`, `userContent.css` and `\config\`, `\css\`, `\image\` folders into `\chrome\` folder. It should look like this afterwards:  
`\chrome\config\`  
`\chrome\css\`  
`\chrome\image\`  
`\chrome\userChrome.css`  
`\chrome\userContent.css`

(Optional) Profile folders location on drive:  
**Windows**  
`C:\Users\ USERNAME \AppData\Roaming\Mozilla\Firefox\Profiles\ PROFILE FOLDER NAME \`  
Hidden files must be visible to see `AppData` folder. Alternatively open `%APPDATA%\Mozilla\Firefox\Profiles\` from explorers location bar.  
**Linux**  
`/home/ username /.mozilla/firefox/ profile folder name /`  
Hidden files must be visible to see `.mozilla` folder.  
**Mac OS X**  
`~\Library\Mozilla\Firefox\Profiles\ PROFILE FOLDER NAME \` or  
`~\Library\Application Support\Mozilla\Firefox\Profiles\ PROFILE FOLDER NAME \`  
`\Users\ USERNAME \Library\Application\Support\Firefox\Profiles\`

## How to use custom user styles?

The _userChrome.css_ and _userContent.css_ files works like an options\configurations file. All main "features" can be enabled and disabled there.  
Edit _userChrome.css_ and _userContent.css_ with any text editor (**[Notepad++](https://notepad-plus-plus.org/download/)** recommended on Windows) and enable or disable any feature you like by modifying, removing or outcommenting available `@import` strings.  
Restart Firefox after every modification for changes to take effect.

**Example**  
If "classic button appearance for navigation toolbar buttons" should be <u>enabled</u>, the corresponding line has to look like this:  
`@import "./css/buttons/buttons_on_navbar_classic_appearance.css"; /**/`

If "classic button appearance for navigation toolbar buttons" should be <u>disabled</u>, the corresponding line has to look like this:  
`/* @import "./css/buttons/buttons_on_navbar_classic_appearance.css"; /**/`

Note  
Code between `/*` and `*/` won't be used by Firefox unless there are other `/*` or `*/` inbetween.

## How to find item ids and attributes?

Firefox 57-60

Enable once:  
1\. Tools > WebDeveloper > Toggle Tools > Toolbox Options > Enable browser chrome and add-on debugging toolboxes  
2\. Tools > WebDeveloper > Toggle Tools > Toolbox Options > Enable remote debugging

Hit `Ctrl+Alt+Shift+I` or open 'Tools > WebDeveloper > Browser Toolbox'.

Inspect ui or web content.

Force popups to stay open for inspection:  
Click on 'disable popup auto hide' button (= button with four squares) on developer toolbars end.

Firefox 61+

Enable once:  
1\. Tools > WebDeveloper > Toggle Tools > 'Customize Tools and get help button' (= button with three dots) > Settings > Enable browser chrome and add-on debugging toolboxes  
2\. Tools > WebDeveloper > Toggle Tools > 'Customize Tools and get help button' (= button with three dots) > Settings > Enable remote debugging

Hit `Ctrl+Alt+Shift+I` or open 'Tools > WebDeveloper > Browser Toolbox'.

Inspect ui or web content.

Force popups to stay open for inspection:
Click on 'Customize Tools and get help button' (= button with three dots) and select 'Disable popup auto-hide'.

## How to modify custom user styles?

Open CSS files with a text editor. Look through the code and change values the way you need.  
Some files contain additional instructions about how to tweak the ui for individual cases.  
Restart Firefox for changes to take effect.

_Example_  
Open `./css/tabs/classic_squared_tabs.css` file  
Look for `/* unloaded/pending tabs color *//*`  
Remove `/*` at lines end to make that part of the code active. Save the file and restart Firefox.

_Example 2_  
Open `userChrome.css` file  
Look for `@import "./css/tabs/classic_squared_tabs.css"; /**/`  
Add `/*` at lines start to remove classic squared tabs.  
The result will look like `/* @import "./css/tabs/classic_squared_tabs.css"; /**/`

_Example 3_  
Open `userChrome.css` file  
Look for `/* @import "./css/locationbar/reader_alternative_icon.css"; /**/`  
Remove `/*` at lines start to enable this popup appearance.  
The result will look like `/* @import "./css/locationbar/reader_alternative_icon.css"; /**`

## Suggested ui tweaks

**Toolbar modes (suggestion: compact mode)**  
_Customize mode > Density > Compact / Normal / Touch_

**Titlebar modes** (suggestion: Firefox titlebar ['application/hamburger button in titlebar' only works in Firefox titlebar])  
_Customize mode > Title Bar > uncheck checkbox_

**Drag space above tabs toolbar** (suggestion: disable drag space ['application/hamburger button in titlebar' works best without drag space])  
_Customize mode > Drag Space > uncheck checkbox_

**Bookmarks menu button on bookmarks toolbar**  
_Customize mode > Toolbars > Bookmarks Toolbar_  
_Customize mode > move 'bookmarks menu' button to bookmark toolbars end_

**Downloads button always visible**  
_Customize mode > downloads button > click on button and uncheck 'Auto-hide'_

**Searchbar** (suggestion: placed after location bar)  
_Customize mode > Search(bar) > move to navigation toolbar_

**Flexible spaces** (suggestion: remove spaces after and before location bar)  
_Customize mode > grab and drag flexible space into palette_

**RSS icon in location bar**  
_Install [Awesome RSS](https://addons.mozilla.org/addon/awesome-rss/) WebExtension_

**Search within "New Tab page" (Fx69+)**  
_browser.newtabpage.activity-stream.improvesearch.handoffToAwesomebar_

## 'about:config' tweaks

(To revert changes right-click entry and select 'reset')

**Tab audio icon**  
_browser.tabs.showAudioPlayingIcon_

**Tab min width** (suggestion: 100)  
_browser.tabs.tabMinWidth_

**Insert related tab after current tab** (suggestion: enable / set to 'true')  
_browser.tabs.insertRelatedAfterCurrent_

**Hide 'http://' from url** (suggestion: disable / set to 'false')  
_browser.urlbar.trimURLs_

**Open links in new tab/window**  
_browser.link.open_newwindow.restriction_ > 0 (new tab instead window)

**Preview tabs using 'Ctrl + Tab'**  
_browser.ctrlTab.previews_

**Close window with last visible tab** (suggestion: disable / set to 'false')  
_browser.tabs.closeWindowWithLastTab_

**Titlebar**  
_browser.tabs.drawInTitlebar_

**Old about:newtab and about:home pages (Firefox 57-59 only)**  
_browser.newtabpage.activity-stream.enabled_  
_browser.newtabpage.activity-stream.aboutHome.enabled_

**HTML5 fullscreen warning**  
_full-screen-api.warning.delay_ > 0 or -1 (reduces delay / hides warning)  
_full-screen-api.warning.timeout_ > 0 (reduces delay)

**Recently added bookmarks**  
_browser.bookmarks.showRecentlyBookmarked_

**General animations**  
_toolkit.cosmeticAnimations.enabled_

**Fullscreen animations for HTML5 content**  
_full-screen-api.transition-duration.enter_ > 0 0 (reduces animation time)  
_full-screen-api.transition-duration.leave_ > 0 0 (reduces animation time)

**Add-on manager: remove 'Get Add-ons' category**  
_extensions.getAddons.showPane_

**Findbar: animated result highlighting**  
_findbar.modalHighlight_

**Searchbar in 'about:preferences'**  
_browser.preferences.search_

**Location Bar: search engines at popups bottom**  
_browser.urlbar.oneOffSearches_

**Searchbar: open search results in new tab**  
_browser.search.openintab_

**Reader mode**  
_reader.parse-on-load.enabled_

**Geolocation** (suggestion: disable / set to 'false')  
_geo.enabled_

**Pocket** (suggestion: disable / set to 'false')  
_extensions.pocket.enabled_

**Screenshots** (suggestion: disable / set to 'true')  
_extensions.screenshots.disabled_

**Container tabs**  
_privacy.userContext.enabled_

**Password viewer in login forms** (suggestion: disable / set to 'false')  
_signon.showAutoCompleteFooter_

**Font rendering**  
_gfx.canvas.azure.backends_ > direct2d1.1,cairo,skia (old font rendering)  
_gfx.content.azure.backends_ > direct2d1.1,cairo,skia (old font rendering)

**Anti fingerprinting (Caution: browser might behave in unforeseen ways!)**  
_privacy.resistFingerprinting_  
[Fingerprinting info at Mozilla Wiki tweaks](https://wiki.mozilla.org/Security/Fingerprinting)

**Telemetry / data collection** (suggestion: disable / set to 'false')  
_browser.ping-centre.telemetry_  
_toolkit.telemetry.archive.enabled_  
_toolkit.telemetry.bhrPing.enabled_  
_toolkit.telemetry.enabled_  
_toolkit.telemetry.firstShutdownPing.enabled_  
_toolkit.telemetry.newProfilePing.enabled_  
_toolkit.telemetry.reportingpolicy.firstRun_  
_toolkit.telemetry.shutdownPingSender.enabled_  
_toolkit.telemetry.unified_  
_toolkit.telemetry.updatePing.enabled_  
_experiments.enabled_  
_experiments.activeExperiment_  
_experiments.supported_  
_datareporting.healthreport.uploadEnabled_  
_nsITelemetry.canRecordBase_  
_nsITelemetry.canRecordExtended_  
_browser.newtabpage.activity-stream.feeds.telemetry_  
_browser.newtabpage.activity-stream.telemetry_  
_extensions.screenshots.upload-disabled_ ("true" to disable)
