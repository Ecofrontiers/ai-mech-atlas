# AI Mechanism Atlas

Interactive atlas of coordination mechanisms, failure modes, and research gaps for AI governance.

**Live:** [aidesignatlas.xyz](https://aidesignatlas.xyz)

## What's Inside

- **33 Coordination Mechanisms** — from prediction markets to constitutional AI, quadratic voting to futarchy
- **26 Failure Modes** — regulatory capture, capability overhang, value lock-in, and more
- **51 Research Gaps** — open problems at the intersection of AI safety and institutional design
- **Case Studies** — real-world implementations and their outcomes
- **L0-L5 Autonomy Taxonomy** — classifying AI systems by control authority (based on HKUST research)

## Quick Start

```bash
npm install
npm run dev
```

Open [localhost:5173](http://localhost:5173).

## Commands

| Command | Description |
|---------|-------------|
| `npm run dev` | Vite dev server with HMR |
| `npm run build` | Production build to `dist/` |
| `npm run preview` | Preview production build |
| `npm run lint` | ESLint |

## Architecture

Single-page React 19 app with all data embedded in `MechanismAtlas.jsx`:

```
src/
  main.jsx              — Entry point
  App.jsx               — Routes to MechanismAtlas
  MechanismAtlas.jsx    — Main component + embedded datasets
  index.css             — Minimal reset
  assets/               — AI-generated imagery
```

### Data Arrays

- `MECHS[]` — coordination mechanisms
- `FAILURES[]` — failure modes
- `GAPS[]` — research gaps
- `CASES[]` — case studies
- `ROLES[]` — stakeholder roles
- `REFS[]` — academic references

All data includes French translations (`descFr`, `fullAnalysisFr`).

## Data Agents Taxonomy

The atlas includes the **L0-L5 Data Agents Taxonomy** (see `DATA_AGENTS_TAXONOMY.md`), a framework for classifying AI systems by autonomy level:

| Level | Control | Agent Role |
|-------|---------|------------|
| L0 | Human 100% | None |
| L1 | Human-initiated | Responder |
| L2 | Human-orchestrated | Executor |
| L3 | Agent-led | Orchestrator |
| L4 | Agent autonomous | Proactive manager |
| L5 | Agent research | Innovator |

Based on HKUST's SIGMOD 2026 tutorial.

## Tech Stack

- React 19
- Vite 7
- Vercel (deployment)
- No backend — all data hardcoded

## Contributing

Edit the data arrays directly in `src/MechanismAtlas.jsx`. Each mechanism, failure mode, and gap follows a consistent schema with English and French fields.

## License

MIT

---

Built by [Ecofrontiers](https://ecofrontiers.xyz)
