# AI Assistant

## Positioning

The AI Assistant is not designed as a generic conversational chatbot.
It operates as a natural-language interface to the planning engine, packaging-control layer, notification system, and runtime operational context.

Its purpose is to make the platform queryable, explainable, and steerable through natural language.

## What it can explain

The assistant can be used to explain planning outcomes such as:

- why a product was selected instead of another product
- why a product was not planned
- why a product was split across multiple days
- which products are critical in the current plan
- what bottlenecks or constraints affected the result

This is supported by decision-trace style runtime context rather than detached text generation.

## What it can analyze

The assistant can support analytical questions such as:

- product-priority comparisons
- split / fragmentation analysis
- notification interpretation
- critical product review
- what-if style scenario prompts
- packaging authority or line-status interpretation

In practice, this allows the user to query the planning engine in business language instead of reading raw optimization outputs.

## What it can control

The assistant is also connected to operational control state in the application.

Depending on the workflow, it can support actions such as:

- closing a packaging line
- reopening a packaging line
- redirecting staff between lines
- recording decisions against notifications
- interacting with packaging-control logic

This moves the assistant beyond passive explanation and closer to an operational control surface.

## Runtime context sources

The assistant works with synchronized runtime context that may include:

- planning outputs
- rejection and placement reasons
- notification memory
- weekly notes
- packaging chatbot controls
- packaging authority state

Because of this, the assistant is better understood as an interface layer to the industrial decision system rather than a standalone LLM wrapper.

## LLM architecture

The natural-language layer is designed to run locally.

From the current implementation perspective, it first checks for a local LM Studio API endpoint and can fall back to a local GGUF model loaded through `llama_cpp`, using a Llama 3-compatible chat format.

This supports closed-loop enterprise usage without sending company data outside the environment.

## Why it matters

Most industrial software can generate outputs, but very few systems allow users to ask:

- Why did this happen?
- What changed?
- What if we change this?
- Which constraint blocked the result?
- Can I intervene directly from the same interface?

This assistant layer is designed to answer those questions inside the planning workflow.
