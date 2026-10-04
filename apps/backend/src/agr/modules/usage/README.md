# Usage and business receipts

Status: ownership and separation selected; commercial tariff proposed/open.

## Responsibility

Record provider usage/cost attribution and application business charge receipts. These are different concepts. This module is not an invoice, payment collection or tax system.

## Decisions

- Identify usage by customer, actor, operation/run and provider/model, with explicit known/unknown measurements.
- Preserve an unknown token count as unknown; do not manufacture zero consumption.
- A model call may incur cost even if the workflow later fails or the user discards a proposal.
- Business charging follows an explicit versioned product rule, not provider token counts.
- A charge identity prevents duplicated business charges when a save is retried.
- Where saving a document triggers a charge, both participate in one SQL transaction. No charge independently commits before the associated business result.
- Historical tariffs are immutable evidence. A future pricing change does not rewrite past receipts.

## Operations

Record an inference attempt/result; attribute accumulated usage; prepare and commit an applicable business receipt within an existing transaction; return authorized usage summaries; reconcile an operation with uncertain response delivery.

Legacy charges are migration evidence. Do not hard-code the previous tariff as the new product price without an explicit product decision.

## Acceptance cases

Repeated approval yields one business receipt; provider timeout leaves cost uncertainty visible; failed document commit creates no success charge; user-facing summaries cannot expose another scope's document or commercial details.

## Open decisions

Confirm billable events and rates, usage retention, customer quotas and actual invoice/export integration. Quotas that block work need a concurrent enforcement design; budget alerts alone are not spend limits.
