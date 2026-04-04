# Profile README Modernization — Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Transform the `yurieastwood/yurieastwood` GitHub profile README from a static, generator-produced layout into a dynamic, community-focused profile powered by `lowlighter/metrics` and GitHub Actions.

**Architecture:** The profile is a single `README.md` backed by three GitHub Action workflows that auto-update dynamic sections (metrics SVGs, activity feed, blog posts). Static content (bio, quick-facts, tech stack, socials) is hand-edited. No emojis anywhere.

**Tech Stack:** GitHub Flavored Markdown, HTML tables, capsule-render, shields.io, lowlighter/metrics, jamesgeorge007/github-activity-readme, gautamkrishnar/blog-post-workflow, GitHub Actions (scheduled cron).

---

## File Map

| Action | Path | Responsibility |
|--------|------|----------------|
| Delete | `CODE_OF_CONDUCT.md` | No longer needed for profile repo |
| Delete | `CONTRIBUTING.md` | No longer needed for profile repo |
| Delete | `assets/github-header-image.png` | Replaced by capsule-render |
| Rewrite | `README.md` | Full profile content |
| Create | `.github/workflows/metrics.yml` | lowlighter/metrics Action — generates SVGs |
| Create | `.github/workflows/activity.yml` | github-activity-readme Action — updates activity feed |
| Create | `.github/workflows/blog-posts.yml` | blog-post-workflow Action — updates latest posts |

---

### Task 1: Delete old files

**Files:**
- Delete: `CODE_OF_CONDUCT.md`
- Delete: `CONTRIBUTING.md`
- Delete: `assets/github-header-image.png`

- [ ] **Step 1: Delete the three files**

```bash
cd /Users/yurieastwood/Sources/yurieastwood
git rm CODE_OF_CONDUCT.md CONTRIBUTING.md assets/github-header-image.png
```

- [ ] **Step 2: Remove the empty assets directory**

```bash
rmdir assets
```

If git doesn't track the empty directory, this just cleans up the local filesystem.

- [ ] **Step 3: Verify deletions**

```bash
git status
```

Expected: three deleted files staged.

- [ ] **Step 4: Commit**

```bash
git commit -m "chore: remove CODE_OF_CONDUCT, CONTRIBUTING, and old header image

These files are not needed for a GitHub profile README repo.
The static header image is replaced by capsule-render in the next commit."
```

---

### Task 2: Rewrite README.md

**Files:**
- Rewrite: `README.md`

This is the core deliverable. The entire file is replaced with the new layout. Placeholder text is wrapped in `<!-- PLACEHOLDER: ... -->` comments so the user can find-and-replace them easily.

- [ ] **Step 1: Write the new README.md**

Replace the entire contents of `README.md` with:

