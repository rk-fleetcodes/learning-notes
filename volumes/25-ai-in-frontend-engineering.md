# AI in Frontend Engineering

This volume was added for Staff+ frontend engineering depth. It focuses on runtime behavior, production failure modes, architecture decisions, and interview-grade reasoning.

## AI-assisted UX

### What Is It?
AI-assisted UX is a concrete engineering discipline inside AI in Frontend Engineering; treat it as a production system with ownership, failure modes, observability, and user impact.

### Why Does It Exist?
It exists because large frontend applications need predictable delivery across teams, devices, networks, security boundaries, and deployment environments.

### Internal Working
At runtime, the important question is: where does work execute, when is data available, what cache owns it, what can fail, and what user-visible state appears while the system recovers.

### Runtime Flow
```mermaid
sequenceDiagram
participant U as User
participant UI as Frontend UI
participant R as Runtime/Framework
participant API as API or Platform
participant O as Observability
U->>UI: interaction/navigation
UI->>R: schedule/render/load work
R->>API: fetch, stream, import, or mutate
API-->>R: response/error/partial data
R-->>UI: commit visible state
UI->>O: metric, trace, error, breadcrumb
```

### Real Production Example
A production SaaS dashboard uses AI-assisted UX when a user changes tenant, navigates to a lazily loaded route, fetches permission-scoped data, handles a partial outage, and still emits enough telemetry for on-call engineers to diagnose the issue.

### Source Code Analysis
```ts
type ProductionBoundary = {
  owner: string;
  input: 'navigation' | 'user-event' | 'server-data' | 'build-artifact';
  failure: 'timeout' | 'version-mismatch' | 'unauthorized' | 'render-error';
  metric: 'INP' | 'LCP' | 'error-rate' | 'cache-hit-rate';
};
```

### Common Bugs
- Hidden coupling between teams or packages.
- Missing fallback UI for slow or failed work.
- Cache invalidation that ignores tenant, locale, role, or feature flag.
- No trace connecting frontend symptom to backend or build artifact.

### Debugging Strategies
Use a reproduction URL, user/session metadata, release SHA, network waterfall, React Profiler commit, browser performance trace, and logs/traces tied by correlation ID.

### Performance Considerations
Measure JavaScript cost, network waterfalls, cache hit rate, hydration or route transition time, memory growth, and long tasks. Do not optimize abstractions before measuring user-visible latency.

### Security and Accessibility Considerations
Security: isolate trust boundaries, validate server decisions, avoid leaking tenant or user data, and fail closed. Accessibility: preserve focus, announce async state changes, keep keyboard paths working, and avoid UI that only communicates through color or motion.

### Interview Questions
#### Beginner
1. What problem does AI-assisted UX solve?
2. What is the user-visible failure state?
3. What browser or React tool would you use first?

#### Intermediate
1. How would you design ownership boundaries for AI-assisted UX?
2. How would caching, retries, and rollback work?
3. Which metric proves the design works?

#### Advanced
1. How would AI-assisted UX behave during partial outage, deploy rollback, or version skew?
2. How would you make it observable across micro-frontends or server-rendered routes?
3. What trade-off would you document in an ADR?

### Mini Project
Build a production-grade demo with route-level error boundaries, loading states, telemetry events, keyboard support, and a README explaining failure recovery.

### Cheat Sheet
- Define owner.
- Define runtime boundary.
- Define cache and invalidation.
- Define fallback UI.
- Define metrics and alerts.
- Define security and accessibility checks.

### Related Concepts
React rendering, browser event loop, caching, system design, observability, security, accessibility, deployment strategy.

## LLM Streaming UI

### What Is It?
LLM Streaming UI is a concrete engineering discipline inside AI in Frontend Engineering; treat it as a production system with ownership, failure modes, observability, and user impact.

### Why Does It Exist?
It exists because large frontend applications need predictable delivery across teams, devices, networks, security boundaries, and deployment environments.

### Internal Working
At runtime, the important question is: where does work execute, when is data available, what cache owns it, what can fail, and what user-visible state appears while the system recovers.

