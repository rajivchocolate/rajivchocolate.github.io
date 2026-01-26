---
name: CTLogInspector
tools: [Python, Security, SQLite]
image: https://images.unsplash.com/photo-1563986768609-322da13575f3?w=800
description: Certificate Transparency log monitoring and domain enumeration tool
external_url: https://github.com/rajivchocolate/CTLogInspector
---

# CTLogInspector

A command-line tool and Python library for security researchers to enumerate domains from Certificate Transparency logs. The project parses, analyzes, and monitors CT logs to discover subdomains and track SSL/TLS certificate issuance.

## Features

- Pattern-based domain filtering using glob syntax
- Resumable scanning with automatic progress tracking
- Delta scanning for incremental updates
- Asynchronous HTTP operations with concurrency control
- Certificate issuer statistics and expiration tracking
- Wildcard certificate detection
- Webhook notifications for new discoveries
- Multiple export formats (JSON, CSV, HTML)
- Prometheus metrics and Elasticsearch integration

## Technologies

Built with Python 3, SQLite, and async/await patterns for efficient certificate log analysis.

[View on GitHub](https://github.com/rajivchocolate/CTLogInspector)
