# Custom Emoji & Avatar Decoration Guidelines

When requesting custom emoji or avatar decorations, please follow the guidelines below. Please also check the [Rules](./rules.md) and [Terms of Service](./tos.md).

## General notes

- If you use material that requires attribution (e.g. free material that requires crediting the source under its terms), please accurately state the source, author name, and type of license in the "License" field. If it's your own work, or material that doesn't require attribution, you don't need to force something into that field.
- Requests that use the logo or trademark of a real company or organization without permission will be rejected. However, if the logo image has a license that explicitly permits its use (e.g. official material distributed by the company), it's fine to submit it — just note the company's official URL and the image's license in the "License" field.
- Images containing NSFW, violent, or discriminatory content cannot be requested. This follows the same standard as the [Rules](./rules.md).
- Requests for uses outside the intended purpose, such as recreating expressions that violate public order and morals, will also be rejected.
- If we're unsure about something, we may reach out individually during review. Don't overthink it — feel free to submit a request.

## Custom emoji

- Please make the name and category clear and easy to distinguish from other emoji.
- We recommend an image resolution of up to 512px on each side.
- A request is kept pending until it is approved or rejected. If rejected, you will be notified of the reason. If you want to request again, please submit it as a new request.
- For details on how to submit a request, see [Emoji requests](../juice/emoji-request.md).

### Bringing in emoji from another instance

Misskey has a culture of downloading custom emoji used on other instances and importing them into your own. You're welcome to request the same here if you'd like to use an emoji from another instance as-is.

- If the source specifies a license, please state it in the "License" field accordingly.
- If the source doesn't have any license information either, it's enough to just write the name of the instance you got it from in the "License" field. Not knowing the exact license is not a reason to give up on requesting it.
- However, please don't request emoji whose original author has explicitly said not to reuse/redistribute them, or ones that clearly cause problems, such as the logo or trademark of a real company.

### Text emoji and fonts

If your emoji includes text, please pay attention to the license of the font you used. What matters isn't whether it's free or paid — it's **whether the font's license permits commercial use**. Many free fonts restrict commercial use, modification, or redistribution, and conversely, whether a paid font permits commercial use varies by product.

- Please confirm for yourself that the license allows this use before requesting it.
- In case there's any doubt, or the reviewer needs to check, it helps to note the font name, where you obtained it, and a link to its license in the "License" field.
- If you hand-drew the text or used a vector tool instead of a font, mentioning that also makes review smoother.

## Avatar decorations

- Uses the same request mechanism as custom emoji — you submit an image, name, category, and license.
- Since this is displayed layered on top of a profile icon, please design it with a transparent background so it can be layered onto an icon.
- We recommend an image resolution of up to 512px on each side.

## About approval

Approval or rejection of requests is handled by the admin, or by a user who has been delegated approval permissions through a role. Requests that do not follow the guidelines above may be rejected.

## Frequently asked questions

### What should I write in the "License" field for an emoji I drew myself?

Write your own Misskey ID (for example, `@c30`). If you used materials, write where they came from and the license name (such as CC BY-SA 4.0).

### Can I bring in emoji from another server? What if I don't know the license?

Yes, you can request them. If the source states a license, follow it; if nothing is stated, writing the name of the source server in the "License" field is enough. However, do not request emoji whose creators have said "please don't repost," or ones that are clearly problematic, such as company logos.

### What should I watch out for with fonts used in emoji that contain text?

What matters is not whether the font is paid or free, but **whether the font may be used commercially**. It is safest to write the font name and a URL where its license can be checked in the "License" field. If you lettered it without a font, please say so.

### Can I request company logos?

As a rule, they are rejected. However, if the logo is officially distributed as material and its license clearly allows use, it is fine if you write the company's official URL and the image's license in the "License" field.

### How many requests can I make?

On Juice Server, you can currently have up to 200 pending requests each for emoji and avatar decorations, and send up to 256 times each per day (the last 24 hours) (this may vary by role). You can submit up to 10 requests at once. The request form shows how many more requests and submissions you have left.

### How large should the image be?

Up to 512px in both width and height is recommended. Avatar decorations are shown on top of the profile icon, so design them to be layered, for example with a transparent background.

### What happens if my request is rejected?

You will receive a notification with the reason. If you want to request it again, fix it based on the reason and submit it as a new request.

### What happens to the image I used for the request?

When requesting, you can choose whether to delete the image after review. If you choose to delete it, the drive file is deleted when the review is finished, whether the request is approved or rejected. If approved, the image is copied to the emoji, so deleting the file does not affect the emoji.

### When should I turn on "Sensitive" and "Local only"?

- **Sensitive**: turn it on for designs that not everyone may want to see, or that come close to the NSFW criteria in the [rules](./rules.md). Sensitive emoji cannot be used as reactions on notes set not to accept sensitive reactions.
- **Local only**: turn it on for emoji you want to use only within this server. When on, the emoji's image is not sent to other servers (on other servers, it may appear only as its name).

### Can I make emoji of lines spoken by copyrighted characters?

Please do not use **images cut directly from anime or manga screens or panels**. Turning a line into a text emoji with a tool such as [MEGAMOJI](https://zk-phi.github.io/MEGAMOJI/) is fine. However, be careful with lines that spoil the story.

When requesting, please fill in the following:

- **Category**: `文字/版権/<title of the work>`
  - If the work has an official abbreviation, use that abbreviation as the title (for example, Misskey Juice → `JUICE`, アイドルマスター (THE IDOLM@STER) → `アイマス`, 僕のヒーローアカデミア (My Hero Academia) → `ヒロアカ`).
- **Tags**: title of the work and name of the character who says the line (recommended)
  - Please write the character name in hiragana.
  - If the name is not Japanese (such as an English name), also write it in hiragana, and replace "・" with a space so the parts become separate tags (for example, John Smith → `じょん すみす`).

For detailed request steps, see [emoji requests](../juice/emoji-request.md) and [avatar decoration requests](../juice/avatar-decoration-request.md).
