# Avatar decoration requests

A feature that lets regular users request the addition of an avatar decoration. It works the same way as [emoji requests](./emoji-request.md).

## How to submit a request

From the avatar decoration request page, submit the following items:

- Decoration image
- Name
- Description
- Category

Fields such as category and description may be individually required by admin settings. Required fields are labeled "(Required)", and the submit button is disabled while they're empty. When submitting multiple items at once, a warning badge appears on the header of any card with an empty required field.

A request is kept pending until it is either rejected or approved. Once approved, it becomes usable as an avatar decoration right away. If rejected, you will be notified of the reason. If you want to try again, please submit it as a new request. While a request is still pending, you can cancel it yourself.

## Items worth preparing in advance

Having the following ready beforehand makes filling out the form quicker.

```
Decoration name:
Description:
Category:
```

- We recommend an image resolution of up to 512px on each side.

## Request limit

There is a limit on the number of requests (pending review) you can have out at the same time (default 3). There is also a rate limit to prevent continuous requests. The request form shows your current pending count, how many more you can submit, and the maximum number of items you can submit in a single batch (up to 10).

Separate from the pending-request limit, there's also a limit on how many requests you can submit per day (default 5, on a rolling 24-hour window). The request form also shows how many submissions you have left and when your next slot will free up.

## Handling of requested images

At the time of the request, you can choose whether to delete the image once the review is complete. If checked, the drive file is deleted upon completion of review, whether approved or rejected (since the image is copied to the decoration itself upon approval, deleting the original does not affect the decoration).

## Replacing the image of a pending request

While a request is pending review, the requester can replace just its image.

- In your list of requests, choose "Replace image" on a pending request and select a new image (from the drive, your device, or a URL; when choosing from your device, only image files can be selected).
- After replacing, the thumbnail in the list changes to the new image right away.
- If the request was set to delete the image after review, the previous image that is no longer used is deleted (it is not deleted if another request uses the same image).
- Everything other than the image, such as the name and category, stays the same. To change the image of an avatar decoration that has already been created, use a "replacement request" instead.

::: info For moderators
If the image you were looking at on the review screen has since been replaced by the requester, approving or rejecting is refused with "the image has been replaced." Reload the list, check the current image, and review again.
:::

## Reviewing (for moderators)

- On the review screen, you can select requests and approve or reject them together. Even when processed together, notifications and emails to the requester and moderation log entries are still recorded per request.
- Requests submitted together in one go are sent to moderators as a single new-request notification and a single System Webhook (the notification shows "and N more").

::: warning If you receive System Webhooks
Since v3.19, the `avatarDecorationRequestCreated` payload includes the number of requests `count` and the list of requests `requests`. `id`, `name`, and `category` are those of the first request. If you were processing webhooks on the assumption that one arrives per request, update your handler to look at `requests`.
:::
