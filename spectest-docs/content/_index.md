---
title: "Spectest"
description: "Lightning fast and declarative API testing"
---

{{< hero title="API testing without the pain" tagline="Spectest lets you describe HTTP endpoints and verify them in seconds" image="https://raw.githubusercontent.com/justiceo/spectest/refs/heads/main/assets/spectest-logo-transparent.png" cta_text="Get Started" cta_url="/docs/introduction/getting-started/" >}}

## Key Features

{{< cards >}}
{{< card icon="bolt" title="Truly Declarative" >}}
Write tests as plain objects that mirror Fetch Request and Response schemas.
{{< /card >}}
{{< card icon="zap" title="Ridiculously Fast" >}}
Runs requests in parallel with smart rate limiting so suites finish in no time.
{{< /card >}}
{{< card icon="crosshair" title="Focused Workflow" >}}
Filter, tag, randomize and bombard endpoints for robust coverage.
{{< /card >}}
{{< /cards >}}

## Quick Start

{{< button href="/docs/introduction/getting-started/" >}}Read the getting started guide{{< /button >}}

```js
// simple.spectest.js
export default [
  { name: 'Fetch TODO 1', endpoint: '/todos/1' }
]
```

## Explore the docs

{{< cards >}}
{{< card icon="rocket" title="Getting Started" href="/docs/introduction/getting-started/" / >}}
{{< card icon="book" title="Guides" href="/docs/guides/" / >}}
{{< card icon="file-text" title="API Reference" href="/docs/api/" / >}}
{{< card icon="plug" title="Integrations" href="/docs/integrations/" / >}}
{{< /cards >}}