```markdown
![header](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,12,19,24,30&height=200&section=header&text=Yuri%20Eastwood&fontSize=42&fontAlignY=35&desc=Delivery%20Architect%20%7C%20Open%20Source%20Contributor%20%7C%20Community%20Builder&descSize=16&descAlignY=55&animation=fadeIn)

> [!NOTE]
> I'm a Delivery Architect passionate about building robust systems and fostering open-source communities.
> I love bridging the gap between architecture and delivery, and I'm always looking for like-minded contributors.
> <!-- PLACEHOLDER: Customize this bio to reflect your current focus and personality. -->

<table>
  <tr>
    <td><img src="https://raw.githubusercontent.com/primer/octicons/main/icons/telescope-16.svg" width="16" height="16" alt="telescope"></td>
    <td><strong>Currently working on</strong> — <!-- PLACEHOLDER: your current project or focus --></td>
  </tr>
  <tr>
    <td><img src="https://raw.githubusercontent.com/primer/octicons/main/icons/book-16.svg" width="16" height="16" alt="book"></td>
    <td><strong>Currently learning</strong> — <!-- PLACEHOLDER: what you're exploring --></td>
  </tr>
  <tr>
    <td><img src="https://raw.githubusercontent.com/primer/octicons/main/icons/people-16.svg" width="16" height="16" alt="people"></td>
    <td><strong>Looking to collaborate on</strong> — <!-- PLACEHOLDER: types of projects or topics --></td>
  </tr>
  <tr>
    <td><img src="https://raw.githubusercontent.com/primer/octicons/main/icons/comment-discussion-16.svg" width="16" height="16" alt="discussion"></td>
    <td><strong>Ask me about</strong> — <!-- PLACEHOLDER: your areas of expertise --></td>
  </tr>
  <tr>
    <td><img src="https://raw.githubusercontent.com/primer/octicons/main/icons/mail-16.svg" width="16" height="16" alt="mail"></td>
    <td><strong>How to reach me</strong> — <!-- PLACEHOLDER: preferred contact method --></td>
  </tr>
</table>

---

## Socials

### Professional

[![LinkedIn](https://img.shields.io/badge/LinkedIn-%230077B5.svg?logo=linkedin&logoColor=white)](https://linkedin.com/in/yurieastwood) [![Medium](https://img.shields.io/badge/Medium-12100E?logo=medium&logoColor=white)](https://medium.com/@yurieastwood) [![Stack Overflow](https://img.shields.io/badge/-Stackoverflow-FE7A16?logo=stack-overflow&logoColor=white)](https://stackoverflow.com/users/3212472)

### Social / Streaming

[![X](https://img.shields.io/badge/X-%23000000.svg?logo=X&logoColor=white)](https://x.com/yurieastwood) [![Twitch](https://img.shields.io/badge/Twitch-%239146FF.svg?logo=Twitch&logoColor=white)](https://twitch.tv/yurieastwood) [![Facebook](https://img.shields.io/badge/Facebook-%231877F2.svg?logo=Facebook&logoColor=white)](https://facebook.com/yurieastwood) [![Instagram](https://img.shields.io/badge/Instagram-%23E4405F.svg?logo=Instagram&logoColor=white)](https://instagram.com/yurieastwood)

---

## Tech Stack

### Languages

![C#](https://img.shields.io/badge/c%23-%23239120.svg?style=flat&logo=csharp&logoColor=white) ![C++](https://img.shields.io/badge/c++-%2300599C.svg?style=flat&logo=c%2B%2B&logoColor=white) ![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=flat&logo=typescript&logoColor=white) ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=flat&logo=javascript&logoColor=%23F7DF1E) ![Python](https://img.shields.io/badge/python-3670A0?style=flat&logo=python&logoColor=ffdd54) ![PHP](https://img.shields.io/badge/php-%23777BB4.svg?style=flat&logo=php&logoColor=white) ![PowerShell](https://img.shields.io/badge/PowerShell-%235391FE.svg?style=flat&logo=powershell&logoColor=white) ![Shell Script](https://img.shields.io/badge/shell_script-%23121011.svg?style=flat&logo=gnu-bash&logoColor=white)

### Cloud and Infrastructure

![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=flat&logo=amazon-aws&logoColor=white) ![Azure](https://img.shields.io/badge/azure-%230072C6.svg?style=flat&logo=microsoftazure&logoColor=white) ![Google Cloud](https://img.shields.io/badge/GoogleCloud-%234285F4.svg?style=flat&logo=google-cloud&logoColor=white) ![GithubPages](https://img.shields.io/badge/github%20pages-121013?style=flat&logo=github&logoColor=white)

### Frameworks

![.Net](https://img.shields.io/badge/.NET-5C2D91?style=flat&logo=.net&logoColor=white) ![Blazor](https://img.shields.io/badge/blazor-%235C2D91.svg?style=flat&logo=blazor&logoColor=white)

### Databases

![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=flat&logo=postgresql&logoColor=white) ![MySQL](https://img.shields.io/badge/mysql-%2300000f.svg?style=flat&logo=mysql&logoColor=white) ![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=flat&logo=mariadb&logoColor=white) ![MicrosoftSQLServer](https://img.shields.io/badge/Microsoft%20SQL%20Server-CC2927?style=flat&logo=microsoft%20sql%20server&logoColor=white) ![MongoDB](https://img.shields.io/badge/MongoDB-%234ea94b.svg?style=flat&logo=mongodb&logoColor=white) ![AmazonDynamoDB](https://img.shields.io/badge/Amazon%20DynamoDB-4053D6?style=flat&logo=Amazon%20DynamoDB&logoColor=white) ![ApacheCassandra](https://img.shields.io/badge/cassandra-%231287B1.svg?style=flat&logo=apache-cassandra&logoColor=white) ![Redis](https://img.shields.io/badge/redis-%23DD0031.svg?style=flat&logo=redis&logoColor=white) ![SQLite](https://img.shields.io/badge/sqlite-%2307405e.svg?style=flat&logo=sqlite&logoColor=white) ![Firebase](https://img.shields.io/badge/Firebase-039BE5?style=flat&logo=Firebase&logoColor=white)

### DevOps and CI/CD

![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=flat&logo=docker&logoColor=white) ![Kubernetes](https://img.shields.io/badge/kubernetes-%23326ce5.svg?style=flat&logo=kubernetes&logoColor=white) ![Terraform](https://img.shields.io/badge/terraform-%235835CC.svg?style=flat&logo=terraform&logoColor=white) ![Vagrant](https://img.shields.io/badge/vagrant-%231563FF.svg?style=flat&logo=vagrant&logoColor=white) ![AZUREDEVOPS](https://img.shields.io/badge/azuredevops-0078D7.svg?style=flat&logo=azuredevops&logoColor=white&color=%230078D7) ![CHEF](https://img.shields.io/badge/Chef-02303A.svg?style=flat&logo=Chef&logoColor=white&color=%23F09820) ![PUPPET](https://img.shields.io/badge/Puppet-02303A.svg?style=flat&logo=Puppet&logoColor=white&color=%23FFAE1A)

### Observability

![GRAFANA](https://img.shields.io/badge/grafana-F46800.svg?style=flat&logo=grafana&logoColor=white&color=%23F46800) ![KIBANA](https://img.shields.io/badge/kibana-005571.svg?style=flat&logo=kibana&logoColor=white&color=%23005571) ![PROMETHEUS](https://img.shields.io/badge/prometheus-E6522C.svg?style=flat&logo=prometheus&logoColor=white&color=%23E6522C) ![NEWRELIC](https://img.shields.io/badge/newrelic-1CE783.svg?style=flat&logo=newrelic&logoColor=white&color=%231CE783) ![ElasticSearch](https://img.shields.io/badge/-ElasticSearch-005571?style=flat&logo=elasticsearch)

### Quality and Tools

![SonarQube](https://img.shields.io/badge/SonarQube-black?style=flat&logo=sonarqube&logoColor=4E9BCD) ![SonarLint](https://img.shields.io/badge/SonarLint-CB2029?style=flat&logo=SONARLINT&logoColor=white) ![Postman](https://img.shields.io/badge/Postman-FF6C37?style=flat&logo=postman&logoColor=white) ![Swagger](https://img.shields.io/badge/-Swagger-%23Clojure?style=flat&logo=swagger&logoColor=white) ![Jira](https://img.shields.io/badge/jira-%230A0FFF.svg?style=flat&logo=jira&logoColor=white) ![Trello](https://img.shields.io/badge/Trello-%23026AA7.svg?style=flat&logo=Trello&logoColor=white)

---

## Recent Activity

<!--RECENT_ACTIVITY:start-->
<!--RECENT_ACTIVITY:end-->

<!--RECENT_ACTIVITY:last_update-->
<!--RECENT_ACTIVITY:last_update_end-->

---

## Latest Posts

<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->

---

## GitHub Metrics

<p align="center">
  <img src="./generated/github-metrics.svg" alt="GitHub Metrics" width="49%">
  <img src="./generated/github-metrics-community.svg" alt="Community Metrics" width="49%">
</p>

---

[![](https://visitcount.itsvg.in/api?id=yurieastwood&icon=0&color=0)](https://visitcount.itsvg.in)

[![BuyMeACoffee](https://img.shields.io/badge/Buy%20Me%20a%20Coffee-ffdd00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/yurieastwood) [![PayPal](https://img.shields.io/badge/PayPal-00457C?style=for-the-badge&logo=paypal&logoColor=white)](https://paypal.me/yurieastwood)

![footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,12,19,24,30&height=120&section=footer)
```

