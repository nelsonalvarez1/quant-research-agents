---
name: market-data-integration
description: Integrate a newly released market-data API or provider behind a provider-neutral adapter.
---

# Market data integration

Inspect official documentation and sample responses for authentication, endpoints, rate limits and schema. Keep credentials outside Git. Isolate requests and parsing in a provider adapter that emits documented, validated records.

Preserve source timestamps, timezone, availability time, instrument identifiers and provenance. Handle pagination, retries, gaps, duplicates and revisions according to provider semantics. Test with sanitised fixtures before connecting strategy code. Keep vendor-specific fields out of signal logic.
