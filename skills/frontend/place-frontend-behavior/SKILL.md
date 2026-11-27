---
name: place-frontend-behavior
description: Use before implementing or moving a frontend action that touches a page, a UI component, an entity hook, or a client library. Identify the owner of the operation and the decisions each consumer makes.
---

### Before editing

1. Read the project’s architecture rules, the target module’s public API, and its callers. Compare peers that do the same job: detail views with other detail views, public entity hooks with other entity hooks. Check what they accept through props, what they expose, and where they obtain actions. If a nearby handler conflicts with a project rule, identify the file or symbol and the rule before extending the screen.
2. Trace one user action from intent to outcome. Identify who executes it, who supplies its state and errors, and who decides what the user sees afterward. Check the client library for an existing operation before introducing a subscription, request, or wrapper. If its contract is missing a required command, identify the gap at the library boundary.
3. Sketch the public call from two places, such as a detail view and a row menu. A hypothetical second caller is enough; implement only the requested caller. If two owners remain plausible, ask the question that would settle it. For example, “Does every archive operation require confirmation, or does only the detail screen ask for it?” When the user asks why code is placed somewhere, explain the ownership before proposing edits.

### Example: archive a document

The entity API exposes the document’s archive command, availability, pending state, and error. Both callers can invoke the command for their own document. Each caller chooses its label, icon, order, and response to success. For example, these two handlers use the same public operation:

```ts
// Detail screen: return to the list after a successful archive.
const onArchiveFromDetails = async () => {
  await doc.archive()
  returnToList()
}

// Row menu: stay on the list.
const onArchiveFromRow = () => doc.archive()
```

If detail views accept prepared actions, pass the first handler through that existing prop. The detail component renders the action and can manage local interactions such as focus. The page selects the record, composes the screen, and owns navigation. A feature can coordinate several independent operations when the workflow calls for them. In FSD, choose a composition layer that can import all participants through their public APIs.

Check the proposed API from the row menu. It should be able to call the command directly for the selected document. If it must import the detail view, inspect `actions[0]`, search for a button label, or repeat the request, revisit the ownership. A hook that assembles detail-view actions belongs with that consumer. Moving those action descriptors into a general entity hook leaves the coupling in place.