- [ ] **Step 2: Verify the file looks correct**

```bash
head -5 README.md
wc -l README.md
```

Expected: first line is the capsule-render header image, total line count is approximately 100-120 lines.

- [ ] **Step 3: Verify no emojis remain**

```bash
grep -Pn '[\x{1F300}-\x{1F9FF}]' README.md || echo "No emojis found"
```

Expected: "No emojis found"

- [ ] **Step 4: Verify all placeholder comments are findable**

```bash
grep -c 'PLACEHOLDER' README.md
```

Expected: 6 (one per quick-fact row + one for the bio)

- [ ] **Step 5: Commit**

```bash
git add README.md
git commit -m "feat: rewrite profile README with modern community-focused layout

- Dynamic capsule-render header and footer
- Bio callout with quick-facts table using Octicon SVG icons
- Social links split into Professional / Social-Streaming
- Tech stack organized by category (7 groups)
- Comment markers for auto-updated activity and blog post sections
- References to lowlighter/metrics generated SVGs
- Visitor counter and donation links in footer
- No emojis throughout"
```

---

### Task 3: Create lowlighter/metrics workflow

**Files:**
- Create: `.github/workflows/metrics.yml`

This workflow generates two SVG files — `generated/github-metrics.svg` and `generated/github-metrics-community.svg` — and commits them to the repo daily.

