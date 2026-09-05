---
name: screen-a-party-against-the-consolidated-screening-list
description: >-
  Check whether a person, company, vessel or aircraft appears on any U.S. restricted-party
  list consolidated by the Departments of Commerce, State and Treasury — including the four
  Bureau of Industry and Security lists (Denied Persons, Entity, Military End User,
  Unverified) — before an export transaction proceeds.
api: Consolidated Screening List (CSL) API
base_url: https://data.trade.gov/consolidated_screening_list/v1
operations:
  - searchCSL
generated: '2026-09-05'
method: generated
source: openapi/bureau-of-industry-and-security-search-api-openapi.yml
---

# Screen a party against the Consolidated Screening List

## Before you start

- You need an ITA subscription key. Register at <https://developer.trade.gov/signup>, subscribe
  to the "Data Services Platform APIs" product, and send the key as the `subscription-key`
  header. It is free and there is no approval step.
- **This API is operated by the International Trade Administration, not by BIS.** BIS
  contributes four of the thirteen source lists. The host is `data.trade.gov`.
- The surface is read-only. Nothing you call here can change anything, so there is no
  idempotency key to set and nothing to undo.

## Steps

1. **Search by name.** Call `searchCSL` — `GET /search` — with `name` set to the party you are
   screening. Send `subscription-key` as a header.

2. **Widen with fuzzy matching when an exact name returns nothing.** Add `fuzzy_name=true`.
   It only works together with `name`. Fuzzy search strips common words — `co`, `company`,
   `corp`, `corporation`, `inc`, `incorporated`, `limited`, `ltd`, `mrs`, `ms`, `mr`,
   `organization`, `sa`, `sas`, `llc`, `university`, `univ` — so "Water Corporation" and
   "Water" return the same results.

3. **Narrow only when you have a reason to.** `sources` restricts the search to named lists;
   the BIS lists are `DPL`, `EL`, `MEU`, `UVL`. `types` restricts to `Individual`, `Entity`,
   `Vessel` or `Aircraft`. `countries` takes ISO 3166-1 alpha-2 codes, comma separated.
   **Do not narrow by source for a compliance screen** — the point of the consolidated list
   is that you check all of them.

4. **Add address filters if a name is ambiguous.** `address`, `city`, `state` and
   `postal_code` each match inside the `addresses` array. `full_address` searches all four at
   once and, when present, causes the individual four to be ignored.

5. **Page carefully, and know the ceiling.** `size` returns at most **50** results and
   `offset` cannot exceed **1000** — together they cap paginated retrieval at roughly the
   first 1,050 matches. If a query is that broad, it is the wrong query; tighten it, or use
   the bulk download instead (see the companion skill).

6. **Read the result, do not act on a match alone.** Each result carries `source` (the
   originating list), `type`, `name`, `alt_names`, `programs`, `addresses`, `ids`,
   `remarks`, `license_requirement`, `license_policy` and `federal_register_notice`, plus
   `source_list_url` and `source_information_url` pointing at the authoritative publication.
   A hit means additional due diligence is required — there may be a strict export
   prohibition, a licence requirement, or an end-use evaluation to perform. Follow the
   source URLs; the API is an aid to screening, not a determination.

## Handling failures

- **401** — the key is missing or wrong. The response body says so and the
  `WWW-Authenticate: AzureApiManagementKey` header names the parameter. Do not retry without
  fixing the key.
- **404** — you dropped the `/v1` segment. The path is
  `/consolidated_screening_list/v1/search`.
- **429** — throttled. The provider publishes no limit numbers and returns no
  `Retry-After` or `RateLimit-*` headers, so back off exponentially and, if you are screening
  in volume, switch to the bulk download.
- Error bodies are `{"statusCode": N, "message": "..."}` — not RFC 9457 problem+json. There
  is no error code to branch on beyond the HTTP status. The `x-azure-ref` response header is
  the only value worth logging for a support conversation (DataServices@trade.gov).

## Data handling

Records of `type: Individual` are real people, with dates of birth, places of birth,
nationalities and identity document numbers. Do not paste live records into prompts, logs,
tickets or examples. Retain only what your compliance process requires.

## Freshness

The list is rebuilt daily at 05:00 ET. The API "only contains active entities on the list";
for historical research, go to the source lists directly.
