# Import approval

A feature that makes imports from Settings → Account data subject to approval by the staff. Imports of types that require approval are not carried out right away; they become requests, and are imported after the staff checks and approves them.

## Which imports need approval

Choose the types that require approval under "Import approval" in the JUICE settings of the control panel. By default only following is included; muting, blocking, lists, and antennas can also be chosen.

## Who reviews

Moderators and people with the role policy "Approve/reject import requests" can review requests. Their own imports are carried out without approval.

## Requesting (for users)

- For types that require approval, the import button becomes "Import (requires approval)". Choosing a file and importing submits a request.
- Under "Import requests" in Settings → Account data, you can see the status of your requests (Pending, Approved, Rejected, Withdrawn) and the reason if one was rejected.
- Pending requests can be withdrawn with "Withdraw".
- While a request of the same type is pending, you cannot submit a new one.
- You are notified when a request is approved or rejected (with the reason if rejected).

## Reviewing (for staff)

- Open the review screen from "Import requests" in the control panel or from the "Tools" menu. You get a notification when a new request arrives, and the admin screen also shows "There are pending import requests."
- Opening a request shows the first lines of the file (up to 100 lines, scrollable within the box), the total count, and counts per account server.
- "Approve and import" approves the request and starts the import; "Reject" declines it with a reason. Approvals and rejections are recorded in the moderation log.

::: warning
If, when you try to approve, the file has been deleted, or the requester has been suspended, deleted, or moved, or no longer has a role that can import, the import is not carried out and the request stays pending (it can still be rejected).
:::

## For developers

- Added `admin/import-requests/{list,show,approve,reject}` and `import-requests/{list,cancel}`.
- `i/import-*` returns `requiresApproval` to indicate whether a request was created.
- `juice/public-settings` and `admin/juice/settings` include `importApprovalRequiredTypes`.
