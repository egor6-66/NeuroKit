---
name: preserve-prop-reactivity
description: Read changing Solid props where their current values are needed.
---

Read a changing prop directly in JSX or inside the reactive computation that uses it. Reading props.name into a local variable, including by destructuring props in the component body, captures its value during component setup. Use that pattern only when the initial snapshot is intentional.

```tsx
function AgentHeading(props: { name: string }) {
  return <h2>{props.name}</h2>
}
```

For repeated reads, an accessor such as `const name = () => props.name` retrieves the current value when called. To separate locally consumed props from those forwarded to a child, use Solid's splitProps and read properties from the returned groups.

Check the update path: render the component, change the prop in the parent while the same component stays mounted, and verify that its displayed value updates.

[Solid — Props](https://docs.solidjs.com/concepts/components/props)
