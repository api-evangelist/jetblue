# JetBlue (jetblue)

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

This is an honest identity-only record. There is no public API to harvest. See [review.yml](review.yml) for the full switching-cost analysis and every probed URL with its HTTP status.

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
