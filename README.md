# Spreaker (spreaker)

Spreaker is a podcast hosting, distribution, and monetization platform owned by iHeartMedia (acquired via parent company Voxnest in 2020). It lets creators record, host, and publish podcasts, auto-distribute to Apple Podcasts, Spotify, and iHeartRadio, and monetize through programmatic ads, listener subscriptions, and a Supporters Club. Spreaker exposes a documented public REST API (v2) over HTTPS at `api.spreaker.com`, authenticated with OAuth2, covering users, shows, episodes, playback and messaging, analytics/statistics, search and discovery, and advertising campaign management.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/spreaker/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/spreaker/refs/heads/main/apis.yml)

## Access Model

- **Public REST API (v2):** Base URL `https://api.spreaker.com/v2`. All access is over HTTPS.
- **Authentication:** OAuth2. Users are redirected to `https://www.spreaker.com/oauth2/authorize`; tokens are exchanged and refreshed at `https://api.spreaker.com/oauth2/token`. The access token is sent as a `Authorization: Bearer <token>` header (or as a query parameter). The only current scope is `basic`.
- **Read vs. write:** `GET` requests are generally public and do not require authentication unless documented; all `PUT`, `POST`, and `DELETE` requests must be authenticated.
- **Pagination:** Responses default to 50 items per page (up to 100 via the `limit` parameter) and include a `next_url` property for the next page.
- **Rate limiting:** Excessive requests result in temporary IP blacklisting and a `429 Too Many Requests` response. No fixed numeric threshold is published.
- **No WebSocket:** Spreaker's public surface is entirely request/response REST. Audio is streamed and downloaded over HTTPS and distributed via RSS; there is no documented WebSocket or server-push API.
- **SDK:** Spreaker publishes an official open-source JavaScript SDK ([spreaker/api-sdk-js](https://github.com/spreaker/api-sdk-js)) that wraps the v2 REST API. The platform itself is proprietary and hosted.

## Tags

- Podcasting
- Podcast Hosting
- Audio
- Media
- Monetization
- Analytics

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

### Spreaker Users API

Retrieve and update Spreaker user profiles, resolve the authenticated user via `/me`, and manage the social graph - followers, followings, and blocked users.

- **Human URL:** [https://developers.spreaker.com/api/users/](https://developers.spreaker.com/api/users/)
- **Base URL:** `https://api.spreaker.com/v2`

### Spreaker Shows API

Create, retrieve, update, and delete podcast shows, list a user's shows, manage favorite shows, and read supporting reference data such as show categories and languages.

- **Human URL:** [https://developers.spreaker.com/api/shows/](https://developers.spreaker.com/api/shows/)
- **Base URL:** `https://api.spreaker.com/v2`

### Spreaker Episodes API

Upload, update, and delete episodes, create drafts, stream and download audio, and manage engagement and enrichment - likes, bookmarks, listener messages, chapters, and ad cuepoints.

- **Human URL:** [https://developers.spreaker.com/api/episodes/](https://developers.spreaker.com/api/episodes/)
- **Base URL:** `https://api.spreaker.com/v2`

### Spreaker Statistics API

Read playback, likes, followers, source, device, OS, and geographic analytics at the user, show, and episode level, plus rolled-up totals across a user's shows and episodes.

- **Human URL:** [https://developers.spreaker.com/api/statistics/](https://developers.spreaker.com/api/statistics/)
- **Base URL:** `https://api.spreaker.com/v2`

### Spreaker Search and Discovery API

Search shows and episodes globally or scoped to an author or show, browse explore categories, list latest episodes by tag, and embed players via the oEmbed provider.

- **Human URL:** [https://developers.spreaker.com/api/search/](https://developers.spreaker.com/api/search/)
- **Base URL:** `https://api.spreaker.com/v2`

### Spreaker Advertising Campaigns API

Manage the direct ad-sales stack available on the Publisher plan - advertisers, campaigns, and targeted line items - including country targeting for campaign delivery.

- **Human URL:** [https://developers.spreaker.com/api/advertisers/](https://developers.spreaker.com/api/advertisers/)
- **Base URL:** `https://api.spreaker.com/v2`

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/spreaker)
- [Website](https://www.spreaker.com)
- [Documentation](https://developers.spreaker.com/guides/)
- [Plans](plans/spreaker-plans-pricing.yml)
- [Rate Limits](rate-limits/spreaker-rate-limits.yml)
- [Fin Ops](finops/spreaker-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
