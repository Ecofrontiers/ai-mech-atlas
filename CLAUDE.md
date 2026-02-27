# AI Institutional Design Atlas

Interactive atlas of 33 coordination mechanisms, 26 failure modes, and 51 research gaps for AI governance. Target URL: aidesignatlas.xyz.

## Domain Souls

Load these souls when working on the atlas content and governance frameworks:

| Soul | Domain | Role |
|------|--------|------|
| **Atlas** | AI | Core domain — AI capabilities, agent architectures, safety research |
| **Mech** | Cryptoeconomics | Mechanism design — incentives, game theory, coordination primitives |
| **Nous** | Philosophy | Governance theory — institutional design, collective decision-making |

**Soul files:** `~/Desktop/2_resources/<Domain>/SOUL.md`

## Commands

| Command | Description |
|---------|-------------|
| `npm install` | Install dependencies |
| `npm run dev` | Vite dev server with HMR |
| `npm run build` | Production build to dist/ |
| `npm run preview` | Preview production build locally |
| `npm run lint` | ESLint |

## Architecture

```
src/
  main.jsx              — Entry point (React 19 StrictMode)
  App.jsx               — Routes to MechanismAtlas
  MechanismAtlas.jsx    — Main component (1593 lines, monolithic)
  index.css             — Minimal reset
  assets/               — Images (AI-generated via Replicate)
research/               — Reference PDFs (not imported into app)
vercel.json             — SPA routing + security headers + asset caching
```

## Key Details

- **MechanismAtlas.jsx contains everything**: embedded datasets (`MECHS[]`, `FAILURES[]`, `GAPS[]`, `CASES[]`, `ROLES[]`, `REFS[]`), color palette (`P`), font config (`F`), sizing (`SZ`), and all helper components
- **All inline styles** — no CSS files beyond the minimal reset. Colors in `P` object.
- **Bilingual data** — datasets include `descFr`, `fullAnalysisFr` fields (French translations)
- **No backend** — all data hardcoded, no API calls, no env vars needed
- **React 19 + Vite 7** — no routing library, no state management beyond useState/useEffect

## Deployment

**Live:** https://aidesignatlas.xyz
**Repo:** https://github.com/Ecofrontiers/ai-mech-atlas (public)

### Deploy to Production

```bash
cd ~/Desktop/1_projects/ai-mech-atlas
vercel --prod --scope ecofrontiers
```

### After Deploy: Update Custom Domain Alias

Vercel aliases don't auto-update on new deploys. After `vercel --prod`, run:

```bash
# Get the new deployment URL from the output (e.g., ai-mech-atlas-XXXXX-ecofrontiers.vercel.app)
vercel alias set <NEW_DEPLOYMENT_URL> aidesignatlas.xyz --scope ecofrontiers
vercel alias set <NEW_DEPLOYMENT_URL> www.aidesignatlas.xyz --scope ecofrontiers
```

Or use this one-liner after deploy:
```bash
DEPLOY=$(vercel ls ai-mech-atlas --scope ecofrontiers 2>/dev/null | grep -m1 'ai-mech-atlas-' | awk '{print $2}') && \
vercel alias set $DEPLOY aidesignatlas.xyz --scope ecofrontiers && \
vercel alias set $DEPLOY www.aidesignatlas.xyz --scope ecofrontiers
```

### Full Update Workflow

1. Edit `src/MechanismAtlas.jsx` (data arrays: `MECHS[]`, `FAILURES[]`, `GAPS[]`, etc.)
2. Test locally: `npm run dev`
3. Commit: `git add -A && git commit -m "Update mechanisms"`
4. Push: `git push`
5. Deploy: `vercel --prod --scope ecofrontiers`
6. Alias: (use commands above)

## Gotchas

- To update content, edit the data arrays directly in MechanismAtlas.jsx
- ESLint ignores uppercase vars (`varsIgnorePattern: '^[A-Z_]'`) — constants like `P`, `F`, `MECHS` won't trigger warnings
- Bundle is large (~1MB+) due to the monolithic component
- Vercel config sets strict security headers (X-Frame-Options: DENY, CSP)
- **Domain aliases must be manually updated after each deploy** — Vercel doesn't auto-reassign custom domains to new deployments
