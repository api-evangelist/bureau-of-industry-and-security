---
name: load-the-consolidated-screening-list-in-bulk
description: >-
  Load the entire U.S. Consolidated Screening List — every restricted party from the
  Commerce/BIS, State and Treasury lists — with no API key, and keep a local copy fresh with
  conditional requests. The right approach when you screen in volume, screen offline, or
  build and test matching logic before requesting credentials.
api: Consolidated Screening List — bulk distributions
base_url: https://data.trade.gov/downloadable_consolidated_screening_list/v1
operations: []
generated: '2026-09-05'
method: generated
source: >-
  https://www.bis.gov/data.json (BIS DCAT-US 3.0 catalog) ·
  https://www.trade.gov/consolidated-screening-list · live probes 2026-09-05
---

# Load the Consolidated Screening List in bulk

## Why this exists

The query API is rate limited with numbers nobody publishes, and paginated retrieval is
capped at roughly the first 1,050 matches per query. The complete dataset, by contrast, is
served **with no key at all** and refreshed daily. For any workload that screens more than a
handful of names, this is the supported path — and it is the one BIS itself points at: its
own DCAT-US catalog at <https://www.bis.gov/data.json> lists exactly one dataset, the
Consolidated Screening List, with these three distributions and nothing else.

## Steps

1. **Choose a format.** All three carry the same records:
   - `https://data.trade.gov/downloadable_consolidated_screening_list/v1/consolidated.json`
   - `https://data.trade.gov/downloadable_consolidated_screening_list/v1/consolidated.csv`
   - `https://data.trade.gov/downloadable_consolidated_screening_list/v1/consolidated.tsv`

2. **Fetch it.** No credential, no header, no account. The JSON distribution was
   33,683,407 bytes when measured on 2026-09-05, so stream it rather than buffering it.

3. **Refresh conditionally, once a day.** The response carries a strong `ETag` and
   `Last-Modified`. Store both and send `If-None-Match` on the next fetch; a `304` means
   nothing changed and costs you nothing. Schedule the fetch after **05:00 ET**, which is
   when the provider rebuilds the file. Note that the response also sets
   `Cache-Control: no-store` — do not expect a CDN or proxy to hold a copy for you.

4. **Index the records.** Each record carries `name`, `alt_names`, `type`, `source`,
   `programs`, `addresses[]`, `ids[]`, `remarks`, `source_list_url` and
   `source_information_url`. Index `name` **and** `alt_names` together — many entries are
   only findable under an alias.

5. **Do not use `entity_number` as a primary key.** It is assigned by the originating list
   and is not unique across sources. Use `id`, or the `source` + `entity_number` pair.

6. **Filter by source when you need only the BIS lists.** The `source` field carries the
   human-readable list name; the BIS lists are the Denied Persons List, the Entity List, the
   Military End User List and the Unverified List.

## What this does not give you

Fuzzy name matching. The query API's `fuzzy_name=true` is a server-side capability with its
own common-word stripping; if you match locally you have to implement your own and you will
get different results. A common pattern is to screen locally against the bulk file for
throughput and confirm every candidate hit through `searchCSL` with `fuzzy_name=true`.

## Data handling

Records of `type: Individual` are real people, carrying dates of birth, places of birth,
nationalities and identity document numbers. The file is public, but it is person data:
store it with the same controls you apply to any personal dataset, and never paste records
into prompts, logs or examples.
