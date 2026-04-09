# Runtime Configuration

## Why runtime configuration matters

The platform is not structured as a fixed demo application.

It contains runtime-adjustable layers that allow planning behavior, packaging constraints, notification memory, and assistant context to evolve without rewriting the core engine.

## Notification and Runtime Control Examples

![Instant Notifications](<assets/screenshots/instant notifications.png>)

![Overtime Suggestions](<assets/screenshots/overtime suggestions.png>)

## Embedded rule settings

The GUI persists embedded rule settings through an internal store rather than relying only on hardcoded defaults.

From the current implementation, these include controls such as:

- strict missing-data behavior
- capacity-fallback behavior
- production-side default material stock handling
- packaging-side priority fallback behavior

## Notification memory

The application maintains a notification history with metadata such as:

- severity / level
- title and message
- source
- status
- recorded decision
- decision note
- timestamps
- repeat count
- action options

This allows notifications to become part of the assistant context instead of being treated as disposable UI alerts.

## Weekly note synchronization

The runtime layer also supports a weekly-notes style memory model.
This can be used to carry contextual notes into the assistant and into planning-related workflows.

## Packaging chatbot controls

The application maintains packaging-control state that can be synchronized into the assistant layer.
This is part of what enables natural-language packaging authority interactions.

## MRP mode switching

Both production-side and packaging-side MRP modes are exposed as runtime choices.

The current implementation supports at least two conceptual behaviors:

- enforce constraint
- report-only behavior

This allows the same engine to behave differently depending on whether material reality should hard-block a plan or simply be surfaced for human review.

## Bridge settings and overtime approvals

The production–packaging bridge includes runtime settings for:

- enabling or disabling bridge behavior
- exempting specific lines
- storing overtime approvals
- recording auto-revision requests

This is important because packaging overload does not always lead to the same operational response.
The runtime layer can represent whether extra hours were approved or whether upstream production should instead be revised.

## Workforce profile

The GUI also contains packaging workforce configuration behavior with concepts such as:

- staff required by line
- line priority order
- daily available staff
- configured vs manual-confirmed state

This supports more realistic packaging planning than a fixed-capacity abstraction.

## Why it matters

A configurable runtime layer is one of the reasons the system can adapt to real operational use.
It allows the platform to carry operational memory, planning policies, and control preferences without changing the core code path for every scenario.
