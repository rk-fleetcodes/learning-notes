# State Management

This volume contains domain-specific senior-level notes for: Context API, Redux, Zustand, React Query.

```mermaid
graph TD
A[User Event/Data Change] --> B[State Update]
B --> C[Render Phase]
C --> D[Reconciliation/Fiber]
D --> E[Commit DOM]
E --> F[Effects + Analytics]
```

## Context API

### What it is
Context API passes values through a React subtree without prop drilling; it is not a general-purpose high-frequency state store.

### Why it exists
It removes prop drilling for low-frequency cross-cutting values such as theme, locale, session, and feature flags.

### Source-code / internal model
A Provider stores a value; consumers subscribe to the nearest provider; when provider value identity changes, consumers can re-render.

### Architecture diagram

```mermaid
graph TD
A[User Event/Data Change] --> B[State Update]
B --> C[Render Phase]
C --> D[Reconciliation/Fiber]
D --> E[Commit DOM]
E --> F[Effects + Analytics]
```

### Production React example
Theme, locale, auth session, feature flags, and design tokens are good Context use cases.

```tsx
const ContextAPIExample = {
  input: "dashboard filter, route transition, or API response",
  failureMode: "stale state, remount, blocked input, or unsafe data sink",
  metric: "React Profiler commit time, Chrome long task, heap growth, or Web Vital",
};
```

### Debugging scenario
If every page re-renders after typing, inspect a broad Context provider whose value object changes on every render.

### Performance profiling example
Use React Profiler and split contexts by update frequency: auth context separate from theme and permissions.

### Product-company interview prompts
- Interviews ask: Context vs Redux, provider value memoization, and context update blast radius.
- Explain one production incident involving Context API and how you would prevent recurrence.
- Implement or design a minimal example of Context API while narrating correctness, edge cases, and trade-offs.

### Senior-engineer checklist
- What owns the data or behavior?
- What can make it stale, slow, inaccessible, insecure, or hard to test?
- What instrumentation proves it works in production?
- What API would you expose to a team so misuse is difficult?

## Redux

### What it is
Redux centralizes client state transitions with actions and pure reducers.

### Why it exists
It makes complex client-state transitions inspectable, replayable, and testable across large teams.

### Source-code / internal model
Dispatch creates an action, reducers compute next immutable state, subscribers are notified, and selectors derive view data.

### Architecture diagram

```mermaid
graph TD
A[User Event/Data Change] --> B[State Update]
B --> C[Render Phase]
C --> D[Reconciliation/Fiber]
D --> E[Commit DOM]
E --> F[Effects + Analytics]
```

### Production React example
Large ecommerce apps use Redux for cart, checkout flow, permissions, and undoable UI workflows.

```tsx
const ReduxExample = {
  input: "dashboard filter, route transition, or API response",
  failureMode: "stale state, remount, blocked input, or unsafe data sink",
  metric: "React Profiler commit time, Chrome long task, heap growth, or Web Vital",
};
```

### Debugging scenario
A stale UI often means selectors mutate data or reducers return the same object after changing nested fields.

### Performance profiling example
Use Redux DevTools action trace and selector memoization metrics to find over-rendering.

### Product-company interview prompts
- Companies ask: why reducers must be pure, middleware flow, and Redux Toolkit benefits.
- Explain one production incident involving Redux and how you would prevent recurrence.
- Implement or design a minimal example of Redux while narrating correctness, edge cases, and trade-offs.

### Senior-engineer checklist
- What owns the data or behavior?
- What can make it stale, slow, inaccessible, insecure, or hard to test?
- What instrumentation proves it works in production?
- What API would you expose to a team so misuse is difficult?

## Zustand

### What it is
Zustand is a small external store library using hooks and selector subscriptions.

### Why it exists
It provides granular external-store subscriptions without the ceremony of reducers/actions for every UI state change.

### Source-code / internal model
The store lives outside React; components subscribe to selected slices and re-render when equality checks detect changes.

### Architecture diagram

```mermaid
graph TD
A[User Event/Data Change] --> B[State Update]
B --> C[Render Phase]
C --> D[Reconciliation/Fiber]
D --> E[Commit DOM]
E --> F[Effects + Analytics]
```

### Production React example
Collaborative editors use Zustand for local UI state such as panels, selected nodes, and transient tool modes.

```tsx
const ZustandExample = {
  input: "dashboard filter, route transition, or API response",
  failureMode: "stale state, remount, blocked input, or unsafe data sink",
  metric: "React Profiler commit time, Chrome long task, heap growth, or Web Vital",
};
```

### Debugging scenario
If components re-render too often, check selectors returning new objects without shallow comparison.

### Performance profiling example
Profile selector churn and compare component renders before/after granular subscriptions.

### Product-company interview prompts
- Interviews ask: external store vs Context and how useSyncExternalStore avoids tearing.
- Explain one production incident involving Zustand and how you would prevent recurrence.
- Implement or design a minimal example of Zustand while narrating correctness, edge cases, and trade-offs.

### Senior-engineer checklist
- What owns the data or behavior?
- What can make it stale, slow, inaccessible, insecure, or hard to test?
- What instrumentation proves it works in production?
- What API would you expose to a team so misuse is difficult?

## React Query

### What it is
React Query manages server state: cache, fetch lifecycle, retries, invalidation, background refetch, and stale data.

### Why it exists
It separates server-state concerns from client UI state: freshness, caching, retries, invalidation, and background refetch.

### Source-code / internal model
Query keys index cache records; observers subscribe components; staleTime/cacheTime control freshness and garbage collection.

### Architecture diagram

```mermaid
graph TD
A[User Event/Data Change] --> B[State Update]
B --> C[Render Phase]
C --> D[Reconciliation/Fiber]
D --> E[Commit DOM]
E --> F[Effects + Analytics]
```

### Production React example
Admin apps use it for user lists, optimistic mutations, pagination, and refetch-on-focus.

```tsx
const ReactQueryExample = {
  input: "dashboard filter, route transition, or API response",
  failureMode: "stale state, remount, blocked input, or unsafe data sink",
  metric: "React Profiler commit time, Chrome long task, heap growth, or Web Vital",
};
```

### Debugging scenario
Duplicate requests usually mean unstable query keys or query functions created with missing parameters.

### Performance profiling example
Use React Query Devtools to inspect cache status, stale state, observers, and retries.

### Product-company interview prompts
- Interviews ask: server state vs client state, invalidation strategy, optimistic update rollback.
- Explain one production incident involving React Query and how you would prevent recurrence.
- Implement or design a minimal example of React Query while narrating correctness, edge cases, and trade-offs.

### Senior-engineer checklist
- What owns the data or behavior?
- What can make it stale, slow, inaccessible, insecure, or hard to test?
- What instrumentation proves it works in production?
- What API would you expose to a team so misuse is difficult?

