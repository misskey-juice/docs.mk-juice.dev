# Federation diagnosis

A feature for moderators that helps you find where federation with another server is getting stuck.

## How to use

Open the "Diagnosis" tab on the information page of a federated server (`/instance-info/<host>`) and press "Run diagnosis". It can take a few tens of seconds for the results to appear.

The diagnosis does not deliver anything to the remote server. It only requests information.

## What is checked

### Settings and state on this server

| Item | What it checks |
| --- | --- |
| Federation scope | Whether this server is set not to federate, or to federate only with listed servers and the remote server is not on the list |
| Block | Whether this server blocks the remote server |
| Silence | Whether this server silences or media-silences the remote server |
| Delivery suspension | Whether delivery to the remote server is suspended (manually, because it replied 410 Gone, because it did not respond for a long time, because of its software, and so on) |
| Remote responsiveness | Whether deliveries to the remote server keep failing |
| Last activity received from remote | Whether anything has been received from the remote server, and whether it has stopped for a while |
| Deliveries waiting for retry | Whether any failed deliveries are waiting to be retried |

### Requests to the remote server

| Item | What it checks |
| --- | --- |
| Name resolution (DNS) | Whether the remote domain name can be resolved (not checked when a proxy is configured) |
| HTTPS connection | Whether the remote server can be reached over HTTPS (also checks for expired certificates, name mismatches, and so on) |
| NodeInfo (server information) | Whether the remote server's information can be fetched |
| WebFinger (user lookup) | Whether users can be looked up on the remote server |
| Signed fetch of a user | Whether a remote user known to this server can be fetched with a signed request |
| Inbox (delivery target) response | Whether the remote server's delivery target responds |

## Reading the results

Each item shows one of "OK", "Warning", "Problem", or "Not checked", along with the reason (an HTTP status code, a connection error, and so on). Going through them from the top tells you where federation is stopping.

::: tip
"Signed fetch of a user" may show "OK" even if the remote server blocks this server, because many servers return user information without verifying signatures. Also, if nothing has been received from the remote server for a while, it may have stopped delivering to this server or may be blocking it.
:::

## For developers

The API is `admin/federation/diagnose-instance` (for moderators; requires `write:admin:federation`).