### Runtime Flow
```mermaid
sequenceDiagram
participant U as User
participant UI as Frontend UI
participant R as Runtime/Framework
participant API as API or Platform
participant O as Observability
U->>UI: interaction/navigation
UI->>R: schedule/render/load work
R->>API: fetch, stream, import, or mutate
API-->>R: response/error/partial data
R-->>UI: commit visible state
UI->>O: metric, trace, error, breadcrumb
```

### Real Production Example
A production SaaS dashboard uses LLM Streaming UI when a user changes tenant, navigates to a lazily loaded route, fetches permission-scoped data, handles a partial outage, and still emits enough telemetry for on-call engineers to diagnose the issue.

### Source Code Analysis
```ts
type ProductionBoundary = {
  owner: string;
  input: 'navigation' | 'user-event' | 'server-data' | 'build-artifact';
  failure: 'timeout' | 'version-mismatch' | 'unauthorized' | 'render-error';
  metric: 'INP' | 'LCP' | 'error-rate' | 'cache-hit-rate';
};
```

### Common Bugs
- Hidden coupling between teams or packages.
- Missing fallback UI for slow or failed work.
- Cache invalidation that ignores tenant, locale, role, or feature flag.
- No trace connecting frontend symptom to backend or build artifact.

### Debugging Strategies
Use a reproduction URL, user/session metadata, release SHA, network waterfall, React Profiler commit, browser performance trace, and logs/traces tied by correlation ID.

### Performance Considerations
Measure JavaScript cost, network waterfalls, cache hit rate, hydration or route transition time, memory growth, and long tasks. Do not optimize abstractions before measuring user-visible latency.

### Security and Accessibility Considerations
Security: isolate trust boundaries, validate server decisions, avoid leaking tenant or user data, and fail closed. Accessibility: preserve focus, announce async state changes, keep keyboard paths working, and avoid UI that only communicates through color or motion.

### Interview Questions
#### Beginner
1. What problem does LLM Streaming UI solve?
2. What is the user-visible failure state?
3. What browser or React tool would you use first?

#### Intermediate
1. How would you design ownership boundaries for LLM Streaming UI?
2. How would caching, retries, and rollback work?
3. Which metric proves the design works?

#### Advanced
1. How would LLM Streaming UI behave during partial outage, deploy rollback, or version skew?
2. How would you make it observable across micro-frontends or server-rendered routes?
3. What trade-off would you document in an ADR?

### Mini Project
Build a production-grade demo with route-level error boundaries, loading states, telemetry events, keyboard support, and a README explaining failure recovery.

### Cheat Sheet
- Define owner.
- Define runtime boundary.
- Define cache and invalidation.
- Define fallback UI.
- Define metrics and alerts.
- Define security and accessibility checks.

### Related Concepts
React rendering, browser event loop, caching, system design, observability, security, accessibility, deployment strategy.

## Prompt Injection Defense

### What Is It?
Prompt Injection Defense is a concrete engineering discipline inside AI in Frontend Engineering; treat it as a production system with ownership, failure modes, observability, and user impact.

### Why Does It Exist?
It exists because large frontend applications need predictable delivery across teams, devices, networks, security boundaries, and deployment environments.

### Internal Working
At runtime, the important question is: where does work execute, when is data available, what cache owns it, what can fail, and what user-visible state appears while the system recovers.

### Runtime Flow
```mermaid
sequenceDiagram
participant U as User
participant UI as Frontend UI
participant R as Runtime/Framework
participant API as API or Platform
participant O as Observability
U->>UI: interaction/navigation
UI->>R: schedule/render/load work
R->>API: fetch, stream, import, or mutate
API-->>R: response/error/partial data
R-->>UI: commit visible state
UI->>O: metric, trace, error, breadcrumb
```

### Real Production Example
A production SaaS dashboard uses Prompt Injection Defense when a user changes tenant, navigates to a lazily loaded route, fetches permission-scoped data, handles a partial outage, and still emits enough telemetry for on-call engineers to diagnose the issue.

