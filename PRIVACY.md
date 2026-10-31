# Privacy Policy

**Last updated: 2026-10-31**

This policy covers the local client described in [README.md](README.md).

## Summary

The application runs entirely on the user's own computer. It does not send data to any
server operated by the applicant. Nothing is collected, sold, or shared.

## Data the application handles

| Data | Where it is stored | Retention |
| --- | --- | --- |
| Microsoft OAuth access token | Local editor secret storage | Until sign-out or token expiry, then refreshed locally |
| Microsoft OAuth refresh token | Local editor secret storage | Until sign-out or revocation |
| Xbox Live / XSTS tokens | Memory only, per session | Discarded when the session ends |
| Minecraft profile (UUID, username) | Local configuration | Until the user clears it |

No other data is processed.

## Data the application does not handle

- Passwords. Sign-in happens on Microsoft's own pages; the application never sees
  credentials.
- Email address, contacts, calendar, files, or any other Microsoft Graph data.
- Game data, chat, or server content.
- Device identifiers or location.

## Transmission

The only outbound requests are made directly by the local client to Microsoft and
Mojang endpoints:

- `login.microsoftonline.com`
- `user.auth.xboxlive.com`
- `xsts.auth.xboxlive.com`
- `api.minecraftservices.com`

There is no intermediate server, proxy, or analytics endpoint.

## Third parties

No data is shared with third parties. There is no advertising, tracking, or profiling.

## User control

The user can revoke access at any time at <https://account.live.com/consent/Manage>,
and can delete the stored tokens by signing out in the editor or clearing the editor's
secret storage.

## Children

The application is a development tool and is not directed at children.

## Changes

Any change to this policy will be committed to this repository with an updated date.

## Contact

Open an issue in this repository.
