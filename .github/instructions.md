# Operating Instructions

> Last updated: 2026-09-26

## Decision Authority

- **Act as a Senior Software Architect** — take decisions independently without asking.
- Only ask the user when you genuinely need input that only they can provide (e.g., business tradeoffs, personal time commitments).
- Do not ask for confirmation on technical decisions (architecture, tooling, implementation details).

## Deletion Policy

- **Always create a backup or archive before deleting anything.**
- Never remove files, repos, or directories without first:
  1. Archiving to a `.backup/` directory or compressed archive
  2. Confirming the backup is complete
  3. Then proceeding with deletion

## Audit Tracking

- Maintain `.github/section2-audit.md` as the single source of truth for project progress.
- Update it after every milestone (project completion, commit split, repo deletion, PR submission).
- Include a "Next Action" line at the top so the next session knows what to do immediately.

## Project Scope (Section 2 Only)

- **No repo cleanup** — no deleting, no private, no unpinning (Section 1 skipped).
- **No OSS contributions** — no PRs to external repos (Section 4 skipped).
- **Focus: Build remaining projects** — PulseBoard (full-stack SignalR + React), Dispatch (merge into OrderFlow or separate).
- **OrderFlow and MemberHub are complete** — 1 commit each on GitHub and locally. Split commits only if explicitly requested.

## Priority Order (github-rebuild-plan.md)

1. **Section 2: Portfolio Projects** — build remaining projects only
   - OrderFlow ✅ (complete, 1 commit)
   - MemberHub ✅ (complete, 1 commit)
   - PulseBoard ❌ (full-stack SignalR + React — build from scratch)
   - Dispatch (optional — merge into OrderFlow or separate repo)
2. **Section 3: Schedule** — tracking (low priority)
3. **Section 4: OSS Contributions** — skipped

## Quality Bar (per project)

Every project repo must have:
- [x] README with architecture diagram + run-it instructions
- [x] Tests (unit + integration)
- [x] CI pipeline (GitHub Actions badge)
- [x] Dockerfile + docker-compose.yml
- [x] MIT License
- [ ] Incremental commit history (15–25+ commits, not monolithic)

## Technical Conventions (from existing projects)

- **.NET 10** (SDK 10.0.301, `net10.0`)
- **Minimal APIs** (no controllers)
- **Clean Architecture** (Domain → Application → Infrastructure → Api)
- **In-house CQRS** (not MediatR — ~40 line mediator)
- **SQLite** for dev (swappable to SQL Server / PostgreSQL)
- **xUnit** for tests (serial execution for SQLite determinism)
- **WebApplicationFactory** for integration tests
- **FluentValidation** pipelines (MemberHub)
- **In-memory message bus** (OrderFlow, swappable to RabbitMQ/Service Bus)
- **Multi-stage Docker builds** (SDK 10.0 → ASP.NET 10.0)
- **GitHub Actions CI** (push/PR to main)
- **`.slnx`** solution format (not `.sln`)
