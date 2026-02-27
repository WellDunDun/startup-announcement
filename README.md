# Startup Announcement Planner

A Claude skill that helps founders turn announcements into coordinated distribution systems — not just blog posts.

Based on [Anatomy of an Announcement](https://x.com/allisonbraley/status/2027098454439379412) by [Allison Braley](https://x.com/allisonbraley), Partner at Bain Capital Ventures.

> <a href="https://x.com/allisonbraley/status/2027098454439379412"><img src="https://img.shields.io/badge/Read_the_original-@allisonbraley_on_𝕏-000000?style=for-the-badge&logo=x&logoColor=white" alt="Read the original on X" /></a>

The full article is also included in [`references/anatomy-of-an-announcement.md`](references/anatomy-of-an-announcement.md).

## What it does

This skill walks founders through a four-step process for any startup announcement — funding rounds, product launches, coming out of stealth, or milestones:

1. **Pick one audience** — customers, talent, or investors. Not all three.
2. **Craft the message** — headline that names the change (not the product), narrative paragraph, three skeptic-proof proof points.
3. **Plan distribution** — 1 owned asset + 1 earned amplifier + 1 social post, synchronized in a tight window. Evaluate media on both reach and depth.
4. **Execute** — timeline adapted to your constraints, amplification network with specific timing asks.

The output is a complete plan document plus ready-to-use content drafts: blog post, headline options, social post, amplification ask, and media pitch.

## Install

```bash
npx skills add WellDunDun/startup-announcement
```

## What the skill prevents

Without this skill, Claude defaults to patterns the article explicitly warns against:

- **Product-first openings** — "Today we're launching X" instead of leading with the problem
- **"Introducing X" headlines** — naming the product instead of naming the change
- **No trap awareness** — not warning founders about the corporate PR / AI slop / feature dump pitfalls
- **Shallow media evaluation** — listing publications without evaluating the reach vs. depth tradeoff

## Benchmark results

Tested across 4 scenarios with 11 strategic-quality assertions each (44 total). Each assertion tests a specific principle from the article — not just "does a section exist" but "does the headline name the change, not the product?"

| | With Skill | Without Skill | Delta |
|---|---|---|---|
| **Pass Rate** | 100% (44/44) | 72.7% (32/44) | **+27.3%** |
| **Avg Time** | 308s | 445s | -136s |
| **Avg Tokens** | 36K | 37.5K | -1.5K |

### Most discriminating assertions

| Assertion | Without-Skill Failure Rate | What happens without the skill |
|---|---|---|
| Explicit trap awareness | 3/4 evals failed | Claude doesn't proactively name pitfalls to avoid |
| Blog opens with problem, not product | 2/4 evals failed | Defaults to "Today we're launching..." |
| Headlines name the change | 2/4 evals failed | Falls into "Introducing [Product]" pattern |
| Media evaluated on reach AND depth | 1/4 evals failed | Lists outlets without evaluating the tradeoff |

### Test scenarios

| Eval | Scenario | With Skill | Without Skill |
|---|---|---|---|
| seed-cyber | $6M seed, AI threat detection, targeting CISOs | 11/11 | 8/11 |
| devtools-recruiting | Open-source observability tool, recruiting engineers, 1-week timeline | 11/11 | 7/11 |
| stealth-fintech | Coming out of stealth, payments for SMBs, zero budget | 11/11 | 7/11 |
| solo-ai-builder | Solo AI founder, audience mismatch (X followers vs. B2B ICP) | 11/11 | 10/11 |

### View full results

Open `evals/viewer.html` in your browser to see the complete outputs, assertion grades, and side-by-side comparisons for every test case.

## Evals

The `evals/` directory contains everything you need to run your own benchmarks or modify the assertions:

- **`evals.json`** — 4 test prompts with 44 strategic-quality assertions
- **`viewer.html`** — standalone HTML viewer with outputs, grades, and benchmark data

### Assertion philosophy

The assertions test the article's strategic principles, not structural presence. For example:

- **Not this**: "Does the plan include a blog post draft?"
- **This**: "Does the blog post open with the audience's problem, not a product description?"

This matters because Claude naturally produces well-structured plans. The skill's value is in enforcing strategic quality — problem-first framing, change-naming headlines, explicit trap awareness, and reach-vs-depth media evaluation.

## Modify and contribute

Fork the repo, edit `SKILL.md`, and re-run the evals to test your changes. The assertions in `evals/evals.json` are designed to catch regressions in strategic quality.

## License

MIT
