# End-to-End AI Planning Platform

A showcase repository for an industrial AI decision platform designed to generate **executable** weekly production and packaging plans by evaluating production capacity, packaging feasibility, MRP and material constraints, purchasing due dates, available and inbound raw materials, and operational bottlenecks in a single decision architecture.

## Overview

This platform was built to solve a common industrial problem: plans that look correct in spreadsheets but fail in execution.

Instead of treating planning as an isolated capacity exercise, the system connects **production, packaging, MRP, material reality, purchasing due dates, and process uncertainty** in the same decision loop.

With a single run, the platform can generate a weekly production plan and a weekly packaging plan in **under 20 seconds**, then test downstream feasibility, surface bottlenecks, and support more executable alternatives.

## Core capabilities

- Weekly production planning
- Weekly packaging planning
- Packaging feasibility validation
- MRP and material-aware planning
- Purchasing due-date aware decision logic
- Raw material availability and inbound-material awareness
- What-if scenario comparison
- Explainable decision support
- Local private GPT/LLM integration
- Entropic Bayes-based fermentation readiness forecasting

## What makes it different

The platform does not only generate a plan.

It evaluates whether the plan can actually work in the field.
If a downstream bottleneck emerges, the system can revise the decision flow and help the user compare more executable alternatives.

This makes the platform closer to an **industrial decision system** than a conventional planning tool.

## Interface modules

The GUI combines multiple decision layers in a single workflow:

- Production Planning
- Packaging Planning
- Fermentation Forecasting
- MRP Control
- Notifications
- AI Assistant

## Entropic Bayes layer

One of the platform's distinctive modules is the **Entropic Bayes** layer, positioned inside the fermentation forecasting workflow.

Its role is to estimate fermentation readiness under uncertainty, especially for fermented sausage products, and convert that uncertainty into a practical planning signal for packaging timing and supply chain synchronization.

This approach was also presented at **Falling Walls Lab Türkiye**.

## Private LLM architecture

The platform also includes a **local, private GPT/LLM layer** designed to operate without sending company data outside the environment.

This supports explainable interaction, scenario evaluation, and a more secure enterprise AI architecture for planning-intensive operations.

## Development approach

- Developed fully in-house
- No external consultancy used in development
- Codebase exceeds **40,000 lines**
- Source code remains private

## Repository scope

This is a **showcase repository**.

It intentionally does **not** include:

- production source code
- internal datasets
- private prompts
- company-sensitive rules or configuration
- model files
- deployment assets

The goal of this repository is to present the **system architecture, product logic, and decision philosophy** without exposing proprietary implementation details.

## Contact

For professional collaboration, research discussion, or product inquiries:

**Ardan Morgül**
