# Minecraft Workbench Auth

Application registration documentation for a local, single-user OAuth 2.0 client used
in a Visual Studio Code workflow for **Minecraft: Java Edition** mod development.

This repository exists to document the OAuth application and its data handling for
reviewers. There is no hosted service, no backend, and no user data collection.

---

## What this application does

The application is a **public client** (native/desktop) that authenticates the
developer's own Microsoft account through the **OAuth 2.0 device authorization grant**
(RFC 8628).

Authentication chain:

1. Microsoft identity platform — device code flow, scopes `XboxLive.signin` and `offline_access`
2. Xbox Live user authentication (`user.auth.xboxlive.com`)
3. XSTS authorization (`xsts.auth.xboxlive.com`)
4. Minecraft Services (`api.minecraftservices.com`) — `login_with_xbox`, then the
   signed-in account's own profile (UUID and username)

The Minecraft Services calls are used only to:

- confirm that the signed-in account owns Java Edition,
- read that account's own profile so the local tool can address it correctly,
- allow the developer to launch the game client for local testing against a
  development server.

## What this application does not do

- No client secret is created or used. It is a public client only.
- No redirect URI is configured. Device code flow does not require one.
- No backend server. The client runs entirely on the user's machine.
- No telemetry, analytics, or crash reporting.
- No collection, storage, sale, or sharing of account data.
- No access to any account other than the one the user signs in with.
- No modification of Minecraft services data.

## Token handling

Access tokens and refresh tokens are stored only in the local editor's secret storage
(VS Code `SecretStorage`) on the user's own machine. Tokens are never transmitted to a
server controlled by the applicant, and are never logged.

## Scopes requested

| Scope | Purpose |
| --- | --- |
| `XboxLive.signin` | Sign in with a Microsoft account through Xbox Live |
| `offline_access` | Refresh the session locally without repeated sign-in |

No Microsoft Graph permissions are requested. No directory data is read.

## Application details

| Field | Value |
| --- | --- |
| Application (client) ID | `2d3135da-ba54-4e5d-9a99-883c47e74de3` |
| Client type | Public client / native |
| Redirect URI | None |
| Client secret | None |
| Sign-in audience | Multitenant + personal Microsoft accounts |

## Status

Minecraft Services access requires an allow-listed application ID. Requests to
`api.minecraftservices.com/authentication/login_with_xbox` from unregistered clients are
rejected with HTTP 403 `Invalid app registration`. An approval request has been submitted
through the official Mojang review process.

## Contact

Open an issue in this repository.

## Privacy

See [PRIVACY.md](PRIVACY.md).
