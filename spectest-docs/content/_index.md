---
description: "Lightning fast and declarative API testing"
toc: false
---

{{< hero title="API testing without the pain" tagline="Write tests as fast as you think. Spectest transforms API testing from a chore into a superpower with declarative syntax and lightning-fast execution." image="https://raw.githubusercontent.com/justiceo/spectest/refs/heads/main/assets/spectest-logo-transparent.png" cta_text="Get Started" cta_url="/docs/introduction/getting-started/" />}}

## Why Developers Choose Spectest

{{< cards >}}
{{< card title="Ridiculously Fast" icon="lightning-bolt" subtitle="Execute hundreds of tests in seconds with parallel execution and smart caching." >}}
{{< card title="Truly Declarative" icon="document-text" subtitle="Write tests in plain JSON/YAML. No boilerplate, just describe what you expect." >}}
{{< card title="Focused Workflow" icon="cursor-click" subtitle="Built for API testing. Smart defaults and intuitive syntax keep you focused." >}}
{{< card title="CI/CD Native" icon="code" subtitle="Snapshot testing, environment variables, and detailed reporting for seamless integration." >}}
{{< card title="Framework Agnostic" icon="puzzle" subtitle="Works with Jest, Vitest, or standalone. Fits into any existing test suite." >}}
{{< card title="Visual Clarity" icon="eye" subtitle="Clear output with diff views and smart error messages saves debugging time." >}}
{{< /cards >}}

## See It In Action

Here's how simple API testing becomes with Spectest:

### Before: Traditional API Testing
```javascript
describe('User API', () => {
  it('should create user and return 201', async () => {
    const response = await fetch('/api/users', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ name: 'John', email: 'john@example.com' })
    });
    
    expect(response.status).toBe(201);
    const user = await response.json();
    expect(user).toHaveProperty('id');
    expect(user.name).toBe('John');
    expect(user.email).toBe('john@example.com');
  });
});
```

### After: Spectest Declarative Testing
```yaml
name: "Create User"
endpoint: "/api/users"
method: POST
body:
  name: "John"
  email: "john@example.com"
expect:
  status: 201
  body:
    id: "@type:number"
    name: "John"
    email: "john@example.com"
```

{{< hint type="tip" >}}
**That's it!** No setup, no boilerplate, no ceremony. Just describe what you want to test and Spectest handles the execution, validation, and reporting.
{{< /hint >}}

## Quick Start Guide

{{< cards >}}
{{< card title="1. Install" icon="download" subtitle="Get up and running in seconds with our CLI tool" >}}
{{< card title="2. Create Test Suite" icon="document-add" subtitle="Write your first test in simple YAML format" >}}
{{< card title="3. Run Tests" icon="play" subtitle="Watch your tests execute with beautiful, detailed output" >}}
{{< /cards >}}

### Install Spectest
```bash
npm install -g spectest
```

### Create Your First Test
```yaml
# api-tests.yaml
baseURL: "https://api.example.com"
tests:
  - name: "Health Check"
    endpoint: "/health"
    expect:
      status: 200
```

### Run Your Tests
```bash
spectest run api-tests.yaml
```

## Powerful Features for Every Use Case

### Smart Test Dependencies
```yaml
tests:
  - name: "Login"
    operationId: "auth"
    endpoint: "/auth/login"
    body:
      username: "admin"
      password: "secret"
    
  - name: "Get Profile"
    dependsOn: ["auth"]
    endpoint: "/user/profile"
    headers:
      Authorization: "Bearer {{auth.response.token}}"
```

### Environment Variables & Configuration
```javascript
// spectest.config.js
module.exports = {
  baseURL: process.env.API_URL || 'http://localhost:3000',
  timeout: 5000,
  retries: 2,
  parallel: true
};
```

### Snapshot Testing for Regression Prevention
```bash
# Capture current API responses
spectest run --snapshot

# Later, detect any changes
spectest run --check-snapshots
```

## Integration That Just Works

### With Jest
```javascript
import { runSpectest } from 'spectest';

describe('API Integration', () => {
  it('should pass all API tests', async () => {
    const results = await runSpectest('api-tests.yaml');
    expect(results.failed).toBe(0);
  });
});
```

### With Vitest
```javascript
import { describe, it, expect } from 'vitest';
import { runSpectest } from 'spectest';

describe('API Tests', () => {
  it('validates all endpoints', async () => {
    const results = await runSpectest('./tests/*.spec.yaml');
    expect(results.passed).toBeGreaterThan(0);
  });
});
```

## Ready to Transform Your API Testing?

{{< cards >}}
{{< card title="Read the Docs" icon="book-open" link="/docs/introduction/" subtitle="Comprehensive guides, examples, and API references to get you up to speed quickly" >}}
{{< card title="View on GitHub" icon="github" link="https://github.com/justiceo/spectest" subtitle="Explore the source code, contribute, or report issues. We ❤️ community feedback!" >}}
{{< card title="Get Support" icon="chat" link="/docs/more/about/" subtitle="Join our community or reach out for help. We're here to make your testing experience amazing" >}}
{{< /cards >}}

---

{{< hint type="info" >}}
**Open Source & MIT Licensed** • Spectest is free, open-source software released under the MIT license. Use it anywhere, modify it as needed, and contribute back to help make API testing better for everyone.
{{< /hint >}}