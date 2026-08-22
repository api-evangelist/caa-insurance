# CAA Insurance (caa-insurance)

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

CAA Insurance Company is a Canadian property and casualty carrier that began underwriting in 1974 and is part of CAA Club Group, with its head office in Thornhill, Ontario. It underwrites personal-lines auto insurance (accident benefits, the CAA MyPace pay-as-you-drive product, CAA Connect telematics, antique and classic vehicles) and personal property insurance (homeowners, condominium, tenant), plus optional endorsements including tire coverage, home equipment breakdown, service line, renewable energy equipment, and legal expense coverage. It sells in British Columbia, Saskatchewan, Manitoba, Ontario, New Brunswick, Nova Scotia, and Prince Edward Island, direct to consumers and through independent brokers.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/caa-insurance/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/caa-insurance/refs/heads/main/apis.yml)

## API Posture

CAA Insurance publishes **no public API and no developer portal**. This is recorded as an honest absence, not an oversight.

- **Developer portal:** none. The `developer.`, `developers.`, `docs.`, and `api.` subdomains do not resolve on either `caainsurancecompany.com` or `caainsurancecompany.ca`, and `/developers`, `/developer`, `/api`, `/partners`, `/integrations`, and `/brokers` all return `404`.
- **OpenAPI / Swagger:** none. Every spec-discovery path probed (`/openapi.json`, `/swagger.json`, `/v1/openapi.json`, `/api-docs`, `/spec`, `/redoc`, `/docs`, `/swagger`, `/swagger-ui.html`) returns `404`. No specification was harvested.
- **Broker integration surface:** partner-gated. [broker.caainsurance.com](https://broker.caainsurance.com/) is a marketing microsite for the broker program, segmented by region, describing business-development support rather than connectivity. Its "Login to Portal" link leads to `caabrokerportal.ca`, which federates to Microsoft Entra External ID (CIAM) over WS-Federation into a SharePoint broker workspace — a login wall.
- **ACORD posture:** no ACORD reference found. Neither ACORD, AL3, ACORD XML, NGDS, IVANS, agency download, Applied, Policy Works, nor Vertafore appears on any public page. Canada's ACORD-derived standards body, CSIO, is likewise never named publicly.
- **Quote / bind / issue / FNOL:** none exposed as an API. Quoting is a hosted consumer web application; claims are reported by phone and web form.
- **Auth model:** no public API authentication exists. The broker portal uses WS-Federation to Entra External ID; the customer portal is a session-login web app that does not serve OIDC discovery anonymously.
- **Webhooks / events / GraphQL / gRPC / Postman:** none published.

Canada has no open-insurance mandate — OSFI supervises federally-regulated insurers prudentially, provincial regulators such as FSRA and the AMF govern market conduct, and Consumer-Driven Banking excludes insurance entirely. With no forcing function, this posture is representative of the Canadian personal-lines carrier tier.

See [review.yml](review.yml) for the full probe log, HTTP statuses, and sources.

## Enrichment round — 2026-07-25

The "no public API" finding stands, but a deeper contract hunt turned up machine-readable descriptions that are **platform-provided, not CAA-authored**:

- **20 SharePoint SOAP WSDLs, 199 operations, served anonymously.** The broker portal `www.caabrokerportal.ca` (TLS certificate issued to *CAA South Central Ontario Systems and Services Inc.*) runs Microsoft SharePoint `16.0.0.5552` on IIS 10 and serves WSDL 1.1 at `/_vti_bin/<service>.asmx?WSDL` for Sites, Webs, UserGroup, WebPartPages, SiteData, Meetings, Imaging, Dws, search/spsearch, Views, Permissions, RecordsRepository, Versions, People, Copy, Alerts, Forms, Authentication, and PublishedLinksService. Harvested verbatim to [`wsdl/`](wsdl/_index.yml). **Not one is an insurance operation** — no quote, bind, issue, or FNOL exists here either; it is document/list/site collaboration, and every data call is authenticated.
- **SharePoint REST/OData present but gated.** `/_api/web` returns `403 System.UnauthorizedAccessException` as `application/json;odata=verbose`.
- **OpenID Connect discovery is real and anonymous.** The Microsoft Entra External ID (CIAM) tenant behind the broker sign-in publishes standards-compliant discovery (scopes `openid profile email offline_access`, mTLS-bound access tokens, RS256). Saved to [`well-known/`](well-known/caa-insurance-well-known.yml).
- **Still absent:** `security.txt`, `llms.txt`, RFC 8414 metadata, any vulnerability-disclosure programme, any trust center, any first-party package on npm/PyPI/any registry, DNSSEC, and CAA DNS records.

Artifacts added this round: [`wsdl/`](wsdl/_index.yml), [`well-known/`](well-known/caa-insurance-well-known.yml), [`authentication/`](authentication/caa-insurance-authentication.yml), [`scopes/`](scopes/caa-insurance-scopes.yml), [`conformance/`](conformance/caa-insurance-conformance.yml), [`conventions/`](conventions/caa-insurance-conventions.yml), [`errors/`](errors/caa-insurance-problem-types.yml), [`security/`](security/caa-insurance-domain-security.yml), [`llms/`](llms/caa-insurance-llms.txt).

## Tags

- Insurance
- Canada
- Property and Casualty
- Auto Insurance
- Home Insurance
- Carrier
- Broker
- Personal Lines
- Telematics
- Partner Gated
- No Public API

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## APIs

None. CAA Insurance exposes no public, documented API.

## Common Properties

- [Website](https://caainsurancecompany.ca/)
- [About](https://caainsurancecompany.ca/about)
- [Blog](https://caainsurancecompany.ca/blog)
- [FAQ](https://caainsurancecompany.ca/faq)
- [Support](https://caainsurancecompany.ca/claims-and-inquires)
- [Login](https://customer.caainsurancecompany.ca/)
- [Partner Portal](https://www.caabrokerportal.ca/)
- [Partners](https://broker.caainsurance.com/) — broker program microsite (marketing, not a developer portal)
- [Privacy](https://caainsurancecompany.ca/privacy)
- [Terms of Service](https://caainsurancecompany.ca/terms-of-use)
- [LinkedIn](https://www.linkedin.com/company/caa-insurance-company/)

## Maintainers

- Kin Lane — kin@apievangelist.com
