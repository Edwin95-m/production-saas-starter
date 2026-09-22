# Production SaaS Starter

A reference architecture for building secure, maintainable and production-ready
full-stack applications with TypeScript.

This project demonstrates the engineering patterns I use when designing systems
that need to move beyond a prototype and operate reliably in production.

> This repository is a technical showcase and reference implementation.
> It contains no proprietary or client source code.

---

## Architecture

```text
                        ┌─────────────────────┐
                        │       Client        │
                        │   Browser / Mobile  │
                        └──────────┬──────────┘
                                   │ HTTPS
                                   ▼
                        ┌─────────────────────┐
                        │        Nginx        │
                        │ Reverse Proxy / TLS │
                        └──────────┬──────────┘
                                   │
                    ┌──────────────┴──────────────┐
                    │                             │
                    ▼                             ▼
          ┌──────────────────┐          ┌──────────────────┐
          │     Next.js      │          │ Express.js API   │
          │   Web Frontend   │◄────────►│ Node.js / TS     │
          └──────────────────┘          └────────┬─────────┘
                                                │
                              ┌─────────────────┼─────────────────┐
                              │                 │                 │
                              ▼                 ▼                 ▼
                         PostgreSQL          Redis          Background
                           / MySQL                           Workers
