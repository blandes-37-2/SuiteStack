# SuiteStack

An enterprise-grade commercial real estate intelligence platform providing building analytics, AI-powered tenant insights, interactive stacking plans, and market intelligence at scale.

**Built by [Ben Landes](https://BenLandes.net)**

![React](https://img.shields.io/badge/React-18.0-blue) ![TypeScript](https://img.shields.io/badge/TypeScript-5.0-blue) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-blue) ![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4-green) ![Perplexity](https://img.shields.io/badge/Perplexity-Sonar_Pro-purple)

---

## Table of Contents

- [Scale](#scale)
- [Features](#features)
- [AI Enrichment Pipeline](#ai-enrichment-pipeline)
- [Tech Stack](#tech-stack)
- [Architecture & Performance](#architecture--performance)
- [Security](#security)

---

## Scale

| Metric | Value |
|---|---|
| Buildings | 893 across 12 major regions |
| Suites | 12,643 with full occupancy data |
| Tenants | 6,553 AI-enriched profiles |
| Submarkets | 96 across 12 regions |
| Active Users | 70 enterprise users |
| Components | 350+ modular TypeScript components |

![SuiteStack Dashboard](Screenshot%202025-11-06%20201953.png)

---

## Features

### Data Management
- **All-or-Nothing CSV Import** — three-tier validation, 95% fuzzy duplicate detection, business name normalization, full rollback on failure
- **Intelligent Column Mapping** — auto-maps imported columns to schema fields with conflict resolution
- **Excel & PDF Export** — formatted exports with custom headers; 100-page PDFs generate in under 3 seconds

### Interactive Stacking Plans
SVG-based floor visualizations rendered in real time with color-coded overlays:
- Lease expiry heat maps
- Industry clustering
- Availability status and tenant size analysis
- PDF/PNG export with print optimization

### Market Intelligence
- Tenant In Market (TIM) tracking
- Lease expiration forecasting
- Competitive analysis dashboards
- Submarket heat maps and absorption reports

### Search & Filtering
- Multi-dimensional filtering across market, class, size, and status
- Full-text tenant search with fuzzy matching
- Geographic clustering
- Saved search profiles

### Enterprise Permissions
Four-tier role hierarchy (Admin → Researcher → Broker → Viewer) with two-dimensional access control: Region × Property Type, down to building-level assignments with full audit trails.

---

## AI Enrichment Pipeline

A multi-stage micro-enrichment architecture with independent processing queues:

**1. Industry Classification**
Two-stage pipeline — Perplexity AI Sonar Pro for business research, OpenAI GPT-4 for final classification. 95% confidence threshold required for auto-approval. Specialized models for Office vs Industrial properties.

**2. Company Intelligence**
Automated website and LinkedIn detection, multi-source revenue validation, real-time RTO policy monitoring, confidence scoring on every AI decision.

**3. Voice-Enabled Updates**
Speech-to-text data entry for field use — hands-free suite updates via natural language.

**Performance:** 6-second rate limiting between API calls, parallel micro-queue architecture, exponential backoff retry logic, daily audit completeness checks.

---

## Tech Stack

| Layer | Stack |
|---|---|
| Frontend | React 18, TypeScript 5.0, Vite 5, shadcn/ui, Tailwind CSS v4, TanStack Query v5 |
| Visualizations | React-Leaflet (maps), Recharts (dashboards), custom SVG stacking plans |
| Backend | Node.js 20, Express.js, TypeScript, Drizzle ORM |
| Database | PostgreSQL 16 (Neon serverless), 45+ interconnected tables |
| Auth | Passport.js, bcrypt, PostgreSQL-backed sessions via connect-pg-simple |
| AI | OpenAI GPT-4, Perplexity AI Sonar Pro |
| Real-time | WebSocket for live collaboration |
| Export | PDFKit, Multer (CSV import) |

---

## Architecture & Performance

**Performance benchmarks:**
- Initial page load: < 2 seconds
- API response average: < 200ms
- Complex DB queries: < 50ms
- CSV import (10,000 records): < 30 seconds
- PDF generation (100 pages): < 3 seconds
- Real-time update latency: < 100ms

**Key architectural decisions:**
- Virtual scrolling handles 100,000+ row tables without pagination
- 90% query performance improvement via strategic indexing
- Optimistic UI updates via React Query mutations
- PostgreSQL-backed sessions replacing in-memory storage
- Browser back/forward navigation with full state restoration
- Nightly aggregations at 2 AM ET with orphaned record detection
- Suite number change tracking with 90-day expiration warnings

**Data integrity:** Foreign key normalization across 30+ tables, JSONB columns for flexible metadata, composite indexes for analytics queries, complete user-attributed audit trails.

---

## Security

- httpOnly cookie session management
- bcrypt password hashing (12 rounds)
- Parameterized queries (SQL injection prevention)
- React-native XSS protection
- CORS policies configured per environment
- Rate limiting on sensitive endpoints
- WCAG 2.1 AA accessibility compliance

---

## License

MIT © Ben Landes