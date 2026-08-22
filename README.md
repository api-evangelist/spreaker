# Spreaker (spreaker)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
