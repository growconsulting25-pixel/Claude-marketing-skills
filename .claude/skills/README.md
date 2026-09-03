# Marketing Skills

Claude Code loads every skill folder in this directory automatically. The
skills come from two upstream repositories.

## Source 1: coreyhaines31/marketingskills (50 skills)

Installed from
[coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills)
(v2.11.0, upstream commit d4ff28a) via the `skills` CLI.

`product-marketing` is the foundation skill: the others read the product
marketing context file (`.agents/product-marketing.md`) first, so run that skill
once to describe the product, audience, and positioning.

Update with:

```bash
npx skills add coreyhaines31/marketingskills -a claude-code -y
```

`skills-lock.json` at the repo root records the installed source and hashes so
`npx skills update` can pick up upstream changes.

## Source 2: irinabuht12-oss/marketing-skills (48 skills)

Installed from
[irinabuht12-oss/marketing-skills](https://github.com/irinabuht12-oss/marketing-skills)
(Ryze AI, upstream commit 210d8d9). That repo ships loose markdown files rather
than the Agent Skills layout, so each file was copied into its own
`<name>/SKILL.md` folder using the `name` from its frontmatter. Content is
otherwise unchanged. The `.skill` bundles in the upstream zip are the same
content as ten of the markdown files, so they were not installed separately.

One rename: upstream has two different files both named `landing-page-audit`.
The general CRO audit (file 39, also the one shipped in the zip) keeps
`landing-page-audit`; the ad-to-page message-match audit (file 10) is installed
as `ads-landing-page-audit`.

These are not tracked by `skills-lock.json`. To update, re-clone the upstream
repo and repeat the copy.

### Google Ads

| Skill | What it does |
|-------|--------------|
| `cpa-diagnostics` | When your CPA spikes, Claude breaks down exactly what caused it. It looks across your campaign data and isolates the contributing... |
| `wasted-spend-finder` | Scans your Google and Meta accounts for money being spent on search terms, placements, audiences, and ads that produce zero or near-zero... |
| `budget-scenario-planner` | Models what happens to your CPA, ROAS, conversion volume, and impression share when you increase or decrease budget by any amount. Uses... |
| `client-report-narratives` | Takes your raw campaign performance data and writes the executive summary paragraph that goes at the top of the report. The plain... |
| `anomaly-detection` | Catches unusual performance changes across your accounts — CPC spikes, CVR drops, spend surges, impression collapses, CTR shifts — and... |
| `search-term-mining` | Analyzes your search term reports across all campaigns and surfaces high-intent terms you're not bidding on yet. Groups them by theme,... |
| `ad-copy-variant-generator` | Analyzes your top performing ads, identifies what's working in the hooks, CTAs, messaging angles, and formats, then generates new... |
| `ads-landing-page-audit` | Reviews your landing pages against the ads driving traffic to them. Checks for message match between ad copy and page content, CTA... |
| `bid-strategy-recommendations` | Analyzes your campaign history, conversion volume, CPA targets, and auction dynamics, then recommends the right bid strategy for each... |
| `day-hour-performance-breakdown` | Analyzes performance by day of week and hour of day across your campaigns. Identifies when your ads perform best and worst, recommends... |
| `quality-score-breakdown` | Breaks down Quality Score components for your Google Ads keywords — expected CTR, ad relevance, and landing page experience — and tells... |
| `channel-mix-optimizer` | Given your total budget, recommends the optimal split across Google Search, PMax, Meta prospecting, Meta retargeting, and any other... |
| `conversion-path-analysis` | Maps out how users move through your funnel from first ad click to conversion. Identifies where the biggest drop-offs happen, which... |
| `account-structure-review` | Evaluates your campaign and ad set structure against your actual goals and budget. Flags over-segmentation that fragments your data,... |
| `roas-forecasting` | Projects your ROAS for the next 30, 60, and 90 days based on current performance trends, seasonality patterns from your historical data,... |
| `keyword-cannibalization-check` | Identifies where your own keywords and campaigns are competing against each other in Google Ads auctions. Finds duplicate keywords... |
| `ad-extension-audit` | Reviews all your Google Ads extensions — sitelinks, callouts, structured snippets, call extensions, image extensions, price extensions —... |
| `campaign-naming-convention-builder` | Builds a consistent, filterable naming convention across your Google and Meta accounts based on your campaign types, objectives,... |
| `geo-performance-analysis` | Breaks down campaign performance by geographic location at whatever level matters — country, state, city, DMA, zip code. Flags... |
| `device-performance-split` | Analyzes how your campaigns perform across mobile, desktop, and tablet. Identifies where device performance diverges significantly and... |
| `attribution-model-comparison` | Runs your conversion data through different attribution models side by side — last click, first click, linear, time decay, position... |
| `pacing-monitor` | Tracks daily spend against monthly budget targets across all campaigns and accounts. Tells you exactly where you'll land at current... |
| `ab-test-setup-and-analysis` | Designs statistically valid split tests for ads, audiences, landing pages, or bid strategies. Calculates required sample sizes before... |
| `performance-benchmarking` | Compares your key metrics against industry benchmarks for your specific vertical, campaign type, and platform. Tells you where you're... |
| `weekly-account-summary` | Generates a plain English summary of everything that happened across all your accounts this week. What improved, what declined, what... |
| `ab-test-analyzer` | Statistical significance calculator for A/B test results with sample size requirements, segment breakdowns, and hypothesis generation.... |
| `ad-spend-allocator` | Multi-channel budget optimization using MER, marginal ROAS, and diminishing returns analysis. Use when pasting multi-channel spend and... |
| `competitor-teardown` | Systematic competitive analysis covering positioning, messaging hierarchy, objection handling, and CTA strategy from landing page URLs... |
| `content-repurposer` | Transform one long-form piece into multiple platform-specific content derivatives including LinkedIn posts, tweet threads, email... |
| `email-sequence-writer` | Write complete nurture email sequences with subject lines, preview text, and body copy using proven copywriting formulas. Use when given... |
| `google-ads-audit` | Comprehensive Google Ads account health analysis detecting wasted spend, search term leaks, negative keyword gaps, bid strategy issues,... |
| `icp-research-assistant` | Build detailed B2B buyer personas with pain points, objections, buying triggers, and messaging angles. Use when given a product and... |
| `landing-page-audit` | CRO analysis for landing pages evaluating headline clarity, CTA placement, trust signals, mobile friction, and conversion killers. Use... |
| `linkedin-ads-audit` | LinkedIn Ads campaign analysis for B2B marketers detecting CTR issues, audience quality problems, lead gen form friction, and budget... |
| `reddit-ads-audit` | Reddit Ads campaign analysis detecting community targeting issues, creative fatigue, bid inefficiencies, and subreddit performance... |
| `utm-tracking-generator` | Generate consistent UTM parameters, GA4 event naming, and conversion tracking specs following taxonomy best practices. Use when... |

### Meta Ads

| Skill | What it does |
|-------|--------------|
| `creative-fatigue-detection` | Monitors your ads for early signs of fatigue before performance fully collapses. Tracks frequency buildup, CTR decay, CPM increases, and... |
| `audience-overlap-analysis` | Compares your Meta ad sets and identifies where audiences overlap significantly, causing your ads to compete against each other in the... |
| `competitor-creative-analysis` | Pulls competitor ads from Meta Ad Library and Google Ads Transparency Center, categorizes their messaging angles, formats, CTAs, and... |
| `frequency-cap-recommendations` | Analyzes frequency data across your Meta campaigns, identifies where you're overserving ads to the same people, and recommends frequency... |
| `retargeting-window-analysis` | Analyzes your conversion lag data to determine the optimal retargeting window for each audience segment. Tells you whether your 30-day... |
| `meta-ads-audit` | Meta/Facebook/Instagram Ads campaign structure analysis detecting creative fatigue, audience overlap, scaling opportunities, and iOS... |

### SEO

| Skill | What it does |
|-------|--------------|
| `e2e-seo-assistant` | Full SEO workflow covering technical audits, content gaps, backlink opportunities, on-page fixes, and content briefs. Use when given a... |
| `programmatic-seo-builder` | Create scalable programmatic SEO page templates with title patterns, internal linking logic, schema markup, and thin content avoidance... |

### AI visibility

| Skill | What it does |
|-------|--------------|
| `ai-visibility-audit` | Audit how visible your brand is inside AI answers (ChatGPT, Claude, Gemini, Perplexity, AI Overviews). Claude builds a prompt panel for... |
| `citation-source-gap-finder` | Find the exact pages AI assistants cite when answering questions in your category, and identify which ones you can get into. Claude... |
| `content-aeo-optimizer` | Rewrite existing pages so AI assistants can extract, quote, and cite them. Claude restructures your content into answer-ready blocks —... |
| `brand-answer-monitoring` | Track how AI assistants describe your brand over time and catch wrong, outdated, or damaging claims. Claude builds your monitoring... |
