# Intelligence internal modules

[retrieval](retrieval/README.md) owns authorized evidence/index behavior; [assistant](assistant/README.md) owns consultation conversations/answers. They collaborate through explicit internal operations, not shared mutable global context.

Cross-package consumers use the public `agr_intelligence` surface. Private search-planner/answer implementation can change without exposing a new frontend or commercial dependency.
