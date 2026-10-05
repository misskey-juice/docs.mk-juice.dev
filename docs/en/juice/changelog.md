# Changelog

Major changes to misskey-juice's JUICE-specific features. This does not include changes inherited from upstream Misskey. For the full history, see the [GitHub releases page](https://github.com/misskey-juice/misskey-juice/releases).

> [!note]
> This page is updated manually and may lag behind the [Japanese changelog](../../juice/changelog.md). If you need the latest information, please check the Japanese page (or the GitHub releases page above) as well.

## v2026.10.0-juice+4.6

- Added a "juice" style for the welcome page ([JUICE entrance](./entrance.md)). It can be switched with upstream's classic and simple styles under Branding in the control panel. Alongside the server introduction and sign-up, it shows the numbers of users, users online, connected servers, and notes, the local timeline, popular content, activity, and some connected servers. If a background image URL is set, it is laid across the whole page and the panels become semi-transparent
- [Federation diagnosis](./federation-diagnosis.md) now shows the types of signature keys in "Signed fetch of a user" (distinguishing RSA with key length, Ed25519, and ECDSA). "Inbox (delivery target) response" is now checked with an empty unsigned POST, fixing it showing OK even when there was no inbox (404, etc.)
- The JUICE badge on the colored "Request to join" button on the welcome page is now filled for better visibility
- For developers: added `keys` to each item in `admin/federation/diagnose-instance`, which now returns `inboxNotFound` when the inbox does not accept deliveries. Added `juice` to `entrancePageStyle` in `admin/update-meta`

## v2026.10.0-juice+4.5

- Imports from Settings → Account data can now require approval by the staff ([Import approval](./import-approval.md)). Imports of the types chosen in the JUICE settings (by default only following; muting, blocking, lists, and antennas can also be chosen) become requests and are imported once the staff approves them. You can see the status of your requests and the reason for rejection, and withdraw pending requests
- Added a review screen for import requests. It opens from the control panel or the "Tools" menu, and shows the first lines of the file, the total count, and counts per server so you can approve or reject (with a reason). Moderators and people with the new role policy "Approve/reject import requests" can review
- Rooms in [drawing chat](./draw-room.md) can now have a description (up to 10 lines and 512 characters). It is shown below the name in the room list, and inside the room with the "Room description" button
- For developers: added `admin/import-requests/{list,show,approve,reject}` and `import-requests/{list,cancel}`. `i/import-*` now returns `requiresApproval`. Added `importApprovalRequiredTypes` to `juice/public-settings` and `admin/juice/settings`, and `description` to `draw-rooms/create` and `update`

## v2026.10.0-juice+4.4

- Added a "Diagnosis" tab to the information page of federated servers (`/instance-info/<host>`) for moderators. It checks this server's settings and state and makes actual requests to the remote server in order, showing where federation is stopping (nothing is delivered to the remote server). See [Federation diagnosis](./federation-diagnosis.md)
- The [Doodle](./doodle.md) timelapse now also follows changes to how layers look and operations other than drawing (moving, rotating, scaling, flipping, deleting, undo, redo, and so on; operations before this update are not followed). Watermark presets can now be overlaid. Cropping the canvas can also be started from an area selected with the range tool, the selection bar, or the image menu
- Added pixel-art canvas sizes 32×32, 64×64, and 128×128 to [drawing chat](./draw-room.md) and Doodle, and lowered the minimum canvas size to 16. When you come back to a room where you were a drawer, you now start as a spectator
- "Notes from followed users" can now be chosen as an [antenna](./antenna.md) source
- [Reactions with emojis from other servers](./reaction-enhancements.md) now have a dotted border so they can be told apart from this server's emojis. Fixed joining such a reaction not appearing until reload
- Fixed characters on the left being cut off depending on the width in the novel viewer's vertical mode. Fixed the watermark QR code getting stuck loading when the avatar in the middle could not be loaded
- For developers: added `admin/federation/diagnose-instance` (`write:admin:federation`). Added `pixel32`, `pixel64`, and `pixel128` to `canvasPreset` in `draw-rooms/create`, and lowered the minimum of `canvasWidth` and `canvasHeight` to 16

