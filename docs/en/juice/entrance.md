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

If a background image URL is set, the image is laid across the whole page and the panels become semi-transparent. Notes in the timeline and popular sections are also shown semi-transparent (the fade and "Show more" on collapsed long notes stay as usual).

## Other screens when not logged in

When the entrance style is "juice", other screens seen by people who are not logged in (notes, server information, drawing chat rooms, and so on) also use the same look.

- If a background image URL is set, the image is laid across the whole screen, the area behind the page content is blurred, and the panels become semi-transparent. Without a background image, only the top of the screen gets a light tint of the accent color.
- On wide screens, the server introduction and sign-up, along with the numbers of registered users, users online, connected servers, and notes, are shown at the side. On smartphones, the top bar (server name and sign-up button) is also semi-transparent.
- In drawing chat rooms, the area around the canvas is also semi-transparent. The curtain that hides the drawing in rooms with a content warning (CW) is not transparent.

## "Request to join" button

The JUICE badge on the colored "Request to join" button is now filled with the button's text color to make it easier to see. This applies to all entrance styles.

## For developers

`juice` can be specified for `entrancePageStyle` in `admin/update-meta`.
