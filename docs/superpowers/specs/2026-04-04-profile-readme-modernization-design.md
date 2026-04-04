# GitHub Profile README Modernization — Design Spec

## Goal

Modernize the `yurieastwood/yurieastwood` GitHub profile README from a static, generator-produced layout into a dynamic, community-focused profile powered by `lowlighter/metrics` and GitHub Actions.

## Guiding Principles

- **Community / open-source focus** — the profile should signal activity, invite collaboration, and make it easy for contributors to understand who Yuri is and what he works on.
- **No emojis** — section headers, labels, and content must avoid emojis. They feel like GenAI output and undermine the crafted look.
- **Self-hosted where possible** — prefer SVGs committed to the repo over external Vercel-hosted widgets to reduce third-party dependency.
- **Low maintenance** — GitHub Actions handle dynamic content; manual edits are limited to the bio and quick-facts.

---

## Section-by-Section Design

### 1. Header — Dynamic Capsule Render

Remove the broken `Bottom_up.svg` reference and the static `github-header-image.png`.

Replace with a `capsule-render` dynamic SVG header rendered via URL:

```
![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,12,19,24,30&height=200&section=header&text=Yuri%20Eastwood&fontSize=42&fontAlignY=35&desc=Delivery%20Architect%20%7C%20Open%20Source%20Contributor%20%7C%20Community%20Builder&descSize=16&descAlignY=55&animation=fadeIn)
```

A matching waving footer closes the README:

```
![footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,12,19,24,30&height=120&section=footer)
```

Delete `assets/github-header-image.png` and the `assets/` directory.

### 2. Bio and Quick Facts

**Bio** — a `> [!NOTE]` GitHub blockquote callout with 2-3 sentences. Placeholder text clearly marked for user to customize.

**Quick-facts** — an HTML `<table>` with two columns:
- Left column: small (16px) inline SVG icons from Octicons (monochrome, professional).
- Right column: bold label + description text.

Rows:
| Icon | Label |
|------|-------|
| telescope | **Currently working on** — (placeholder) |
| book | **Currently learning** — (placeholder) |
| people | **Looking to collaborate on** — (placeholder) |
| comment-discussion | **Ask me about** — (placeholder) |
| mail | **How to reach me** — (placeholder) |

No emojis. Icons are small, consistent, and professional.

### 3. Social Links

Split into two groups under `###` subheadings:

**Professional**
- LinkedIn, Medium, Stack Overflow

**Social / Streaming**
- X (updated from Twitter — new logo and color), Twitch, Facebook, Instagram

Same shields.io badge style. One line of badges per group.

### 4. Tech Stack (Organized by Category)

Same shields.io badges, grouped under `###` subheadings. No emoji prefixes on headings.

Categories:

- **Languages** — C#, C++, TypeScript, JavaScript, Python, PHP, PowerShell, Shell Script
- **Cloud and Infrastructure** — AWS, Azure, Google Cloud, GitHub Pages
- **Frameworks** — .NET, Blazor
- **Databases** — PostgreSQL, MySQL, MariaDB, SQL Server, MongoDB, DynamoDB, Cassandra, Redis, SQLite, Firebase
- **DevOps and CI/CD** — Docker, Kubernetes, Terraform, Vagrant, Azure DevOps, Chef, Puppet
- **Observability** — Grafana, Kibana, Prometheus, New Relic, ElasticSearch
- **Quality and Tools** — SonarQube, SonarLint, Postman, Swagger, Jira, Trello

### 5. Recent GitHub Activity (Auto-Updated)

Uses `jamesgeorge007/github-activity-readme` GitHub Action.

- Inserts last 5 public activities between HTML comment markers: `<!--RECENT_ACTIVITY:start-->` / `<!--RECENT_ACTIVITY:end-->`
- Activities: pushes, PRs, issues, reviews
- Scheduled cron: daily

### 6. Latest Posts (Auto-Updated)

Uses `gautamkrishnar/blog-post-workflow` GitHub Action.

- Single unified section pulling from multiple RSS sources:
  - Medium: `https://medium.com/feed/@yurieastwood`
  - LinkedIn articles: exact RSS URL to be discovered during implementation (LinkedIn's RSS support varies; may require a third-party RSS bridge as fallback)
- Sorted by date, shows the 5 most recent posts
- Each entry: clickable title + date
- Inserted between comment markers: `<!--BLOG-POST-LIST:start-->` / `<!--BLOG-POST-LIST:end-->`
- Scheduled cron: daily

### 7. GitHub Metrics (lowlighter/metrics)

Replace all existing third-party stat cards with `lowlighter/metrics` Action.

**Removed widgets:**
- `github-readme-stats` (stats card, top langs)
- `github-readme-streak-stats`
- `github-profile-trophy`
- `github-readme-widgets` (certifications)
- `quotes-github-readme` (random dev quote)
- `visitor-badge.laobi.icu` visitor counter (the `visitcount.itsvg.in` counter is relocated to the footer, not removed)

**Generated SVGs (committed to repo):**

1. **`github-metrics.svg`** — main stats overview:
   - Base stats (commits, PRs, issues, stars, contributions)
   - Contribution calendar/graph
   - Most used languages (by repo)
   - Achievement badges

2. **`github-metrics-community.svg`** — community-focused panel:
   - Recent activity (commits, PR reviews, issues)
   - Notable contributions to external repos
   - Follow/star trends

**Action config:**
- Scheduled cron: daily
- Requires `METRICS_TOKEN` secret (PAT with `read:user` scope)
- SVGs committed to `generated/` directory in the repo

### 8. Footer

- Single `visitcount.itsvg.in` visitor counter badge
- Donation links: BuyMeACoffee and PayPal (shields.io `for-the-badge` style, kept as-is)
- Capsule-render waving footer (matching header gradient)

---

## Files to Delete

- `CODE_OF_CONDUCT.md`
- `CONTRIBUTING.md`
- `assets/github-header-image.png`
- `assets/` directory

## Files to Create

- `.github/workflows/metrics.yml` — lowlighter/metrics Action
- `.github/workflows/activity.yml` — github-activity-readme Action
- `.github/workflows/blog-posts.yml` — blog-post-workflow Action

## Files to Modify

- `README.md` — full rewrite following the section order above

## Removals from README

- Broken `Bottom_up.svg` reference
- Status/contributors/stars/forks badge cluster at top
- All emoji prefixes from section headers
- GPRM attribution comment
- All external Vercel-hosted stat widgets
- StackOverflow flair embed (redundant — SO is linked in socials)
- Random dev quote widget

---

## Overall README Section Order

1. Capsule-render waving header
2. Bio paragraph (blockquote callout)
3. Quick-facts table (Octicon SVG icons)
4. Social links (Professional / Social-Streaming)
5. Tech stack (organized by category)
6. Recent GitHub activity (auto-updated)
7. Latest posts (auto-updated, Medium + LinkedIn)
8. GitHub metrics panels (auto-generated SVGs)
9. Visitor counter
10. Donation links
11. Capsule-render waving footer

---

## Required Secrets

| Secret | Scope | Used By |
|--------|-------|---------|
| `METRICS_TOKEN` | PAT with `read:user` | lowlighter/metrics Action |

Note: `blog-post-workflow` and `github-activity-readme` use the default `GITHUB_TOKEN` — no additional secrets needed.