## v2026.10.0-juice+4.3

- Added a [timelapse](./doodle.md#timelapse) to [Doodle](./doodle.md). It replays your strokes in order (10–60 seconds) and can be turned into a video to download, save to the drive, or post in a note. The canvas can now be cropped or extended with the same controls as cropping an image
- When a text-only [novel](./novel.md) note is collapsed because it is long, "Read as novel" is shown instead of "Show more". Chapter titles (`[chapter:…]`) are now shown as headings in the novel viewer. Fixed chapters that start with a chapter title without a divider continuing from the previous chapter in vertical mode
- In [drawing chat](./draw-room.md), the room owner can now write a reason when removing someone from the drawers (shown only to that person). Fixed not being able to draw in the empty space next to the overview map while it is shown (also in Doodle)
- Added a setting to [JUICE settings](./settings.md) that rejects disposable email addresses using the disposable-email-domains list (off by default). When verifymail.io or Truemail cannot be reached during email address validation, sign-ups are no longer blocked; the server's own validation is used instead
- For developers: added `reason` to `draw-rooms/kick` (sent only to the removed person's stream in `memberLeft`). Added `disposableEmailBlocklistEnabled`, `disposableEmailAllowDomains`, and related fields to `admin/juice/settings` and `admin/juice/update-settings`

## v2026.10.0-juice+4.2

- Added [Doodle](./doodle.md). You can draw on your own with the same tools as drawing chat, and your work is saved automatically in this browser (not sent to the server). Open it from "Doodle" in the navigation bar (`/doodle`), or draw from the doodle button in the post form and attach the result directly. It is also added to the default navigation bar (and added once for existing users)
- Added a shape tool (line, rectangle, ellipse, triangle) to [drawing chat](./draw-room.md) and Doodle. Choose outline only or filled; hold Shift for a square, circle, or lines at 45° angles
- Fixed a trailing divider appearing in the layer menu in drawing chat, and the hide button in the layer panel not aligning to the right in ended rooms

## v2026.10.0-juice+4.1

- You can now prevent others from downloading .txt files attached to [novel](./novel.md#preventing-downloads-of-attached-txt-files) posts (switch it from the attachment menu in the drive or the post form; you can also have it disabled from the start under "JUICE" in settings). Other servers receive a link to the novel viewer. Note that this cannot completely prevent the text from being extracted, and attachments that have already reached other servers cannot be retracted
- In the novel viewer, you can now bookmark lines and jump back to them later ([bookmarks](./novel.md#reading-in-the-novel-viewer)). The resume position is now also remembered in horizontal mode. Added a setting to keep half-width words sideways in vertical mode. Fixed chapters split with `[chapter:…]` sometimes not appearing in the table of contents
- The size of avatar decorations can now be changed (0.1–1×). Decoration sizes from other servers are also reflected
- Added "Don't nyaize cat posts (show only the cat ears)" under "JUICE" in settings (based on [misskey-tempura](https://github.com/lqvp/misskey-tempura))
- Added "Slider" as a source for the [BPM measurement widget](./bpm-widget.md). Removed the metronome's BPM limit and fixed it slowing down in background tabs, among other fixes
- Fixed the screen turning black when using the move tool on large canvases on iPad and similar devices in [drawing chat](./draw-room.md). Moving selected strokes no longer freezes on drawings with many strokes
- For developers: added `notes/novel-text` (takes `noteId` and `fileId`, returns `name` and `data` (base64)). Added `novelDownloadDisabled` to drive files, `novelTextProtected` to notes, and `avatarDecorations[].scale` to `i/update`

## v2026.10.0-juice+4.0

A release that follows upstream Misskey 2026.10.0 (including security fixes; see the [upstream changelog](https://github.com/misskey-dev/misskey/blob/develop/CHANGELOG.md) for upstream changes).

- The [relay timeline](./relay-timeline.md#display-for-visitors-who-are-not-signed-in) now respects "Visibility of user-generated content to guests" in the Control Panel. Since every note that arrives via a relay is a remote note, visitors who are not signed in see nothing on it unless the setting is "Everything is public"
- Added Traditional Chinese translations for JUICE-specific items

## v2026.9.1-juice+3.20

- In [drawing chat](./draw-room.md), you can now merge your layer with the layer above or below it (cannot be undone). Selected strokes can now also be scaled and flipped horizontally or vertically
- Drawing chat rooms whose visibility is all local users and that are not NSFW can now be viewed from their URL by people who are not logged in (view only). Posting a link shows a preview of the drawing
- Each person can now host 5 drawing chat rooms at the same time by default (previously 1). Admins can change this with the role policy "Number of drawing chat rooms one person can host at the same time" (1–100). The room list shows "Your rooms in progress: n/limit"
- Rooms that ended without saving can now be switched to "Save to server" by the host before they are deleted
- Two-finger tap to undo and three-finger tap to redo. Pen size up to 250%. Tool buttons always show their names. Improved loading progress and data size display, long-press eyedropper feedback, and "Pet" button placement; profiles can be opened from the chat and layer list
- For developers: in-progress strokes on the stream are now delivered as `strokeParts` (`{ parts: [...] }`), batched every 50 ms per room. **`strokePart` is no longer delivered.** Added `draw-rooms/keep` and `draw-rooms/hosting` (`{ count, max }`); `draw-rooms/show`, `strokes`, `chat-history`, and the stream can be used without logging in under certain conditions. Added the role policy `drawRoomMaxActiveRooms`, `g` on strokes and `groups` on layers, and `drawRoomMaxRoomMegabytes` in `juice/public-settings`

## v2026.9.1-juice+3.19

- On the review screens for [emoji requests](./emoji-request.md#reviewing-for-moderators) and [avatar decoration requests](./avatar-decoration-request.md#reviewing-for-moderators), selected requests can now be approved or rejected together (notifications, emails, and moderation log entries are still recorded per request)
- Requests submitted together in one go now produce a single new-request notification to moderators (with "and N more") and a single System Webhook. The webhook payload gains `count` and `requests` (`id`, `name`, and `category` are from the first request). **If you were receiving one webhook per request, you need to update your handler to look at `requests`**
- "Paint inside lines" can now be used with "Fill enclosed area" in [drawing chat](./draw-room.md). Fixed issues with strokes whose opacity changes with pressure (opacity bleeding into other parts, disappearing when combined with alpha lock, and slowing down while drawing)
- The "check" in approval/rejection notifications for requesters is now a button (showing the reason for rejections). Added a save button to text files attached to novel posts
- Fixed the favorite button not appearing as favorited in favorites lists, and the post language's initial value sometimes not matching any available language

## v2026.9.1-juice+3.18

- Added features to [drawing chat](./draw-room.md): undo/redo (`Ctrl+Shift+Z` / `Ctrl+Y` to redo), a sketch layer visible only to you, reordering/deleting all/alpha lock/blend modes for layers, a color palette, gap closing for fills, a pet tool (spectators can use it too), a toggle for whether pen pressure changes size and opacity, content warning (CW) and sensitive marks for rooms, "Everyone's saved drawings" and "Rooms being deleted soon" lists, room sharing, and a display settings menu with debug information
- Raised the per-person stroke limit in drawing chat from 3,000 strokes / 8MB to 30,000 strokes / 64MB, adjustable via role policies (up to 200,000 strokes / 128MB). The total limit for a whole room can be set in the JUICE settings (16–512MB, default 256MB)
- Posts edited on other servers are now received and updated, and shown as "edited" (based on Mastodon and Fedibird)
- Avatar decorations of users on Misskey-based servers (Misskey, CherryPick, Sharkey) are now shown (based on misskey-tempura; can be turned off in the JUICE settings, on by default)
- Added "Unrenote and renote again" to the renote menu (imported from misskey-springroll)
- Added settings to place a favorite button to the right of a note's "+" button, and a button to the left that adds a chosen reaction (🧡 by default) in one tap (both off by default; the reaction button is based on misskey-tempura)
- Added a "BPM counter" widget. Measure BPM by tapping along to a rhythm, or from how fast posts arrive on timelines or notifications, and play a metronome at that BPM
- Text files attached to [novel-flagged](./novel.md) posts can now be opened with "Read as novel". Fixed posts flagged as novels after posting not appearing with "Show novels only", which now also works on the media timeline and includes plain renotes of novels
- Added the novel editor and drawing chat to the default navigation bar, and JUICE-specific items now show a JUICE badge
- Settings backup/restore now also restores font size, system font, language, custom CSS, and display preferences for the novel viewer, novel editor, and drawing chat
- The [post language](./post-language.md) filter now always shows posts without a language (same as Mastodon). The post form's language now starts from your account's language setting (or the display language if none)

## v2026.9.1-juice+3.17

- In [drawing chat](./draw-room.md), each person can now have multiple layers (up to 8). Layers can be added, renamed, shown/hidden, have their opacity changed, reordered, and deleted, and changes are reflected on other people's screens. "Clear my layer" is now "Clear current layer"
- "Fill enclosed area" is now one of the brush types in drawing chat: it fills with the pen and erases the enclosed area with the eraser
- In drawing chat, other people's cursors can now be hidden or have their opacity changed. The layers and chat panel can be tucked away to the right together, and its width and height ratio can be changed by dragging (saved in the browser)
- Drawing chat is lighter, and rooms with many strokes load faster. PNG saving now uses lossless compression ("PNG (lossless)")
- Fixed the zoom level menu, the rotation of the overview map frame, and unintended rotation during two-finger gestures on smartphones in drawing chat
- The "+tag" and "Gmail dot" settings in [JUICE-specific settings](./settings.md) now reject matching email addresses regardless of whether an account already exists (for new signups and email address changes; the contact form is not affected). The signup screen now shows the reason
- Fixed an issue where lining up multiple unverified signups and verifying them one by one could bypass the duplicate email check. Duplicates and blocked addresses are now also checked when opening the verification link
- Added drawing chat, the novel editor, and the MFM search engine choice to the feature list on the in-app About JUICE page

## v2026.9.1-juice+3.16

> [!important] The GitHub repository has moved
> After the v3.16 release, the misskey-juice repository moved to the [misskey-juice organization](https://github.com/misskey-juice). Its new location is <https://github.com/misskey-juice/misskey-juice>.
>
> - The old URL (`github.com/Zel9278/misskey-juice`) redirects to the new location automatically, but if you already self-host, please update your remote: `git remote set-url origin https://github.com/misskey-juice/misskey-juice.git`
> - Docker images are now published to `ghcr.io/misskey-juice/misskey-juice`. Images up to v3.16 remain at `ghcr.io/zel9278/misskey-juice`.

- Added the [novel editor](./novel-editor.md) (`/novel-editor`). It highlights notations and has buttons for ruby, emphasis dots, formatting, indentation, chapter titles, section breaks, page breaks, dashes, and ellipses. Supports per-work drafts saved in the browser, a table of contents with per-chapter lengths, character count and manuscript page count, a target length, find and replace, focus mode, a preview with the same look as the novel viewer, and a pre-post check. Text can be opened from or saved as .txt files, and posted as a .txt file with the novel flag
- Added many features to [drawing chat](./draw-room.md): rectangle/lasso selection, a move tool, and rotating/deleting selected strokes; lasso fill, bucket fill, soft and pixel brushes, and painting inside lines; separate pen and eraser sizes, a hand tool, canvas rotation, more zoom and pan controls on PC; Pixelated Zoom with a pixel grid (up to 3200% zoom); the room owner can clear other people's layers and switch to spectator mode; emoji and timestamps in chat; a loading indicator when opening a room
- The search engine used by MFM search boxes ("… 検索") can now be chosen per user in the JUICE settings: Google, Yahoo!, Yahoo! JAPAN, Bing, DuckDuckGo, Kagi, Brave Search, Startpage, Ecosia, Perplexity, or a custom URL
- On narrow screens such as smartphones, buttons in drawing chat and the novel editor now show their names, and the page header buttons are grouped into a named menu. The window resize handle is larger on smartphones and tablets
- Fixed saving to Drive, posting, and downloading not working correctly after a drawing chat room ended, and spectators and online status remaining in the layer list after it ended
- Fixed several novel viewer issues: pages exceeding the screen height in vertical mode, the text not showing when switching to horizontal mode after turning pages in vertical mode, and the chapter navigation buttons being cut off on narrow screens in horizontal mode

## v2026.9.1-juice+3.15

- Added [drawing chat](./draw-room.md). Create a room where multiple people draw on the same canvas. The room owner decides the visibility, the maximum number of people who can draw, and the canvas size, and people can still join as spectators when the room is full. Supports per-user layers, pen pressure, an eyedropper, zoom and an overview map, other people's cursors and online status, and saving/posting/downloading the canvas as an image (PNG, WebP, JPEG)
- Added a drawing chat enable/disable toggle to the JUICE settings in the control panel, and "Create drawing chat rooms" and "Maximum drawing chat canvas size" to role policies
- Drawing chat rooms and their chat messages can now be [reported](./abuse-report.md). Moderators can delete problematic rooms even while they are open, and deletions are recorded in the moderation log

## v2026.9.1-juice+3.14

- The [novel viewer](./novel.md) no longer interprets MFM in the text. Links, mentions, custom emoji, etc. are shown as written; only ruby (MFM, Aozora Bunko notation, and pixiv's `[[rb:]]`) and bold, italic, and strikethrough are applied
- Added support for pixiv novel notation in the novel viewer. `[newpage]` inserts a page break (in horizontal mode, one page is shown at a time with buttons to move between pages), and `[chapter:Title]` sets the chapter name used in the table of contents
- Added support for Aozora Bunko emphasis dots (filled sesame, open sesame, filled circle, and open circle)
- Added full-screen reading, plus a character count and estimated reading time, to the novel viewer
- EUC-JP .txt files are now detected automatically. In addition to ｜, ＊, *, and | are now accepted as markers for the start of the ruby base text
- Automatic paragraph indent no longer indents lines starting with opening brackets such as 「 or symbols such as middle dots, dashes, and ●○
- Fixed several vertical-writing issues: …, ―, and half-width brackets being shown sideways; page breaks and reading position drifting when resizing the window; slivers of ruby from the adjacent page showing at the page edge; and left/right page contents misaligning after in-page browser search

## v2026.9.1-juice+3.13

- Added the [novel flag & novel viewer](./novel.md). Posts and .txt files in Drive can be marked as "novel", and flagged posts can be opened in a dedicated viewer with horizontal or vertical writing (paperback-style page turning and two-page spreads). It supports a per-chapter table of contents, ruby text, Aozora Bunko notation, paragraph indentation, font size/typeface/background, and bookmarks. Because an attached .txt file can be read as the body, you can post long works that exceed the character limit
- Added "Show novels only" to the menu of the regular timelines. Novel-flagged posts now appear in the [Media timeline](./media-timeline.md) even without attachments
- Added a fallback setting that sends the novel status as a CW when federating to non-JUICE instances that can't interpret the novel flag (disabled by default)
- Fixed long alphanumeric strings in the social login item overflowing the card on the in-app About JUICE page

## v2026.9.1-juice+3.12

- Added a [personal setting](./settings.md) that automatically sets posts containing decorative MFM (standard Markdown-style: bold, italic, strikethrough, code / MFM-specific decorations: center, small, quote, search, math, `$[]` functions) to "local only" visibility. The two categories can be toggled independently, and it triggers if either the body or the CW contains matching syntax (direct messages and replies to remote users are excluded)
- Fixed the username-availability check during signup not accounting for the prohibited-word list, which could show "available" while typing but reject the name on submission
- Removed the JPEG XL / HEIC/HEIF display support (dedicated WASM decoder) added in v3.11 (the fix that falls back to 404 on image processing failure is retained)

## v2026.9.0-juice+3.11

- Unified the [MIDI player](./midi-player.md)'s expanded view with the lightbox used for images and videos. Playback state carries over when expanding, and the "..." menu now also exposes the visualizer settings
- Fixed MIDI keyboard highlights staying lit longer than the actual note-off when sustain pedal was used
- Added a warning on iPhone/iPad for the known behavior where MIDI audio doesn't play if the device's silent switch is on
- Added support for displaying JPEG XL and HEIC/HEIF files through `/proxy/`, fixing remote custom emoji/avatars in these formats that previously failed to display (local Drive originals are handled the same way)
- Fixed unexpected exceptions from things like MIME mis-detection returning a raw 500 error; image processing failures now fall back to 404 properly

## v2026.9.0-juice+3.10

- Added a piano roll visualizer (vertical scroll, tick-based playback position) to the [MIDI player](./midi-player.md). You can toggle it and adjust roll speed and max polyphony from either the "JUICE" settings page or the in-player menu
- Fixed audio dropping out or freezing while playing files with an extreme number of note events (e.g. "black MIDI")
- Fixed the playback position drifting when seeking in MIDI files with tempo changes
- Removed the [relay timeline](./relay-timeline.md)'s boost-source display feature (added in v3.9; the underlying recording/federation mechanism was removed too)
- Fixed the update notification dialog not appearing for a JUICE-only version bump; it now shows both the Misskey and Juice version numbers

## v2026.9.0-juice+3.9

- Added a [MIDI player](./midi-player.md): play MIDI files attached to notes using soundfont-free Web Audio API synthesis (with a keyboard visualizer, BPM display, Media Session API integration, and more)
- Improved the [relay timeline](./relay-timeline.md) to clearly show the actual original poster of notes forwarded via a boost
- Fixed a bug where, after deleting and re-registering a relay server, the relay timeline of a user who had filtered to just that relay would stay empty

## v2026.9.0-juice+3.8

- Added [social login](./social-login.md): link Discord, Google, GitHub, GitLab, or Microsoft accounts and use them as a sign-in method (requires enabling two-factor authentication and opting in individually)
- Reorganized the "JUICE" settings page into three categories: "Account", "Timeline & display", and "Request forms"

## v2026.9.0-juice+3.7

- The [emoji request](./emoji-request.md) and [avatar decoration request](./avatar-decoration-request.md) forms let admins individually require fields like category, tags, license, and description (all optional by default); when submitting multiple items at once, cards with an empty required field now show a warning badge
- Improved the [AI-generated content flag](./ai-generated-flag.md)'s CW fallback for non-JUICE instances: it's now combined with an existing CW instead of being skipped, and detection was extended to cover AI-generated flags on individual attached files
- The [post language](./post-language.md) timeline language filter and local-users-only toggle can now also be switched from the Deck "Timeline" column
- Improved compatibility of the display-language filter and post language federation with Mastodon/Pleroma-style region-less language codes
- Added a button to bulk-delete selected images while in Drive's multi-select mode
- Fixed uploaded images being left behind in Drive when an emoji/avatar decoration request was canceled or failed to submit
- Various minor bug fixes

## v2026.9.0-juice+3.6

- The [emoji request](./emoji-request.md) and [avatar decoration request](./avatar-decoration-request.md) forms now show, separate from the pending-request limit, how many submissions you have left per day and when your next slot will free up (default 5 per rolling 24-hour window)
- New [abuse report](./abuse-report.md) notifications now also appear in the standard notification list (🔔), not just as a realtime toast
- Added an option, for non-JUICE instances that can't interpret the [AI-generated content flag](./ai-generated-flag.md), to synthesize a notice into the ActivityPub summary for AI-generated notes without a CW set (disabled by default)
- Fixed the media timeline not showing plain renotes (not quotes) of posts with images
- Various minor bug fixes

## v2026.9.0-juice+3.5

- Fixed a bug where reloading the page while on the relay or media timeline would unexpectedly send you back to the home timeline
- Added the ability to individually hide the list/antenna/channel shortcut icons shown in the timeline tab bar, via the "Tabs to show" item on the "JUICE" settings page
- Fixed an issue where an error during LD-Signature verification of relay-forwarded posts would cause note delivery to keep failing
- Added an item to [JUICE feature settings](./settings.md) that treats follows from accounts created less than a set amount of time ago as follow requests requiring approval, regardless of the target's own approval-required-following setting (disabled by default; a countermeasure against mass-following by troll/spam accounts right after signup)
- Added an earthquake info widget, listing recent earthquake information (intensity, epicenter, magnitude, and time)
- Added categories to [abuse reports](./abuse-report.md), and reported notes/chat messages can now be previewed on the report detail page for moderators (this is the first way staff can see the content of a reported chat direct message)
- You can now choose the [relay timeline](./relay-timeline.md) or [media timeline](./media-timeline.md) from the Deck "Timeline" column
- You can now drag to reorder the tabs in "Tabs to show" on the [JUICE feature settings](./settings.md) page
- Relaxed the swipe detection on the [media timeline](./media-timeline.md)'s inline carousel, added prev/next buttons for mouse use, and made the switch animation faster
- Added an admin/moderator-only feature to [block a user from your own account before suspending them](./abuse-report.md#block-then-suspend)
- The [emoji request](./emoji-request.md) and [avatar decoration request](./avatar-decoration-request.md) forms now show your current pending count, how many more you can submit, and the per-submission limit
- Added a setting to [JUICE feature settings](./settings.md) that blocks multiple account registrations relying on email address aliases (Gmail's dot-insensitivity and +tag addressing), disabled by default

## v2026.9.0-juice+3.4

- Added the [media timeline](./media-timeline.md), a PixelFed-style dedicated timeline that collects only posts with attached files in a grid/carousel layout (only available if an admin has enabled it). Both video and audio can be played inline, and individual posts can be excluded from it
- Changed the volume setting to be shared across all inline playback in the lightbox and the media timeline (saved locally on the device)
- Which timelines appear in the timeline tab bar can now be individually hidden per viewer from `/settings/juice`

## v2026.9.0-juice+3.3

- Fixed the pending-request warning banner (emoji requests, approval-required signups, etc.) not clearing while the control panel was open, even after the requests were resolved
- Fixed reordering the navigation bar, emoji palette, and widgets on smartphones not working correctly with touch input (especially long-press)
- Fixed buttons (e.g. change avatar, save) overlapping the "Back"/"Continue" footer buttons in the post-signup profile setup dialog on short, landscape-oriented screens

## v2026.9.0-juice+3.2

- New emoji/avatar decoration request notifications, new approval-required signup applications, and new contact form submissions now also appear in the standard notification list (🔔), not just the realtime toast/banner. Role-policy holders who aren't moderators now receive realtime notifications app-wide as well
- [Emoji requests](./emoji-request.md) and avatar decoration requests can now be cancelled by the requester themselves while still pending
- The "Register with invitation code" button on the welcome page / "Add account" menu, and the "Explore other servers" button, can each be hidden via admin settings
- Added a new standard theme, "Juice Orange" (light/dark), based on the JUICE brand color, and set it as the default theme
- The [relay timeline](./relay-timeline.md) now shows which relay each note was delivered through
- Fixed the [display language filter](./post-language.md#timeline-language-filter) not applying to some timelines and realtime streaming. Also revised how notes with no specified language are handled, and how always-showing your own notes is configured
- Added a confirmation dialog before closing the "delete and edit" form to prevent accidental closes, and fixed content being lost when closing without editing
- Fixed remote emoji reaction piggybacking falling back to a heart on upstream Misskey and other forks
- Added English, Korean, and Simplified Chinese translations for JUICE-specific strings

## v2026.9.0-juice+3.1

- The [emoji info menu](./reaction-enhancements.md#emoji-info-menu) now also works for emoji embedded in a note body, CW, or profile, not just reactions
- The maximum number of reaction types on an [announcement reaction](./announcement-reaction.md) is now configurable via role policy (20 by default)
- Added a copyright note about using remote emoji via reaction piggybacking to the admin panel and the in-app [About JUICE page](./about-page.md) as well
- Fixed display and real-time update issues with the Favorites deck column
- Split the job queue widget's notification sound setting into a separate on/off toggle and sound choice

## v2026.9.0-juice+3.0

A major release aligned with tracking upstream Misskey 2026.9.0. Main additions:

- [Reaction enhancements](./reaction-enhancements.md) (piggybacking on reactions, resolving remote custom emoji reactions, a reaction search tab, and more)
- [Post language](./post-language.md)
- [Note search enhancements](./note-search-enhancements.md)
- [Contact form](./contact-form.md)
- Added batch requests, replacement requests, and edit-on-approval to emoji and avatar decoration requests
- The number of users shown in [user ranking](./user-ranking.md) is now configurable from the JUICE settings (default 3)
- Expanded moderation/admin notifications (new emoji requests, contact form submissions, etc. now show in real time in the control panel)
- Localized system emails
- Various security enhancements (broader captcha coverage, notifying users of failed logins, exclusive locking during review, etc.)
- Added a "Favorites" column to the Deck UI
- Added a boot log display and a customizable splash text setting to the loading screen
- The job queue widget's notification sound can now be changed to a sound of your choice

## v2026.7.0-juice+2.5

- Approval/rejection of [emoji requests](./emoji-request.md), avatar decoration requests, and [approval-based signup](./approval-signup.md) can now be delegated per-role to users without moderator permissions

## v2026.7.0-juice+2.4

- Added an "Avatar Decoration Request" page, letting regular users request avatar decorations (using the same mechanism as [emoji requests](./emoji-request.md))
- Fixed JUICE-specific items in the admin panel not showing their badge

## v2026.7.0-juice+2.3

- When a Webhook's destination is a Discord Webhook URL, it's now automatically detected and formatted as a Discord embed

## v2026.7.0-juice+2.2

- Public releases now track the `juice/main` branch starting with this release
- Fixed pgroonga search failing on words containing symbols such as `OR` or `-`
- (Contributed by chan-mai) Fixed file corruption on emoji request approval, timing of the pending-approval check at sign-in, and more

## v2026.7.0-juice+2.1

- Added a contributors section to the in-app [About JUICE page](./about-page.md)

## v2026.7.0-juice+2.0

A major release that added a bundle of JUICE-specific features at once. Main additions:

- [Approval-based signup](./approval-signup.md)
- [AI-generated content flag](./ai-generated-flag.md)
- [Emoji requests](./emoji-request.md)
- [User ranking](./user-ranking.md)
- [Relay timeline](./relay-timeline.md)
- [Widget position setting](./widget-position.md)
- [Announcement polls](./announcement-poll.md)
- [LaTeX (math) rendering](./latex.md)
- Personal nicknames for other users
- Notifying the account owner on failed login attempts
- A new in-app [About JUICE page](./about-page.md)

## v2026.7.0-juice+1.0

The first release, based on Misskey 2026.7.0. Ported from misskey-art:

- Sensitive image display fix (fixed upstream in Misskey 2026.9.0, so this is no longer a JUICE-specific feature)
- [Announcement reactions](./announcement-reaction.md)
- A guard against accidental deletion of the development database
