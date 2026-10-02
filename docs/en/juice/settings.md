# JUICE feature settings

Juice Server has several original features not found in standard Misskey. Settings for these original features are grouped together under the **"JUICE" item** in the control panel, organized into three categories: "Account", "Timeline & display", and "Request forms".

## Main items you can configure

After logging in with an admin account, go to Control Panel → "JUICE" to change the following kinds of settings — enabling/disabling original features and various options:

- Enable/disable each [social login](./social-login.md) provider (Discord, Google, GitHub, GitLab, Microsoft), and set its client ID, client secret, and the shared redirect URI
- Enable/disable [approval-based signup](./approval-signup.md), whether a registration reason is required, and its maximum character count
- Enable/disable treating follows from accounts created less than a set amount of time ago as follow requests requiring approval, regardless of the target's own approval-required-following setting, and the age threshold
- The aggregation period and number of users shown for [user ranking](./user-ranking.md)
- Enable/disable the [relay timeline](./relay-timeline.md)
- Enable/disable the [media timeline](./media-timeline.md)
- The maximum file size the [MIDI player](./midi-player.md) will play back (default 500KB), and the piano roll visualizer's enabled state, roll speed, and max polyphony
- Enable/disable [emoji requests](./emoji-request.md) and avatar decoration requests, the limit on simultaneous requests, the daily submission limit, and which fields (category, tags, license, description) are required
- Enable/disable [LaTeX (math) rendering](./latex.md)
- Enable/disable the [contact form](./contact-form.md), manage its categories, and set the maximum body length
- Enable/disable [drawing chat](./draw-room.md), and the max stroke data per room
- Show avatar decorations of users on Misskey-based servers (Misskey, CherryPick, Sharkey) (enabled by default)
- Manage [abuse report](./abuse-report.md) categories
- Reject email addresses with a +tag (`name+tag@…`) or Gmail addresses containing dots (`na.me@gmail.com`) for new signups and email address changes. Disabled by default; +tags and Gmail dots can be toggled independently. It applies regardless of whether a matching account already exists, and the signup screen shows the reason. The contact form is not affected
- Show/hide the "Register with invitation code" button on the welcome page / "Add account" menu, and the "Explore other servers" button
- The custom splash text shown on the loading screen at startup

Per-user settings (such as [widget position](./widget-position.md), which timelines appear in the timeline tab bar and their order, auto-local-only for posts containing decorative MFM, the search engine used by MFM search boxes, or the favorite and reaction buttons next to a note's "+" button, the setting to not nyaize cat posts, or the setting to [disable downloads of attached novel .txt files from the start](./novel.md#preventing-downloads-of-attached-txt-files)) are changed separately, from `/settings/juice`.

For details on each feature, see its respective page.
