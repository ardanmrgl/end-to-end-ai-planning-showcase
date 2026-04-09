# Packaging Engine

## Role in the platform

The packaging engine is the downstream execution filter of the planning stack.

Its job is not only to assign packaging work to lines, but to determine whether the upstream production plan can actually survive line reality, staffing limits, route structure, and material constraints.

## Interface Example

![Packaging Plan](assets/screenshots/packaging%20plan.png)

## Planning model

The packaging layer is built around a MILP-style planning approach with configurable operational parameters.

From the current implementation, the engine evaluates packaging jobs by using information such as:

- line family and candidate lines
- line machine counts
- line daily hours
- staff requirements by line
- daily available staff
- route stage structure
- final-stage vs intermediate-stage operations
- release-day logic and lag rules
- packaging MRP mode
- backlog, split, delay, and WIP penalties

## Examples of encoded operational rules

The implementation includes plant-style rules rather than abstract scheduling only. Examples include:

- Some lines are modeled with a larger daily-hour profile than others.
- Secondary or fallback lines can be discouraged or conditionally restricted unless preferred lines are sufficiently utilized.
- Some process-delay logic is line-sensitive.
- Two-stage flows are explicitly modeled and monitored.
- Waiting time and split behavior can trigger alerts.
- Missing data can be handled in strict mode, preventing synthetic fallback behavior.

## Material and MRP awareness

The packaging engine is not blind to material reality.

It can work with packaging-material maps and material-issue outputs to support:

- packaging-material usage checks
- material shortage reporting
- enforced or report-only packaging MRP modes
- issue sheets and summary exports for downstream review

## Priority and need signals

The current implementation also enriches packaging jobs with need-driven and priority-style signals derived from production-side order, stock, net-need, and stock-day information.

This helps the packaging layer evaluate not only operational fit, but also urgency.

## Outputs and reporting

The packaging engine can produce structured outputs such as:

- line summaries
- backlog outputs
- packaging MRP issue sheets
- packaging MRP detail and summary sheets
- intraday alert outputs
- gap-fill and chain-fill summaries
- phase-based outputs for different solution stages

## Bridge relevance

The packaging engine is tightly connected to the production–packaging bridge.

Its outputs can be used to:

- identify overloaded line-days
- estimate extra-hour needs
- propose production shifting
- trigger revision requests
- support overtime approval decisions

This is one of the reasons the packaging layer functions as a decision engine rather than a standalone scheduler.

## Why it matters

In many planning environments, packaging is treated as a post-processing step.

In this platform, it acts as a feasibility gate for the production plan and as a structured source of revision signals for the overall planning loop.
