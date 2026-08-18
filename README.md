# Benefits

A machine-readable list of the outcomes an API claims to produce for the people who adopt
it — not what it does, but what changes for them.

This is the schema behind the [Benefits property](https://apicommons.org/common/benefits/)
in [API Commons](https://apicommons.org).

## Why this one is worth doing

Benefits are the softest thing an API publishes and the first thing a buyer reads. This
schema is not an attempt to make marketing rigorous. It is an attempt to make it
**accountable**.

Three optional fields do that work:

- **`audience`** — who the benefit accrues to. A claim that names no audience is usually
  being made to everyone and landing with no one. The same API frequently benefits a
  developer and a buyer for opposite reasons.
- **`metric`** — the thing that would have to move for the claim to be true. The measure,
  not the number: *"days from signup to first successful call"*. A benefit with no metric
  is not falsifiable.
- **`evidence_url`** — a case study or benchmark substantiating it. Its **absence is
  informative**. Do not invent one.

Fill those in and the claims that cannot be checked separate themselves from the ones
that can, without anyone having to make the argument. The examples here deliberately
include entries with no metric and no evidence, including one that is a pure slogan,
because real benefits pages are like that and the schema's job is to make it legible
rather than to hide it.

## Artifacts

- **[benefits-json-schema.yml](benefits-json-schema.yml)** — the JSON Schema (2020-12).
- **[benefits-example-1.yml](benefits-example-1.yml)** — a standalone list for a made-up
  embedded-integration platform.
- **[benefits-example-2.yml](benefits-example-2.yml)** — the `Benefits` property envelope,
  split by audience.
- **[validate.py](validate.py)** — validates any document against the schema.

## Using it

```yaml
- name: Reduce onboarding time
  description: Get a new customer's integrations live without a services engagement.
  url: https://example.com/benefits
  audience: business        # developer | architect | product | business | operations
                            # | security | compliance | partner | end-user
  category: speed
  metric: days from contract signature to first successful customer integration
  evidence_url: https://example.com/case-studies/onboarding
  features:
    - Integration designer
```

Only `name` is required. `features` should use the same names as the
[Features](https://github.com/api-commons/features) property, so a claim links to the
thing that supposedly delivers it.

State outcomes as changes, not capabilities — "reduce onboarding time", not "onboarding
API". If a claim will not survive being written that way, that is the finding.

## Validating

```
pip install jsonschema pyyaml
python3 validate.py benefits-example-1.yml
```

## Support

Questions, corrections, and requests go in
[the issues](https://github.com/api-commons/benefits/issues).

## License

Two licenses, by kind of thing:

- **Artifacts** — the schemas, rulesets, fixtures, examples and API descriptions — are
  **[CC BY-NC-SA 4.0](LICENSE)** (Attribution–NonCommercial–ShareAlike).
- **Code** — the validator, test harness and packaging — is **[Apache-2.0](LICENSE-CODE)**.

API Commons licenses **artifacts** under CC BY-NC-SA 4.0 and **code** under Apache-2.0.

## Part of API Commons

A machine-readable building block from **[API Commons](https://apicommons.org)** — open specifications and schemas for the APIs you produce and consume. See all building blocks at **[apicommons.org](https://apicommons.org)** and the tools at **[apicommons.org/tools](https://apicommons.org/tools/)**.

**Related building blocks**
- [plans](https://github.com/api-commons/plans) — access plans, tiers, and pricing
- [rate-limits](https://github.com/api-commons/rate-limits) — the quotas an API enforces
- [starters](https://github.com/api-commons/starters) — the smallest correct version of each artifact