- [ ] **Step 1: Create the workflow directory**

```bash
mkdir -p .github/workflows
```

- [ ] **Step 2: Create the metrics workflow file**

Write `.github/workflows/metrics.yml` with:

```yaml
name: GitHub Metrics

on:
  schedule:
    - cron: "0 4 * * *" # Daily at 4:00 UTC
  workflow_dispatch: # Allow manual trigger

jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          token: ${{ secrets.METRICS_TOKEN }}
          filename: generated/github-metrics.svg
          # Base stats
          base: header, activity, community, repositories, metadata
          # Contribution calendar
          plugin_isocalendar: yes
          plugin_isocalendar_duration: half-year
          # Most used languages
          plugin_languages: yes
          plugin_languages_sections: most-used
          plugin_languages_categories: markup, programming
          plugin_languages_colors: github
          plugin_languages_limit: 8
          plugin_languages_recent_load: 300
          plugin_languages_recent_days: 14
          # Achievement badges
          plugin_achievements: yes
          plugin_achievements_display: compact
          plugin_achievements_threshold: C
          # Config
          config_timezone: America/Sao_Paulo

      - uses: lowlighter/metrics@latest
        with:
          token: ${{ secrets.METRICS_TOKEN }}
          filename: generated/github-metrics-community.svg
          base: ""
          # Recent activity
          plugin_activity: yes
          plugin_activity_limit: 5
          plugin_activity_days: 14
          plugin_activity_filter: all
          plugin_activity_visibility: public
          # Notable contributions
          plugin_notable: yes
          plugin_notable_repositories: yes
          plugin_notable_from: all
          # People (followers / following)
          plugin_people: yes
          plugin_people_types: followers, following
          plugin_people_limit: 24
          plugin_people_size: 28
          # Config
          config_timezone: America/Sao_Paulo
```

- [ ] **Step 3: Verify YAML syntax**

```bash
python3 -c "import yaml; yaml.safe_load(open('.github/workflows/metrics.yml'))" && echo "Valid YAML"
```

Expected: "Valid YAML"

- [ ] **Step 4: Commit**

```bash
git add .github/workflows/metrics.yml
git commit -m "ci: add lowlighter/metrics workflow for auto-generated SVG stats

Generates two SVGs daily:
- github-metrics.svg (base stats, calendar, languages, achievements)
- github-metrics-community.svg (activity, notable contribs, people)

Requires METRICS_TOKEN secret (PAT with read:user scope)."
```

---

### Task 4: Create GitHub Activity workflow

**Files:**
- Create: `.github/workflows/activity.yml`

This workflow auto-updates the recent activity section between the `<!--RECENT_ACTIVITY:start-->` / `<!--RECENT_ACTIVITY:end-->` comment markers in `README.md`.

- [ ] **Step 1: Create the activity workflow file**

Write `.github/workflows/activity.yml` with:

```yaml
name: Recent GitHub Activity

on:
  schedule:
    - cron: "0 5 * * *" # Daily at 5:00 UTC (after metrics)
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v4
      - uses: jamesgeorge007/github-activity-readme@master
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          COMMIT_MSG: "chore: update recent GitHub activity"
          MAX_LINES: 5
```

