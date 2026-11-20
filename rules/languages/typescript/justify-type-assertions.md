---
name: justify-type-assertions
description: Use a type assertion only when a concrete guarantee supports the asserted type.
---

Before using an assertion such as value as T, identify what guarantees that the runtime value satisfies T. Prefer a check that lets TypeScript narrow the value. An assertion can be appropriate when an external API makes a specific guarantee that its type declaration cannot express. A compiler error alone provides no such guarantee.

```ts
type LaunchMode = 'manual' | 'scheduled'

function readLaunchMode(params: URLSearchParams): LaunchMode | undefined {
  const mode = params.get('mode')
  if (mode === 'manual' || mode === 'scheduled') return mode
  return undefined
}
```

Here the equality checks verify the supported modes. Writing params.get('mode') as LaunchMode would preserve an unsupported string or a missing parameter's null at runtime while promising callers a valid mode.

[TypeScript Handbook — Type Assertions](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#type-assertions)