### Source Code Analysis
```ts
type ProductionBoundary = {
  owner: string;
  input: 'navigation' | 'user-event' | 'server-data' | 'build-artifact';
  failure: 'timeout' | 'version-mismatch' | 'unauthorized' | 'render-error';
  metric: 'INP' | 'LCP' | 'error-rate' | 'cache-hit-rate';
};
```

### Common Bugs
- Hidden coupling between teams or packages.
- Missing fallback UI for slow or failed work.
- Cache invalidation that ignores tenant, locale, role, or feature flag.
- No trace connecting frontend symptom to backend or build artifact.

### Debugging Strategies
Use a reproduction URL, user/session metadata, release SHA, network waterfall, React Profiler commit, browser performance trace, and logs/traces tied by correlation ID.

### Performance Considerations
Measure JavaScript cost, network waterfalls, cache hit rate, hydration or route transition time, memory growth, and long tasks. Do not optimize abstractions before measuring user-visible latency.

### Security and Accessibility Considerations
Security: isolate trust boundaries, validate server decisions, avoid leaking tenant or user data, and fail closed. Accessibility: preserve focus, announce async state changes, keep keyboard paths working, and avoid UI that only communicates through color or motion.

### Interview Questions
#### Beginner
1. What problem does Prompt Injection Defense solve?
2. What is the user-visible failure state?
3. What browser or React tool would you use first?

#### Intermediate
1. How would you design ownership boundaries for Prompt Injection Defense?
2. How would caching, retries, and rollback work?
3. Which metric proves the design works?

#### Advanced
1. How would Prompt Injection Defense behave during partial outage, deploy rollback, or version skew?
2. How would you make it observable across micro-frontends or server-rendered routes?
3. What trade-off would you document in an ADR?

### Mini Project
Build a production-grade demo with route-level error boundaries, loading states, telemetry events, keyboard support, and a README explaining failure recovery.

### Cheat Sheet
- Define owner.
- Define runtime boundary.
- Define cache and invalidation.
- Define fallback UI.
- Define metrics and alerts.
- Define security and accessibility checks.

### Related Concepts
React rendering, browser event loop, caching, system design, observability, security, accessibility, deployment strategy.

## Evaluation Harnesses

### What Is It?
Evaluation Harnesses is a concrete engineering discipline inside AI in Frontend Engineering; treat it as a production system with ownership, failure modes, observability, and user impact.

### Why Does It Exist?
It exists because large frontend applications need predictable delivery across teams, devices, networks, security boundaries, and deployment environments.

### Internal Working
At runtime, the important question is: where does work execute, when is data available, what cache owns it, what can fail, and what user-visible state appears while the system recovers.

### Runtime Flow
```mermaid
sequenceDiagram
participant U as User
participant UI as Frontend UI
participant R as Runtime/Framework
participant API as API or Platform
participant O as Observability
U->>UI: interaction/navigation
UI->>R: schedule/render/load work
R->>API: fetch, stream, import, or mutate
API-->>R: response/error/partial data
R-->>UI: commit visible state
UI->>O: metric, trace, error, breadcrumb
```

### Real Production Example
A production SaaS dashboard uses Evaluation Harnesses when a user changes tenant, navigates to a lazily loaded route, fetches permission-scoped data, handles a partial outage, and still emits enough telemetry for on-call engineers to diagnose the issue.

### Source Code Analysis
```ts
type ProductionBoundary = {
  owner: string;
  input: 'navigation' | 'user-event' | 'server-data' | 'build-artifact';
  failure: 'timeout' | 'version-mismatch' | 'unauthorized' | 'render-error';
  metric: 'INP' | 'LCP' | 'error-rate' | 'cache-hit-rate';
};
```

### Common Bugs
- Hidden coupling between teams or packages.
- Missing fallback UI for slow or failed work.
- Cache invalidation that ignores tenant, locale, role, or feature flag.
- No trace connecting frontend symptom to backend or build artifact.

### Debugging Strategies
Use a reproduction URL, user/session metadata, release SHA, network waterfall, React Profiler commit, browser performance trace, and logs/traces tied by correlation ID.

