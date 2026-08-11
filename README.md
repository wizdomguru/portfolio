# Saravanan M — Portfolio

A single-file, data-driven portfolio site. Built with Tailwind (CDN) + Chart.js, no build step required.

## Deploy on GitHub Pages

1. Create a repo (e.g. `saravanan-portfolio`) and push `index.html` to the root (or to a `docs/` folder).
2. In the repo: **Settings → Pages → Source** → select the branch and folder containing `index.html`.
3. Your site will be live at `https://<your-username>.github.io/<repo-name>/`.

No `npm install`, no build tools — it's plain HTML/CSS/JS loaded from CDNs.

## How the page is structured

All visible content is generated from JavaScript arrays near the top of the `<script>` block at the
bottom of `index.html`. The HTML only contains empty containers (e.g. `<div id="automation-grid">`);
the `render...()` functions fill them in on load. **You should only ever need to edit the arrays below —
never the HTML or render functions — to update the site.**

| Array | Powers | Section |
|---|---|---|
| `IMPACT_STATS` | The 3 stat cards next to the chart | Operational Transformation |
| `PILLARS` | The 4 tabbed cards (Provagent GPT, Hybrid AI Triage, RAG, AI Productivity) | Generative AI & Agent Development |
| `AUTOMATION_CATEGORIES` | The filter chips above the automation grid | Automation Portfolio |
| `AUTOMATIONS` | The filterable grid of automation projects | Automation Portfolio |
| `EXPERIENCE` | Role/company/summary cards | Experience |
| `PERSONAL_PROJECTS` | Independent projects (e.g. Billing App) | Independent Builds |
| `MENTORING` | Mentoring/enablement blurbs | Mentoring & Team Enablement |
| `SKILLS` | Tag cloud at the bottom | Stack |

### Adding a new automation project

Open `index.html`, find `const AUTOMATIONS = [ ... ]`, and add a new object before the closing `];`:

```js
{
    title: "New Automation Title",
    category: "monitoring", // must match a key in AUTOMATION_CATEGORIES
    description: "One or two sentences on what it does and why it exists.",
    stack: ["Python", "Some API"],
    outcome: "The measurable result",
},
```

It will appear in the grid automatically, filterable by its `category`.

### Adding a new AI/agent pillar

Add an object to `PILLARS`:

```js
{
    key: "unique_key",
    nav: "Short Tab Label",
    title: "Full Title",
    description: "Full description shown in the tab body.",
    stack: ["Tech", "Tools"],
    outcome: "Key business outcome"
},
```

### Adding a new role, project, or mentoring entry

Same pattern — add an object matching the existing shape to `EXPERIENCE`, `PERSONAL_PROJECTS`, or
`MENTORING`. Each array has a `// Add new ... here` comment right above its closing bracket showing
the exact fields expected.

### Adding a new skill

Just add a string to the `SKILLS` array.

## Things to double-check before publishing

- `EXPERIENCE[0].period` is currently a placeholder (`"Add exact dates here"`) — fill in real dates.
- The phone number is masked as `+91 XXXXXXXXXX` in the hero — update or remove it.
- Confirm the LinkedIn URL and email address are current.

## Tech used

- [Tailwind CSS](https://tailwindcss.com/) (via CDN, no build step)
- [Chart.js](https://www.chartjs.org/) (via CDN) for the impact chart
- Vanilla JavaScript for rendering — no framework, no bundler
