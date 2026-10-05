# JUICE entrance

A JUICE-specific "juice" style has been added for the welcome page (entrance) shown to people who are not logged in.

## How to switch

Admins can choose "juice" under "Entrance page style" in Control panel → Branding. You can switch between it and upstream's classic and simple styles.

## What is shown

Alongside the server introduction and sign-up panel, it shows:

- The number of registered users, users online, connected servers, and notes
- The local timeline
- Popular content (trending tags and popular posts)
- Activity
- Some of the connected servers

On narrow screens such as smartphones, these are arranged in a single column.

## Adapting to settings

- If "Show activities" or "Show timeline" (settings for visitors) is turned off, that part is not shown.
- The display also adapts when the local timeline is unavailable or when the server is set not to federate.

## Background image

If a background image URL is set, the image is laid across the whole page and the panels become semi-transparent (notes in the timeline keep their usual background).

## "Request to join" button

The JUICE badge on the colored "Request to join" button is now filled with the button's text color to make it easier to see. This applies to all entrance styles.

## For developers

`juice` can be specified for `entrancePageStyle` in `admin/update-meta`.
