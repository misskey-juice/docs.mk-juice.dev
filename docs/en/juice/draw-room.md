# Drawing chat

A feature that lets you create a room where multiple people draw on the same canvas together. Open it from the navigation menu or the "Games" page (`/draw`).

## Creating a room

From "Create a room", the room owner chooses:

- **Room name**
- **Visibility**: "Followers only" or "All local users"
- **Maximum number of people who can draw**: 2 to 512, and can be changed later. People beyond the limit can still enter the room as spectators
- **Canvas size**: one of the presets — Landscape (1600×900), Portrait (900×1600), Square (1200×1200), Large square (2048×2048), Extra large square (3840×3840) — or a custom width and height between 100 and 3840. It can be changed later, in which case the canvas expands or crops from the top-left corner. Strokes that fall outside after shrinking are not deleted, so they reappear if you enlarge it again
- **Keep on the server after ending**: if turned off, the drawing and chat are deleted one hour after the room ends
- **Content warning (CW)**: write anything people should know before seeing the drawing, such as graphic content (up to 128 characters). When the room is opened, this warning is shown instead of the drawing until the viewer chooses to open it
- **Sensitive (NSFW) room**: for people who hide sensitive media, the drawing is hidden until they choose to open it. Images posted from this room are uploaded as sensitive files. When drawing sensitive content, also check ["NSFW in drawing chat" in the rules](../service/rules.md#nsfw-in-drawing-chat)

Depending on your role, you may not be able to create rooms. Even then, you can still join other people's rooms.

Each person can host up to 5 rooms at the same time by default (this depends on roles). The room list shows "Your rooms in progress: n/limit"; when you reach the limit, end one of your rooms to create a new one.

## Joining and spectating

- Open rooms are listed on the drawing chat page. When you enter a room, you first open it as a spectator.
- The list also includes "Everyone's saved drawing rooms" (rooms kept after ending) and rooms that will be deleted soon. You can share a room in a note or copy its link, and posting an image from a room includes the room's name and URL.
- Rooms whose visibility is "All local users" and that are not sensitive (NSFW) can be viewed from their URL even by people who are not logged in (they can watch the drawing and chat in real time, but cannot draw or chat). This is not possible if the server is set to hide content from visitors who are not logged in, or if the room host has turned on "Require sign-in to view contents". Posting a room link shows a preview of the drawing (OGP).
- Press "Join to draw" to start drawing. If the room is full, you can only spectate.
- Spectators can also write in the chat (up to 500 characters per message). Emoji and custom emoji can be used, and each message shows its time.
- People who have the room open (online) are shown in a list. People who close the room or switch to another tab become offline. You can open a person's profile from the chat or the layer list.
- The room owner can "Remove from drawers" anyone who is drawing (they remain as a spectator).
- The room owner can also leave the drawers and spectate with "Switch to spectator mode". They remain the room owner, so they can rejoin as a drawer even when the room is full.

## Drawing

- **Pen**: supports pen pressure from pen tablets and similar devices. You can choose the "Normal brush", "Soft (watercolor) brush", "Pixel (crisp)", or "Fill enclosed area" brush. With "Fill enclosed area", the area you trace around is filled when using the pen, and erased all at once when using the eraser.
- **Eraser**: its size can be set separately from the pen.
- **Fill (bucket)**: fills the area enclosed by lines around the point you click.
- **Paint inside lines**: lets you paint only inside the lines that enclose the point where you start drawing. Combined with the "Fill enclosed area" brush, it fills only the parts enclosed by lines within the area you traced (or erases them with the eraser).
- **Eyedropper**: picks a color from the canvas. You can also press `I`, or click while holding Alt.
- **Color, size, and opacity**: the maximum size depends on the canvas size.
- **Undo / redo**: you can undo drawing, moving, and rotating strokes, deleting selected strokes, and clearing or deleting draft layers. Undo with `Ctrl+Z`; redo with `Ctrl+Shift+Z` or `Ctrl+Y`. On touch devices, tap with two fingers to undo and with three fingers to redo.
- **Color palette**: pick colors from a hue wheel, saved colors, recent colors, or by color code, RGB, or HSV. Changing the color keeps your current tool.
- **Pressure settings**: "Pressure changes size" and "Pressure changes opacity" can be turned on or off separately (opacity isn't available for the dot brush), and others see your strokes the same way. The pen size is chosen as a percentage of the canvas (1–250%), and size and opacity are remembered.
- **Close gaps**: when using the bucket fill, fills as if small gaps in the lines were closed (off, small, medium, large).
- **Pet**: drag to pet the picture. The picture doesn't change, and everyone can see you petting it. Spectators can use it too. The "Pet" button is next to the save button, and petting also works with touch. While you are petting, a hand is shown on your own screen too.
- After picking a color with the eyedropper, you return to the previous tool. Long-pressing with a finger also acts as the eyedropper. While you hold, a ring fills up, and when the color is picked you get a color swatch and a vibration.
- **Clear current layer**: erases all strokes on the layer you're currently drawing on.

### Layers

Each person who draws can have up to 8 layers. Add more with "Add layer", and rename, show/hide, change the opacity of, reorder, or delete them. Changes are reflected on other people's screens too. Strokes are drawn on the layer you have selected (the one you're drawing on).

You can reorder your layers by dragging (keyboard also works) and delete them all with "Delete all layers". Each layer also has these settings:

- **Lock transparency**: draw only where the layer already has paint, to recolor without going outside.
- **Blend mode**: choose how the layer combines with the ones below, such as multiply, screen, overlay, or color burn.
- **Draft**: with "Add draft" or "Make it a draft", a layer becomes visible only to you and isn't included in saved images. Press "Show to everyone" to send its current strokes to others.
- **Merge layers**: With "Merge with layer above" or "Merge with layer below", you can combine your layer with the layer above or below it. The strokes from the source layer go in as a group that keeps the source layer's opacity and blend mode, and eraser and alpha-locked strokes only affect that group. The merged layer takes over the target layer's opacity and blend mode (if both are 100% and Normal, it looks the same as before merging; if the target is semi-transparent, that opacity also applies to the source strokes). **Merging cannot be undone.**

### Selecting and moving

- **Rectangle select / Lasso select**: selects your own strokes. Strokes are cut at the edge of the selected area, so you can select just part of a stroke. Hold Shift while selecting to add to the selection.
- **Move**: moves the selected strokes, or your entire layer if nothing is selected.
- Selected strokes can be rotated left or right, or deleted (`Delete` / `Backspace`). Press `Esc` to clear the selection. You can also scale them (with the handle at the bottom right or the enlarge/shrink buttons; stroke widths change by the same ratio) and flip them horizontally or vertically.

Strokes are separated into a layer per person, so you can never erase someone else's strokes. You can show or hide each layer, and toggle showing your own layer on top. The room owner can also erase another person's layer with "Clear this layer". There is a limit to how much each person can draw on their layer; operations beyond it are rejected by the server and undone.

Other people's cursors are shown as circles with their avatars. You can also hide them or change their opacity.

## Navigating the canvas

- **Zoom**: mouse wheel, the zoom in/out buttons, `Ctrl+＋` / `Ctrl+－`, or pinch with two fingers on touch devices. You can zoom in up to 3200%. If you turn off "Zoom with the mouse wheel", the wheel pans the view instead and zooming becomes `Ctrl`+wheel (this setting is saved in your browser)
- **Pan**: `Shift`+wheel, drag with the middle mouse button, drag while holding the space bar, the Hand tool (`H`), or slide with two fingers on touch devices. The Hand tool moves only the view, not your strokes
- **Rotate**: rotate the canvas with the rotate left/right buttons, or with two fingers on smartphones and similar devices. "Reset rotation" returns it to normal
- **Pixelated Zoom**: shows pixels as-is without smoothing when zoomed in (also applied to the overview map). At 800% or more in this mode, a pixel grid is also shown
- **Overview map**: shows which part of the whole canvas you're viewing. It can be shown or hidden
- **Fit to screen**: returns to a zoom level where the whole canvas fits (`Ctrl+0`)
- **View settings**: from the "..." menu, you can change display settings and show debug information (stroke count, data size and their limits, redraw time, etc.). You're notified on screen when you reach a stroke limit.
- **Loading display**: When opening a room, the layer (person) being loaded, along with the progress (%) and data size for that layer and overall, is shown. The debug info also shows the room's total data size and its limit

On smartphones and narrow windows (including the deck), the canvas takes up more space and the layers and chat appear in panels that slide up from the bottom. Buttons show their names, and the buttons in the page header are grouped into a named menu.

The layers and chat panel can be tucked away to the right together ("Hide side panel"). You can change the panel's width and the height ratio between layers and chat by dragging the divider (keyboard also works), and these are saved in your browser.

Buttons for tools, the palette, and the bottom bar always show their names, regardless of screen width (the lock is shown as "Alpha lock").

## Saving and posting as an image

Whether the room is still open or has ended, you can turn the whole canvas, or an area you select by dragging, into an image:

- Save image to Drive
- Post image as a note
- Download image

You can choose PNG (lossless), WebP (the same compression Misskey uses on upload), or JPEG. PNG keeps every pixel as-is while compressing, so the file is smaller.

## Ending a room

- The room owner can end the room with "End the drawing chat". Once ended, no one can draw anymore.
- Rooms with "Keep on the server after ending" turned on remain view-only after ending and can be found under "Saved drawings". Rooms with it turned off are deleted one hour after ending, so save or post an image before then if you want to keep it. Even for a room that ended without saving, the host can switch it to be saved with the "Save to server" button before it is deleted (within 1 hour of ending).
- Open rooms where nothing has been drawn or said for 24 hours are ended automatically.

## Reporting and moderation

- You can [report](./abuse-report.md) the room itself (its owner) with "Report room" in the room menu, and a chat message (its sender) from the message. The content at the time of the report is preserved and shown in the reports in the control panel.
- Moderators can delete problematic rooms, even while they are open. Deletions are recorded in the moderation log. While a moderator is inspecting a room, this is not shown to the people in it.

## Settings for admins

- In the JUICE settings of the control panel, you can enable or disable drawing chat as a whole (enabled by default). When disabled, no one can create or enter rooms, and it disappears from the menu.
- Role policies let you configure the following per role:
  - **Create drawing chat rooms**: even when turned off, users can still spectate and join other people's rooms (on by default)
  - **Maximum drawing chat canvas size**: the maximum for each of width and height (100–3840, default 3840). Applied when creating a room and when changing its size later
  - **Per-person stroke count and data limit in a room**: 30,000 strokes / 64MB by default (up to 200,000 strokes / 128MB)
  - **Number of drawing chat rooms one person can host at the same time**: the limit on rooms that have not ended (1–100, default 5)
- With "Max stroke data per room" in the JUICE settings, you can set the total stroke data limit for everyone in a room (16–512MB, default 256MB). Everyone's strokes are loaded together when a room is opened or viewed after ending, so larger values increase the load on the server and viewers' devices.
