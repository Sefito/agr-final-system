# Runnable applications

Status: three host responsibilities selected; deployment topology proposed.

[api](api/README.md) serves HTTP/SSE. [worker](worker/README.md) executes jobs. [web](web/README.md) presents product flows. Applications compose reusable packages; they do not own copies of business rules.

API and worker can use the same image with different entry points. Worker responsibilities do not imply an additional always-on Azure service; scheduled jobs or a worker process may suffice. They are separate application projects because their lifecycle, entry points, resources and verification differ.

Applications never import one another. Deployment, package and process boundaries are separate choices. See the [monorepo design](../docs/architecture/monorepo.md).
