# Streaming event contracts

Status: proposed language-neutral schema authority.

Define event envelope/version, authorized payloads, progress versus business completion, terminal failure/cancellation and compatibility rules. Generate or validate Python/TypeScript types from the same specification when tooling is selected.

An event never authorizes a mutation. Raw prompts, checkpoints, principal objects and provider errors are not public event data. HTTP code generation does not automatically specify streaming semantics.