- [ ] **Step 2: Verify YAML syntax**

```bash
python3 -c "import yaml; yaml.safe_load(open('.github/workflows/activity.yml'))" && echo "Valid YAML"
```

Expected: "Valid YAML"

- [ ] **Step 3: Commit**

```bash
git add .github/workflows/activity.yml
git commit -m "ci: add GitHub Activity workflow for auto-updated activity feed

Populates the RECENT_ACTIVITY comment markers in README.md daily.
Shows last 5 public activities (pushes, PRs, issues, reviews)."
```

---

### Task 5: Create Blog Posts workflow

**Files:**
- Create: `.github/workflows/blog-posts.yml`

This workflow auto-updates the latest posts section between the `<!-- BLOG-POST-LIST:START -->` / `<!-- BLOG-POST-LIST:END -->` comment markers in `README.md`.

- [ ] **Step 1: Create the blog-posts workflow file**

Write `.github/workflows/blog-posts.yml` with:

```yaml
name: Latest Blog Posts

on:
  schedule:
    - cron: "0 6 * * *" # Daily at 6:00 UTC (after activity)
  workflow_dispatch:

jobs:
  update-readme-with-blog:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v4
      - uses: gautamkrishnar/blog-post-workflow@v1
        with:
          feed_list: "https://medium.com/feed/@yurieastwood"
          max_post_count: 5
          readme_path: ./README.md
          template: "$newline- [$title]($url) — $date"
          date_format: "yyyy-mm-dd"
          commit_message: "chore: update latest blog posts"
```

**Note on LinkedIn:** LinkedIn does not offer a reliable public RSS feed for articles. During implementation, check if `https://www.linkedin.com/pulse/feed/articles/urn:li:member:YOUR_ID` works for your account. If it does, add it to `feed_list` as a comma-separated second URL. If not, a third-party RSS bridge like `rss.app` or `fetchrss.com` can be used as a fallback — but start with Medium only and add LinkedIn once a working feed URL is confirmed.

- [ ] **Step 2: Verify YAML syntax**

```bash
python3 -c "import yaml; yaml.safe_load(open('.github/workflows/blog-posts.yml'))" && echo "Valid YAML"
```

Expected: "Valid YAML"

- [ ] **Step 3: Commit**

```bash
git add .github/workflows/blog-posts.yml
git commit -m "ci: add blog post workflow for auto-updated latest posts

Pulls latest 5 posts from Medium RSS feed daily.
LinkedIn feed URL to be added once a working RSS source is confirmed."
```

---

### Task 6: Post-implementation setup notes

This is not a code task — it documents the manual steps the user needs to take after pushing the code.

- [ ] **Step 1: Verify all files are committed and clean**

```bash
git status
git log --oneline -6
```

Expected: clean working tree, 5 new commits (one per task above).

- [ ] **Step 2: Document required manual steps**

After pushing to GitHub, the user must:

1. **Create a PAT** — go to GitHub > Settings > Developer settings > Personal access tokens > Fine-grained tokens. Create a token named `METRICS_TOKEN` with `read:user` scope (classic) or `Account permissions > Profile: Read` (fine-grained).

2. **Add the secret** — go to the `yurieastwood/yurieastwood` repo > Settings > Secrets and variables > Actions > New repository secret. Name: `METRICS_TOKEN`, value: the PAT from step 1.

3. **Trigger workflows manually** — go to each workflow under Actions and click "Run workflow" to populate the dynamic sections immediately rather than waiting for the cron schedule:
   - Run "GitHub Metrics" first (generates the SVGs)
   - Run "Recent GitHub Activity" second
   - Run "Latest Blog Posts" third

4. **Customize placeholder text** — search the README for `PLACEHOLDER` comments and replace them with real content.

5. **Verify LinkedIn RSS** — test whether `https://www.linkedin.com/pulse/feed/articles/urn:li:member:YOUR_ID` returns XML. If it does, add it to the `feed_list` in `.github/workflows/blog-posts.yml`.

- [ ] **Step 3: Push to GitHub**

```bash
git push origin main
```
