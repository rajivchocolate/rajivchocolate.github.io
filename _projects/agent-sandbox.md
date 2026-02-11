---
name: Agent Sandbox
tools: [Go, Security, Docker, Containers]
image: https://images.unsplash.com/photo-1558494949-ef010cbdcc31?w=800
description: Secure container runtime for executing untrusted AI agent code with defense-in-depth isolation
external_url: https://github.com/rajivchocolate/agent-sandbox
---

# Agent Sandbox

A secure container runtime that executes untrusted code from AI agents in locked-down containers. Supports Python, Node.js, Bash, and Claude Code itself — all sandboxed with defense-in-depth isolation so agents can do real work without escaping to the host.

## Key Security Controls

- **Custom seccomp profile**: Deny-by-default with ~70 allowed syscalls, `memfd_create` removed to block fileless execution
- **Full namespace isolation**: PID, network, mount, UTS, IPC, user, and cgroup namespaces all separated
- **All capabilities dropped**: `no-new-privileges` flag, non-root user, read-only root filesystem
- **Resource hard caps**: PID limits, memory caps (no swap), CFS CPU quotas, disk quotas, hard timeouts
- **Auth proxy mode**: API tokens never enter the container — a host-side reverse proxy injects credentials so there's nothing to steal via `/proc/self/environ`
- **Escape attempt detection**: Heuristic detector blocks critical-severity patterns at the API layer before code reaches a container

## Sandboxed Claude Code

The standout feature: run Claude Code inside the sandbox so it can do real dev work on your project while jailed from SSH keys, credentials, and anything outside the project directory. The container is the security boundary — Claude runs with full permissions inside because it physically cannot escape.

## Architecture

Code never lives inside the container image. The server writes submitted code to a host temp file, bind-mounts it read-only into a fresh container, captures output, and tears the container down. The whole lifecycle is managed per-request. On Linux it uses containerd natively for faster cold starts; on macOS it uses Docker with equivalent security flags.

## Features

- REST API with SSE streaming for real-time output
- Automatic backend selection (containerd or Docker)
- Rate limiting, concurrency control, and security headers
- Optional Postgres audit logging with execution history
- Prometheus metrics and health endpoints
- Orphan container cleanup loop for crash recovery
- E2E adversarial tests (fork bombs, filesystem writes, network escape, mount/chroot/setuid attempts)
- Docker Compose deployment with full observability stack

## Technologies

Built with Go, Docker/containerd, custom seccomp profiles, Linux namespaces and cgroups, with optional Postgres for audit logging and Prometheus for metrics.

[View on GitHub](https://github.com/rajivchocolate/agent-sandbox)
