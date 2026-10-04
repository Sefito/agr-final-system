# Model-provider adapters

Status: explicit provider boundary selected; models/providers open.

## Responsibility

Transport authorized generation, structured-output and embedding requests. Translate results, usage and provider failures into application-owned contracts. Prompt/evidence policy belongs to the invoking application use case.

## Decisions

- No model/provider is enabled merely because a credential exists or the runtime is hosted in Azure.
- Customer approval specifies provider/deployment, location and data categories. Apply it to prompts, embeddings and managed extraction where relevant.
- Generation and embedding providers are separate choices. Index identity records the embedding model space, not only its dimensions.
- Structured syntax is validated against a closed contract. Syntactically valid output still requires business/evidence validation.
- Bound input/output, timeouts and retries. Capture usage across attempts and keep missing measurements unknown.
- Persist approved business proposals, not raw provider conversation objects as a replacement domain state.
- No live provider calls in ordinary tests. No hosted tracing of customer content is selected.

## Acceptance cases

Provider disabled produces a clear outcome; invalid output cannot trigger a write; retry usage is accounted for; transport failure does not leak a prompt; model migration includes index/relevance compatibility assessment.

## Open decisions

Choose approved providers, exact model deployments, supported capabilities, SDK pins and measured token envelopes. Decide cancellation and uncertain-call treatment. Framework selection does not choose or authorize a model.