### Performance Considerations
Measure JavaScript cost, network waterfalls, cache hit rate, hydration or route transition time, memory growth, and long tasks. Do not optimize abstractions before measuring user-visible latency.

### Security and Accessibility Considerations
Security: isolate trust boundaries, validate server decisions, avoid leaking tenant or user data, and fail closed. Accessibility: preserve focus, announce async state changes, keep keyboard paths working, and avoid UI that only communicates through color or motion.

### Interview Questions
#### Beginner
1. What problem does Evaluation Harnesses solve?
2. What is the user-visible failure state?
3. What browser or React tool would you use first?

#### Intermediate
1. How would you design ownership boundaries for Evaluation Harnesses?
2. How would caching, retries, and rollback work?
3. Which metric proves the design works?

#### Advanced
1. How would Evaluation Harnesses behave during partial outage, deploy rollback, or version skew?
2. How would you make it observable across micro-frontends or server-rendered routes?
3. What trade-off would you document in an ADR?

### Mini Project
Build a production-grade demo with route-level error boundaries, loading states, telemetry events, keyboard support, and a README explaining failure recovery.

### Cheat Sheet
- Define owner.
- Define runtime boundary.
- Define cache and invalidation.
- Define fallback UI.
- Define metrics and alerts.
- Define security and accessibility checks.

### Related Concepts
React rendering, browser event loop, caching, system design, observability, security, accessibility, deployment strategy.

## Human-in-the-loop Review

### What Is It?
Human-in-the-loop Review is a concrete engineering discipline inside AI in Frontend Engineering; treat it as a production system with ownership, failure modes, observability, and user impact.

### Why Does It Exist?
It exists because large frontend applications need predictable delivery across teams, devices, networks, security boundaries, and deployment environments.

### Internal Working
At runtime, the important question is: where does work execute, when is data available, what cache owns it, what can fail, and what user-visible state appears while the system recovers.

### Runtime Flow
```mermaid
sequenceDiagram
participant U as User
participant UI as Frontend UI
participant R as Runtime/Framework
participant API as API or Platform
participant O as Observability
U->>UI: interaction/navigation
UI->>R: schedule/render/load work
R->>API: fetch, stream, import, or mutate
API-->>R: response/error/partial data
R-->>UI: commit visible state
UI->>O: metric, trace, error, breadcrumb
```

### Real Production Example
A production SaaS dashboard uses Human-in-the-loop Review when a user changes tenant, navigates to a lazily loaded route, fetches permission-scoped data, handles a partial outage, and still emits enough telemetry for on-call engineers to diagnose the issue.

### Source Code Analysis
```ts
type ProductionBoundary = {
  owner: string;
  input: 'navigation' | 'user-event' | 'server-data' | 'build-artifact';
  failure: 'timeout' | 'version-mismatch' | 'unauthorized' | 'render-error';
  metric: 'INP' | 'LCP' | 'error-rate' | 'cache-hit-rate';
};
```

### Common Bugs
- Hidden coupling between teams or packages.
- Missing fallback UI for slow or failed work.
- Cache invalidation that ignores tenant, locale, role, or feature flag.
- No trace connecting frontend symptom to backend or build artifact.

### Debugging Strategies
Use a reproduction URL, user/session metadata, release SHA, network waterfall, React Profiler commit, browser performance trace, and logs/traces tied by correlation ID.

### Performance Considerations
Measure JavaScript cost, network waterfalls, cache hit rate, hydration or route transition time, memory growth, and long tasks. Do not optimize abstractions before measuring user-visible latency.

### Security and Accessibility Considerations
Security: isolate trust boundaries, validate server decisions, avoid leaking tenant or user data, and fail closed. Accessibility: preserve focus, announce async state changes, keep keyboard paths working, and avoid UI that only communicates through color or motion.

### Interview Questions
#### Beginner
1. What problem does Human-in-the-loop Review solve?
2. What is the user-visible failure state?
3. What browser or React tool would you use first?

#### Intermediate
1. How would you design ownership boundaries for Human-in-the-loop Review?
2. How would caching, retries, and rollback work?
3. Which metric proves the design works?

