# Constraint Library

## Purpose

The platform is built around explicit operational constraints rather than generic planning assumptions.

## Main constraint families

The current implementation includes structured constraints around:

- line capacity
- working hours
- staffing availability
- route stages
- material availability
- MRP-related checks
- overload handling
- revision triggers
- penalty-based trade-offs

## Scenario Example

![What-If Scenarios](assets/screenshots/what%20if%20scenarios.png)

## Examples of rule types

Examples of encoded rule types include:

- different lines can have different effective day-hour profiles
- secondary lines can depend on the utilization of preferred lines
- some lines can be exempt from certain process-day logic
- some lines can be eligible for semifinished handling
- runtime heuristics can influence gap-filling and stock-day behavior

## Why this matters

A large part of industrial planning value comes from how constraints are encoded.
That is one of the reasons the platform behaves like a domain-specific decision system rather than a generic scheduling prototype.
