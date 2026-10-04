# Doodle

A feature for drawing on your own. You can draw with the same tools as [drawing chat](./draw-room.md) (pen, eraser, fill, shapes, layers, and so on). Open it from "Doodle" in the navigation bar (`/doodle`).

## Drawing

- Start with "New doodle". Doodles you drew before can be opened from the "Continue drawing" list, which shows a thumbnail, the canvas size, and when each was last updated.
- The name and canvas size can be changed from "Doodle settings" even while you are drawing. The maximum size is 3840px (regardless of roles).
- The tools work the same as in drawing chat. See ["Drawing" in drawing chat](./draw-room.md#drawing) for details.
- Since you draw alone, clearing and deleting layers can also be undone. There is no chat, participant list, sharing, or petting.
- Doodles can be deleted from the list (they are also removed from this browser and cannot be restored).

## Timelapse

With "Timelapse" (▷) at the top right of the screen, you can replay your strokes in order.

- Choose a length from 10 to 60 seconds.
- With "Make video", the replay is turned into a video (WebM, or mp4 on browsers that cannot record WebM) that you can download, save to the drive, or post in a note. On browsers that cannot make videos, you can only replay it.
- Undone strokes and the positions of strokes before they were moved are not replayed.
- Keep the tab visible while the video is being made (it pauses while the tab is hidden and continues when you come back).

## Cropping and extending the canvas

With "Crop canvas" at the top right of the screen, you can change the canvas area with the same controls as cropping an image.

- Drag the frame or its handles to set the area. Dragging the frame outward extends the canvas.
- You can also enter the width, height, and position (X, Y) as numbers.
- Press `Enter` to apply and `Esc` to cancel.
- Strokes outside the frame are kept, so they reappear if you extend the canvas again.
- Applying a crop clears the undo/redo history.

## How doodles are saved

- Your drawing is saved automatically in this browser, per account. It is not sent to the server.
- This means you cannot continue it from another browser or device, and clearing the browser's data also removes your doodles.
- An image is sent to the server only when you save it to the drive or post it in a note. This works the same way as [saving and posting images](./draw-room.md#saving-and-posting-as-an-image) in drawing chat.

## Drawing from the post form

- With the doodle button in the post form, you can start a new doodle or continue a previous one (it opens in a window).
- With "Attach to note", the drawing is attached to that post form as is.

## Navigation bar

"Doodle" is included in the default navigation bar. It is also added once for people who were already using Juice Server (if you remove it yourself, it will not be added again).
