---
name: keep-type-predicates-exact
description: Make both outcomes of a type predicate match its declared type.
---

Use a predicate of the form value is T only when true establishes membership in T and false rules it out for every supported input. Check whether a valid T could fail an extra condition such as a numeric range check.

```ts
function isPositiveId(id: string | number): boolean {
  return typeof id === 'number' && id > 0
}
```

Zero is a number and fails this check. Declaring the return type as id is number would allow callers to treat zero as a string in the false branch. Return boolean for the combined condition, or narrow with typeof first and check positivity inside the numeric branch.

[TypeScript — Type Predicates](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-5-5.html#inferred-type-predicates)
