# Technical Architecture

## System goal

The platform is designed to produce **more executable** weekly planning outputs by linking production, packaging, MRP, raw-material timing, and process uncertainty in one operational flow.

Rather than treating planning as a single optimization pass, the architecture combines planning, validation, revision, and explanation.

## Main layers

### 1. GUI orchestration layer

The GUI acts as the operational entry point for the system.
It brings together:

- Production Planning
- Packaging Planning
- Fermentation Forecasting
- MRP Control
- Notifications
- AI Assistant

The same interface also manages runtime state such as notification memory, packaging chatbot controls, bridge-revision requests, embedded rule settings, and packaging MRP mode selections.

### 2. Production planning layer

The production side generates the weekly production plan under plant-specific constraints.
This output is not treated as final in isolation.
Instead, it becomes the upstream input for packaging feasibility and bridge-revision logic.

### 3. Packaging MILP layer

The packaging engine evaluates whether production outputs can actually be packed under downstream reality.
This includes:

- line capacity
- line candidates
- line-machine counts
- staffing constraints
- line priority ordering
- two-stage routes
- daily lag rules between process stages
- packaging-material awareness
- backlog and delay penalties

### 4. MRP and material layer

The planning flow incorporates MRP-aware checks and packaging-material mapping.
Depending on runtime mode, material constraints can be enforced directly or surfaced as report-only issues.

The architecture is also sensitive to:

- purchasing due dates
- available raw materials
- inbound / expected materials
- packaging material shortages

### 5. Production–packaging bridge

A core differentiator of the platform is the bridge between production and packaging.

Production is not left as a standalone plan.
Once downstream bottlenecks are detected, the system can:

- generate bridge audit outputs
- propose overtime-based responses
- trigger revision requests
- attempt automatic production shifting when packaging overload is not approved for overtime

This turns the architecture into a decision loop rather than a one-directional planner.

### 6. Natural-language interface layer

The AI Assistant sits on top of runtime planning context.
It is connected to:

- planning outputs
- decision traces
- packaging-control state
- notification records
- weekly notes
- packaging chatbot controls

This allows the system to explain, analyze, and partially steer planning behavior through natural language.

### 7. Uncertainty layer

The Entropic Bayes module is positioned inside the fermentation forecasting workflow.
Its role is to transform process uncertainty into an operational planning signal, especially for fermentation readiness and packaging timing.

## Architectural flow

A simplified flow is:

1. Demand, stock, operational rules, and material data are loaded.
2. A weekly production plan is generated.
3. The weekly production output is exploded into packaging jobs.
4. Packaging feasibility is solved under line, staffing, and route constraints.
5. Packaging-material and MRP issues are checked.
6. If downstream bottlenecks appear, bridge logic can request overtime or trigger revision.
7. Notifications and explainability layers surface the result to users.
8. The AI Assistant makes the system queryable and steerable in natural language.

## Why this matters

Many systems can generate schedules.
Fewer systems can validate downstream feasibility, revise upstream production decisions, and explain their behavior inside the same workflow.

That is the architectural role of this platform.