#### Advanced
1. How would Human-in-the-loop Review behave during partial outage, deploy rollback, or version skew?
2. How would you make it observable across micro-frontends or server-rendered routes?
3. What trade-off would you document in an ADR?

### Mini Project
Build a production-grade demo with route-level error boundaries, loading states, telemetry events, keyboard support, and a README explaining failure recovery.

### Cheat Sheet
- Define owner.
- Define runtime boundary.
- Define cache and invalidation.
- Define fallback UI.
- Define metrics and alerts.
- Define security and accessibility checks.

### Related Concepts
React rendering, browser event loop, caching, system design, observability, security, accessibility, deployment strategy.

## AI Developer Tooling

### What Is It?
AI Developer Tooling is a concrete engineering discipline inside AI in Frontend Engineering; treat it as a production system with ownership, failure modes, observability, and user impact.

### Why Does It Exist?
It exists because large frontend applications need predictable delivery across teams, devices, networks, security boundaries, and deployment environments.

### Internal Working
At runtime, the important question is: where does work execute, when is data available, what cache owns it, what can fail, and what user-visible state appears while the system recovers.

### Runtime Flow
```mermaid
sequenceDiagram
participant U as User
participant UI as Frontend UI
participant R as Runtime/Framework
participant API as API or Platform
participant O as Observability
U->>UI: interaction/navigation
UI->>R: schedule/render/load work
R->>API: fetch, stream, import, or mutate
API-->>R: response/error/partial data
R-->>UI: commit visible state
UI->>O: metric, trace, error, breadcrumb
```

### Real Production Example
A production SaaS dashboard uses AI Developer Tooling when a user changes tenant, navigates to a lazily loaded route, fetches permission-scoped data, handles a partial outage, and still emits enough telemetry for on-call engineers to diagnose the issue.

### Source Code Analysis
```ts
type ProductionBoundary = {
  owner: string;
  input: 'navigation' | 'user-event' | 'server-data' | 'build-artifact';
  failure: 'timeout' | 'version-mismatch' | 'unauthorized' | 'render-error';
  metric: 'INP' | 'LCP' | 'error-rate' | 'cache-hit-rate';
};
```

### Common Bugs
- Hidden coupling between teams or packages.
- Missing fallback UI for slow or failed work.
- Cache invalidation that ignores tenant, locale, role, or feature flag.
- No trace connecting frontend symptom to backend or build artifact.

### Debugging Strategies
Use a reproduction URL, user/session metadata, release SHA, network waterfall, React Profiler commit, browser performance trace, and logs/traces tied by correlation ID.

### Performance Considerations
Measure JavaScript cost, network waterfalls, cache hit rate, hydration or route transition time, memory growth, and long tasks. Do not optimize abstractions before measuring user-visible latency.

### Security and Accessibility Considerations
Security: isolate trust boundaries, validate server decisions, avoid leaking tenant or user data, and fail closed. Accessibility: preserve focus, announce async state changes, keep keyboard paths working, and avoid UI that only communicates through color or motion.

### Interview Questions
#### Beginner
1. What problem does AI Developer Tooling solve?
2. What is the user-visible failure state?
3. What browser or React tool would you use first?

#### Intermediate
1. How would you design ownership boundaries for AI Developer Tooling?
2. How would caching, retries, and rollback work?
3. Which metric proves the design works?

#### Advanced
1. How would AI Developer Tooling behave during partial outage, deploy rollback, or version skew?
2. How would you make it observable across micro-frontends or server-rendered routes?
3. What trade-off would you document in an ADR?

### Mini Project
Build a production-grade demo with route-level error boundaries, loading states, telemetry events, keyboard support, and a README explaining failure recovery.

### Cheat Sheet
- Define owner.
- Define runtime boundary.
- Define cache and invalidation.
- Define fallback UI.
- Define metrics and alerts.
- Define security and accessibility checks.

### Related Concepts
React rendering, browser event loop, caching, system design, observability, security, accessibility, deployment strategy.

