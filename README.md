# CAA Insurance (caa-insurance)

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
- [Portal](https://broker.caainsurance.com/)
- [Privacy](https://caainsurancecompany.ca/privacy)
- [Terms of Service](https://caainsurancecompany.ca/terms-of-use)
- [LinkedIn](https://www.linkedin.com/company/caa-insurance-company/)

## Maintainers

- Kin Lane — kin@apievangelist.com
