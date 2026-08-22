# JetBlue (jetblue)

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

JetBlue Airways (IATA code B6) is a New York-headquartered low-cost United States carrier flying across the U.S., Caribbean, Latin America, and Europe, with hubs and focus cities at JFK, Boston, Fort Lauderdale, Orlando, and San Juan. It owns its own inventory and sells it through three channels: a direct consumer surface (jetblue.com, the JetBlue app, TrueBlue), the legacy GDS channel settled through ARC and IATA BSPs, and an IATA New Distribution Capability program reached via GDS/NDC aggregators, corporate booking tools, and online booking platforms.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/jetblue/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/jetblue/refs/heads/main/apis.yml)

## API Posture

JetBlue publishes **no public developer portal, no API reference, and no downloadable OpenAPI or NDC schema**. `developer.jetblue.com`, `developers.jetblue.com`, `docs.jetblue.com`, `apis.jetblue.com`, `ndc.jetblue.com`, and `partners.jetblue.com` do not resolve. `api.jetblue.com` resolves behind Fastly but returns HTTP 404 at `/`, `/v1`, `/docs`, `/ndc`, `/openapi.json`, `/swagger.json`, and `/.well-known/openapi.json` — it is an internal edge host for the jetblue.com clients, not a published API product. The 361-URL public sitemap contains no developer, API, sandbox, or portal page.

The two airline surfaces must not be conflated:

- **Consumer surface** — flight status, booking, check-in, and TrueBlue exist only on jetblue.com and in the mobile app. The website terms (section 9.1.5) explicitly forbid access "by using any manual process, or any 'robot,' 'spider,' 'deep-link,' 'page-scrape,' or any other automatic device, program, algorithm or methodology without first obtaining the prior written consent of JetBlue."
- **Distribution surface** — [jetblue.com/travel-agents](https://www.jetblue.com/travel-agents) is the only published third-party channel. Every documented workflow is a GDS workflow: fares filed in the GDS, bags and priority security and seat assignments sold as GDS EMDs (explicitly "not available in Apollo and Worldspan"), SSR codes in the PNR, and settlement through ARC (U.S.) or IATA BSP (international).

### NDC

[jetblue.com/travel-agents/ndc](https://www.jetblue.com/travel-agents/ndc) is a live NDC program page. It states most agencies connect via GDS/NDC aggregators, corporate booking tools, and online booking platforms, and that JetBlue "also supports direct integrations for TMCs and technology partners with development capabilities" through business use case submission → onboarding → certification testing → go-live. JetBlue says it provides NDC API documentation, schema and message samples, certification and testing guidelines, and release notes — **all partner-only**. No NDC version, no IATA certification level, no endpoint hostname, and no GDS surcharge are published. The only public entry points are `ndcsales@jetblue.com` and `ndcsupport@jetblue.com`.

### Access gate

Selling JetBlue requires full **ARC accreditation** in the U.S., or **IATA accreditation plus local BSP participation** internationally followed by an emailed ticketing-authority request. JetBlue grants authority "as we deem appropriate" and can remove it. OTAs are effectively closed: "We only work with a few Online Travel Agencies (OTAs) and we are not accepting new applications at this time. Please do not give your inventory or plating access to an OTA, or you will lose your ticketing plate and access to inventory."

### The one machine-readable contract

The 2026-07-28 enrichment round found exactly one document JetBlue serves anonymously and machine-readably: the **OpenID Connect discovery** document (and its RFC 8414 sibling) at [accounts.jetblue.com/.well-known/openid-configuration](https://accounts.jetblue.com/.well-known/openid-configuration) — the Okta-hosted identity provider behind jetblue.com sign-in and the TrueBlue account. It advertises authorization_code, implicit, refresh_token, password, device_code and CIBA grants, PKCE (S256), DPoP, PAR, introspection and revocation. It is the **consumer identity backend for JetBlue's own clients**, not a partner or NDC API, and no third-party client-onboarding path is published — so `apis[]` stays empty. The document is harvested verbatim to `well-known/` and read into `authentication/`, `scopes/` and `conformance/`.

JetBlue also runs a **[Vulnerability Disclosure Program on HackerOne](https://hackerone.com/jetblue)** under a published [policy](https://www.jetblue.com/legal/vulnerability-disclosure-policy) with safe harbor and coordinated disclosure — but serves no `/.well-known/security.txt` on any host, so the program is not machine-discoverable.

There is no status page (`jetblue.statuspage.io` redirects to `/inactive`, `status.jetblue.com` does not resolve), no JetBlue GitHub organization, and no first-party SDK in any package registry.

## Artifacts

| Artifact | File |
|---|---|
| Well-known probe index | [well-known/jetblue-well-known.yml](well-known/jetblue-well-known.yml) |
| OIDC discovery (verbatim) | [well-known/jetblue-openid-configuration.json](well-known/jetblue-openid-configuration.json) |
| OAuth AS metadata (verbatim) | [well-known/jetblue-oauth-authorization-server.json](well-known/jetblue-oauth-authorization-server.json) |
| Authentication profile | [authentication/jetblue-authentication.yml](authentication/jetblue-authentication.yml) |
| OAuth scopes | [scopes/jetblue-scopes.yml](scopes/jetblue-scopes.yml) |
| Standards conformance | [conformance/jetblue-conformance.yml](conformance/jetblue-conformance.yml) |
| Vulnerability disclosure | [security/jetblue-vulnerability-disclosure.yml](security/jetblue-vulnerability-disclosure.yml) |
| Domain security | [security/jetblue-domain-security.yml](security/jetblue-domain-security.yml) |
| Packages / SDK survey | [packages/jetblue-packages.yml](packages/jetblue-packages.yml) |
| MCP survey | [mcp/jetblue-mcp.yml](mcp/jetblue-mcp.yml) |
| llms.txt | [llms/jetblue-llms.txt](llms/jetblue-llms.txt) |

This remains an honest, near-identity-only record: there is no public JetBlue API to harvest. See [review.yml](review.yml) for the full switching-cost analysis and every probed URL with its HTTP status.

## Tags

- Travel
- United States
- Aviation
- Airline
- Distribution
- NDC
- GDS
- Booking
- Loyalty

## Timestamps

- **Created:** 2026-07-28
- **Modified:** 2026-07-28

## APIs

No public API is documented by JetBlue. See the API posture above.

## Common Properties

- [Website](https://www.jetblue.com/)
- [About](https://www.jetblue.com/our-company)
- [Brands](https://www.jetblue.com/our-company/our-brands)
- [Partner Program](https://www.jetblue.com/travel-agents)
- [Documentation](https://www.jetblue.com/travel-agents/ndc)
- [Onboarding](https://www.jetblue.com/travel-agents/ticketing-authority)
- [Policies](https://www.jetblue.com/travel-agents/booking-policies)
- [Terms of Service](https://www.jetblue.com/legal/website-terms)
- [Privacy Policy](https://www.jetblue.com/legal/privacy)
- [Legal](https://www.jetblue.com/legal)
- [Contract of Carriage](https://legacycms.jetblue.com/public/dam/ui-assets/p/contract_of_carriage.pdf)
- [Vulnerability Disclosure](https://www.jetblue.com/legal/vulnerability-disclosure-policy)
- [Support](https://www.jetblue.com/contact-us)
- [LinkedIn](https://www.linkedin.com/company/jetblue)

## Maintainers

- Kin Lane — kin@apievangelist.com
