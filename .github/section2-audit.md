# Section 2 Audit — ehsaaan

> Last updated: 2026-09-26
> **Next Action:** Build PulseBoard — full-stack SignalR + React project

## Quick Status

| Section | Progress |
|---|---|
| 1. Repo Hygiene | Skipped (no cleanup per user instruction) |
| 2. Portfolio Projects | 50% (2/4 complete) |
| 3. Schedule | ~30% (OrderFlow Weeks 1–3, MemberHub Week 4 complete) |
| 4. OSS Contributions | Skipped (no PRs) |

## Project Registry

| Project | GitHub | Local Path | Commit | Quality Bar | Status |
|---|---|---|---|---|---|
| **OrderFlow** | ✅ ehsaaan/OrderFlow | `/Volumes/Samsung SSD 870 EVO 1TB/Code Projects/OrderFlow` | `d90a8eb` | 5/6 | Complete |
| **MemberHub** | ✅ ehsaaan/MemberHub | `/Volumes/Samsung SSD 870 EVO 1TB/Code Projects/MemberHub` | `0343c71` | 5/6 | Complete |
| **PulseBoard** | ❌ 404 | N/A | — | 0/6 | **Not Started** |
| **Dispatch** | ❌ 404 | N/A | — | 0/6 | Not Started |

## Quality Bar Per Project

### OrderFlow (5/6)
- [x] README (architecture diagram, run-it instructions, ADRs)
- [x] Tests (xUnit: 10 tests — saga, idempotency, domain)
- [x] CI pipeline (GitHub Actions badge present)
- [x] Dockerfile + docker-compose.yml
- [x] MIT License
- [ ] Incremental commit history (⚠️ 1 monolithic commit — likely AI-generated in one pass)

### MemberHub (5/6)
- [x] README (architecture diagram, run-it, auth flow)
- [x] Tests (14 integration tests via WebApplicationFactory)
- [x] CI pipeline (GitHub Actions badge present)
- [x] Dockerfile + docker-compose.yml
- [x] MIT License
- [ ] Incremental commit history (⚠️ 1 monolithic commit — likely AI-generated in one pass)

### PulseBoard (0/6)
- [ ] README
- [ ] Tests
- [ ] CI pipeline
- [ ] Dockerfile
- [ ] MIT License
- [ ] Commit history

### Dispatch (0/6)
- [ ] Same as above (optional — can merge into OrderFlow)

## Known Issues

1. **OrderFlow + MemberHub:** single monolithic commit each (likely AI-generated in one pass) — splitting needed for interview credibility (only if user requests).
2. **PulseBoard + Dispatch:** repos don't exist locally or on GitHub.
3. **Projects live in `/Volumes/Samsung SSD 870 EVO 1TB/Code Projects/`** (APFS), not inside `Portfolio` repo. Portfolio is just a profile README.
4. **Apple Double `._*` files:** all 1,737 deleted. Old exFAT drive (`/Volumes/Mac`) archived to `/Volumes/Mac/Code Projects/Archive/`.

## Recommendations

- **Build PulseBoard** (full-stack SignalR + React) — the main remaining project (~25 commits).
- **Dispatch:** merge into OrderFlow as a 4th service (saves time, keeps 2-repo target) OR build as separate repo (meets 3-repo target).
- **Split commits** on OrderFlow + MemberHub (optional — adds credibility for interviews).
- **Target:** 3 well-built repos (OrderFlow, MemberHub, PulseBoard) + optional Dispatch.

## Section 1: Repo Hygiene Status (Skipped)

Per user instruction: no repo cleanup (no deleting, no private, no unpinning).

## Section 3: Schedule Tracker

| Week | Target | Status |
|---|---|---|
| 1 | Profile README + repo hygiene + OrderFlow scaffold | ✅ README, ✅ scaffold (external) |
| 2 | OrderFlow core (domain, EF Core, endpoints, tests) | ✅ Done (external) |
| 3 | OrderFlow messaging (Service Bus, outbox, Testcontainers, Docker) | ✅ Done (external) |
| 4 | MemberHub (Clean Arch, CQRS, JWT) | ✅ Done (external) |
| 5 | **PulseBoard** (SignalR + React) | **Not started** |
| 6 | Docs, polish, pin top 3 | Not started |

## Section 4: OSS Contributions Log (Skipped)

Target repos: `dotnet/docs`, `MassTransit`, `MediatR`, `FluentValidation`, `Polly`, `Serilog`, `Refit`, `testcontainers-dotnet`, `reduxjs/redux-toolkit`, `react-hook-form`, `TanStack/query`
- PRs submitted: 0

## Project File References

### OrderFlow Structure (for reference when building PulseBoard)
```
OrderFlow/
├── OrderFlow.slnx
├── global.json (SDK 10.0.301)
├── Directory.Build.props
├── src/
│   ├── OrderFlow.Domain/          (Order aggregate, InventoryItem)
│   ├── OrderFlow.Application/     (Handlers: PlaceOrder, ReserveStock, Confirm/Cancel)
│   ├── OrderFlow.Infrastructure/  (EF Core, InMemory bus, Outbox processor)
│   └── OrderFlow.Api/             (Minimal API: POST /orders, GET /orders/{id}, GET /inventory/{sku})
└── tests/OrderFlow.Tests/         (xUnit: 10 tests)
```

### MemberHub Structure (for reference when building PulseBoard)
```
MemberHub/
├── MemberHub.slnx
├── src/
│   ├── MemberHub.Domain/          (Member aggregate, MemberRole, MembershipStatus)
│   ├── MemberHub.Application/     (CQRS: Login, Create/Update/Delete/Get Members)
│   ├── MemberHub.Infrastructure/  (EF Core, JWT, PBKDF2 password hashing)
│   └── MemberHub.Api/             (Minimal API: POST /auth/login, CRUD /members)
└── tests/MemberHub.Tests/         (xUnit: 14 integration tests)
```
