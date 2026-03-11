# Public Integration Notes

This document describes the public-facing integration model for Vartovii at a
high level.

It is intentionally representative rather than exhaustive. The private execution
layer, internal pipelines, and protected orchestration logic are not exposed
here.

## Delivery Modes

Vartovii outputs can be consumed through three public-facing modes:

- web application workflows
- source-attributed research reports
- API-ready trust decisions for partner integrations

## Representative Trust Decision Shape

```json
{
  "entity_type": "token",
  "entity_id": "example-protocol",
  "status": "reviewed",
  "trust_score": 74,
  "risk_level": "moderate",
  "decision": "allow_with_review",
  "summary": "Mixed operational and market signals. No single blocker detected, but elevated treasury concentration and weak documentation hygiene warrant review.",
  "breakdown": {
    "security": 81,
    "market_integrity": 68,
    "treasury_behavior": 64,
    "developer_activity": 72,
    "community_signals": 79
  },
  "evidence": [
    {
      "source": "github",
      "signal": "recent_repository_activity",
      "confidence": "medium"
    },
    {
      "source": "market_data",
      "signal": "liquidity_concentration",
      "confidence": "high"
    },
    {
      "source": "public_reputation",
      "signal": "community_sentiment_shift",
      "confidence": "medium"
    }
  ],
  "generated_at": "2026-03-09T12:00:00Z"
}
```

## Consumption Pattern

Typical partner flow:

1. Submit or select an entity for review.
2. Receive a structured trust output with score, decision, and evidence.
3. Use the response in analyst workflows, monitoring, or downstream automation.

## Design Principles

- deterministic, structured outputs instead of narrative-only summaries
- explicit evidence attribution
- clear separation between public integration surfaces and private execution
  infrastructure

## Notes

- Scores reflect available data and configured methodology at evaluation time.
- Outputs support decision workflows but do not replace legal, compliance,
  investment, or employment review.
