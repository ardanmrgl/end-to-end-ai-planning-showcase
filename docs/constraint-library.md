# Constraint Library

## Purpose

The platform is built around explicit operational constraints rather than generic planning assumptions.

This document summarizes the types of constraints visible from the current implementation.

## Line structure and capacity constraints

The packaging layer includes line-aware settings such as:

- machine counts by line
- daily working hours by line
- candidate-line mappings
- line fallback definitions
- line-priority ordering

This means packaging capacity is evaluated as a structured line problem, not as a single aggregated capacity pool.

## Staffing constraints

The current implementation includes staffing-aware packaging planning through concepts such as:

- staff required per line
- total available staff by day
- binary line-open style constraints
- manual and default workforce profiles

These constraints matter because line feasibility may depend on labor, not only on nominal machine hours.

## Route and stage constraints

The packaging engine works with route-aware logic, including:

- product routes
- stage ordering
- intermediate vs final stages
- release-day logic
- line-specific process exemptions
- semifinished-enabled lines
- post-production and post-slicing lag rules

This allows the model to account for real route structure rather than using a single flat operation model.

## Material and MRP constraints

The planning stack also includes material-sensitive constraints such as:

- packaging material mapping
- material usage checks
- MRP-mode behavior
- due-date aware material interpretation
- shortage issue generation

This helps prevent plans that look feasible on paper but fail because materials are not actually ready.

## Bridge and overload constraints

The production–packaging bridge introduces another class of constraints:

- overloaded line-day detection
- extra-hour requirement estimation
- overtime approval logic
- automatic production shifting when overload is not accepted
- exempt-line behavior for bridge logic

These constraints transform packaging from a reporting layer into a revision trigger for upstream planning.

## Penalty-based decision behavior

From the packaging planning side, the current implementation includes configurable penalty concepts such as:

- backlog penalty
- split penalty
- delay penalty
- two-stage WIP penalty
- line-priority penalty
- fallback penalties for less preferred line usage

This is important because the engine is not only checking feasibility; it is also shaping trade-offs.

## Notable encoded business rules

Visible examples of plant-style business rules include:

- `Kuvet-4` and `Kuvet-1` do not share the same effective day-hour assumptions.
- `Kuvet-1` can be constrained by the fill state of `Kuvet-4`.
- some lines are treated as exempt from certain process-day logic
- some lines are treated as eligible for semifinished handling
- gap-fill and stock-day related heuristics can be applied in runtime

## Why this matters

A large part of industrial planning value comes from how constraints are encoded.
The presence of this constraint library is one of the reasons the platform behaves like a domain-specific decision system rather than a generic scheduling prototype.
