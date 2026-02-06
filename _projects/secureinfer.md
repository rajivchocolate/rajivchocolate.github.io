---
name: SecureInfer
tools: [Go, Security, Kubernetes, Redis, SQLite]
image: https://images.unsplash.com/photo-1555949963-aa79dcee981c?w=800
description: Secure LLM inference API with defense against model extraction, prompt injection, and DoS attacks
external_url: https://github.com/rajivchocolate/secureinfer
---

# SecureInfer

A secure LLM inference API built in Go to explore how AI labs protect their models. The project implements real security controls and includes attack simulations to test defenses.

## Security Controls

- **Risk Scorer**: Scores each request from 0 to 100 based on threat signals
- **Extraction Detector**: Catches attempts to steal the model through systematic queries
- **Tenant Isolator**: Keeps each user's conversation context separate
- **Model Verifier**: Detects if model files have been tampered with

## Features

- Rate limiting with Redis-backed token buckets
- Multi-tenant isolation for conversation contexts
- Request risk scoring and automatic blocking
- Model extraction detection via query pattern analysis
- Attack demonstration scripts (prompt injection, extraction, DoS)
- Kubernetes deployment with network policies

## Technologies

Built with Go and Chi router, SQLite for persistence, Redis for caching and rate limiting, Ollama for local LLM inference, and Kubernetes (Kind) for container orchestration.

[View on GitHub](https://github.com/rajivchocolate/secureinfer)
