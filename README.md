# XOVI Extensions for reMarkable

A personal suite of custom [XOVI](https://github.com/asivery/xovi) `.qmd` extensions to enhance the reMarkable tablet workflow, refining the user interface and unlocking essential missing features.

At its core: 
- **[Gestik](#gestik)** — three-, four-finger gestures to instant switch writing tools without reaching for the toolbar; five-finger gestures for navigation to page overview / ToC. Configurable from: *Settings ▸ Gestik* page.
- **[LinkFromSelection](#linkfromselection)** — *links* from a selection: jump to a page in the same document or another one.
- **[NavHistory](#navhistory)** — *Back & Forward* navigation through your visited-page history.
- **Additional nine tweaks** — see the [extensions table](#available-extensions) below.

Tested only for the latest reMarkable OS *xochitl 3.27.2.2* (rM Paper Pure).

## Install

Requires a developer-mode reMarkable running [XOVI](https://github.com/asivery/xovi) and
[qt-resource-rebuilder](https://github.com/asivery/rm-xovi-extensions/tree/master/qt-resource-rebuilder). Every extension needs `qt-resource-rebuilder`; a few need other `XOVI` extensions.


<!-- ### Vellum package manager (recommended)

Most extensions are available in [Vellum](https://vellum.delivery):

```sh
vellum add <extension-name>
``` -->

### Manual

Download the `.qmd` files into `/home/root/xovi/exthome/qt-resource-rebuilder/` and restart `xochitl` over the USB connection:

```sh
scp extensionName.qmd root@10.11.99.1:/home/root/xovi/exthome/qt-resource-rebuilder/
ssh  root@10.11.99.1 'systemctl restart xochitl'
```

## Available Extensions

| Extension | Description |
| --- | --- |
| [**gestik.qmd**](#gestik) | Configurable **multi-finger gestures** from: **Settings ▸ Gestik** page |
| [**linkFromSelection.qmd**](#linkfromselection) | On-page **links** from a lasso selection: tap to jump to a page in the current document or to another document; long-press to edit/delete the link |
| [**navHistory.qmd**](#navhistory) | **Page Back & Forward navigation** through visited-page history, via quick-browse arrow buttons or 5-finger swipes |
| [**betterTocCollapseAll.qmd**](#bettertoccollapseall) | Adds a **collapse-all** / **expand-all button** to the Table-of-Contents header. *Requires [betterToc](https://github.com/rmitchellscott/xovi-bettertoc) + [betterTocCollapse](https://github.com/rmitchellscott/xovi-qmd-extensions#bettertoccollapse) mods* |
| [**forceWideColumn.qmd**](#forcewidecolumn) | Forces every note's typed text to the **Wide column** on open, including existing notes |
| [**fasterPageLabels.qmd**](#fasterpagelabels) | Auto-hides the page-number label ~1.25 s after a page turn |
| [**fasterScrollBar.qmd**](#fasterscrollbar) | Auto-hides the document scrollbar ~0.35 s after you stop scrolling |
| [**hideBackToPageBar.qmd**](#hidebacktopagebar) | Suppresses the native "*Back to page N*" bar that pops up after you follow a PDF hyperlink |
| [**hideTitleQuickBrowse.qmd**](#hidetitlequickbrowse) | Removes the document-title bar shown at the top while the quick-browse page-slider is up |
| [**dockButtons.qmd**](#dockbuttons) | Adds **My Files** / **Favorites** / **Tags** / **Trash** shortcut buttons to the homepage dock |
| [**toolbarTool.qmd**](#toolbartool) | Turns the toolbar collapse/expand button into active tool|
| [**collapseToolbarOnOpen.qmd**](#collapsetoolbaronopen) | Opens every document with the toolbar collapsed |

---

### Gestik

Multi-finger gesture bundle: pen/tool & thickness presets on the 3- and 4-finger swipes, Selection/Lasso on a 4-finger tap, Page Overview / Table of Contents on 5-finger swipes. Each pen gesture switches the tool and sets its thickness and colour. Configurable from a dedicated **Settings ▸ Gestik** page.

| ![gestik cheat sheet](./assets/Gestik%20cheat%20sheet%201.png) | ![gestik settings](./assets/Gestik%20cheat%20sheet%202.png) |
|:---:|:---:|

| <img src="./assets/Gestik settings.png" width="475"> |
|:--:|


---

### LinkFromSelection

Adds links on the page straight from a selection. Lasso some strokes, then tap one of the two buttons in the selection menu:

- **Same-document link** — tap a page from the native page overview / ToC and a clickable icon appears next to the selection. Tapping the icon jumps to that page.
- **Cross-document link** — from the file browser, select a document, then a page to link. Tapping the clickable icon created on the source page opens the
  other document at that page with a *Back* notification to return.

| Same-document link | Cross-document link|
|:---:|:---:|
| ![same document selection internal](./assets/Link%20internal.png) | ![gestik settings](./assets/Link%20external.png) |
| ![external document selection](./assets/Link%20internal%20button.png) | ![same document internal button](./assets/Link%20external%20button.png) |
| | |
|![external document button](./assets/Link%20internal.gif) | ![gestik settings](./assets/Link%20external.gif) |

Links works in `PDF`, `Notebook` and `EPUB` files.

>[!Tip]
> Long-press the icon for an *edit / delete* menu (re-pick the target, or remove the link). Links are stored *per document*, inside the document's own folder, so they're auto-deleted with it and survive restarts. If a target document or page no longer exists, tapping its icon offers to delete the dangling link.

| ![same document](./assets/Link%20internal%20delete.png) | ![external document](./assets/Link%20external%20delete.png) |
|:---:|:---:|

>[!Important]
> A link is independent of the strokes you drew it from: **erasing that handwriting does not delete the link**. A link also can't be selected or dragged, so to move a link, delete it and create a new one in the new position.

---

### NavHistory

Adds back & forward navigation through the pages visited (hyperlink/ToC jumps and page turns), like a desktop PDF viewer's `‹ ›`. Swipe up the quick-browse page-slider to reveal *Back / Forward* buttons. The same actions are also bound to a *5-finger swipe left / right*. Jumps track page identity, so they stay correct across page insert/delete/reorder.


| ![navHistory gestures](./assets/NavHistory%20cheat%20sheet.png) | ![navHistory menu](./assets/NavHistory.png)  |
|:---:|:---:|


| <img src="./assets/NavHistory.gif" width="475"> |
|:--:|

---

### BetterTocCollapseAll

Adds a *collapse-all / expand-all button* to the Table-of-Contents header bar. The button is hidden for documents with no nested entries.

| <img src="./assets/ToC button.png" width="475"> |
|:--:|

| <img src="./assets/ToC.gif" width="475"> |
|:--:|


> [!IMPORTANT]
> Requires [betterToc](https://github.com/rmitchellscott/xovi-bettertoc) and [betterTocCollapse](https://github.com/rmitchellscott/xovi-qmd-extensions/#betterTocCollapse). It's a companion to those mods, which provide the ToC view and the per-entry collapse state it builds on.

---

### ForceWideColumn

Whenever a note that has typed text is opened, its column is forced to *Wide*, including notes you created earlier. 

| Narrow / Medium column |  Wide column |
|:---:|:---:|
| ![narrow column](./assets/Text%20Narrow.png) | ![wide column](./assets/Text%20Wide.png)  |

>[!IMPORTANT]
>It overwrites each note's saved Narrow/Medium width with Wide — a note you set to Narrow snaps back to and is re-saved as Wide on reopen. 

---

### FasterPageLabels

Shortens how long the page-number label (bottom of the screen) lingers after a page turn before it auto-hides (~1.25 s).

| Original speed |`fasterPageLabels.qmd` speed |
|:---:|:---:|
| ![original speed](./assets/original%20page%20speed.gif) | ![fasterPageLabels](./assets/faster%20page%20speed.gif)  |

---

### FasterScrollBar

Shortens how long the scroll bar lingers after you lift your finger (fades in ~0.35 s).

| Original speed |`fasterScrollBar.qmd` speed |
|:---:|:---:|
| ![original speed](./assets/original%20scrollbar%20speed.gif) | ![fasterScrollBar](./assets/faster%20scrollbar%20speed.gif)  |

---

### HideBackToPageBar

After you follow a PDF hyperlink, `xochitl` pops a *"Back to page N"* notification bar at the bottom of the screen. With [navHistory](#navHistory) already providing Back/Forward, that bar is redundant. this extension removes it entirely.

| <img src="./assets/backbar.png" width="475"> |
|:--:|

---

### HideTitleQuickBrowse

Removes the document-title bar shown at the top of the screen while the
quick-browse page-slider is up (a one-finger swipe up from the bottom edge).

| <img src="./assets/title.png" width="475"> |
|:--:|

---

### DockButtons

Adds four shortcut buttons to the homepage dock: *My Files*, *Favorites*, *Tags* and *Trash*, each jumping the file browser straight to that view in one tap. This extends the original [FouzR](https://github.com/FouzR)'s [`favTagButton.qmd`](https://github.com/FouzR/xovi-extensions/blob/main/3.27/favTagButton.qmd).

| <img src="./assets/Dock.png" width="475"> |
|:--:|

---

### ToolbarTool

Turns the toolbar expand button into an at-a-glance readout of the active tool. This is adapted from [FouzR](https://github.com/FouzR)'s [`toolbar_icon.qmd`](https://github.com/FouzR/xovi-extensions/blob/main/3.27/toolbar_icon.qmd); the changes are layout-only: two tuned values (`font.pointSize` 20→15, `leftPadding` 10→4) plus right-justifying the thickness number, all for half-step (X.5) thickness readability.

|`toolbar_icon.qmd` |`toolbarTool.qmd` |
|:---:|:---:|
| ![toolbar icon](./assets/toolbar%20old.png) | ![toolbar tool](./assets/toolbar%20new.png)  |

---

### CollapseToolbarOnOpen

Opens every document (notebook, PDF, typed-text) with the toolbar forced into its collapsed state for a distraction-free page. 

---

## Credits

Several mods of this repo builds on other people's work in the reMarkable / XOVI modding community:

- **[asivery](https://github.com/asivery)** 
- **[FouzR](https://github.com/FouzR)** 
- **[rmitchellscott](https://github.com/rmitchellscott)**

## License

This project is licensed under the GPL-3.0-only — see the [LICENSE](LICENSE) file for details.
