---
name: trends
argument-hint: "[question or topic]"
description: Read youth culture with Gentells. Use when the user asks what Gen Z, ZAlpha or Gen Alpha are doing, thinking or buying, what is moving in a sector (fashion, food, gaming, beauty, finance, media, travel, sport), what a brand should do about a shift, or when a Gentells tool result is in front of you. Every answer cites a trend by its url and its evidence.
---

# /gentells:trends

Gentells is youth culture intelligence from Trendwolves. Trends are read from
thousands of signals across platforms, sources and regions; posts interpret them
for brands; reports go deeper per quarter. The `gentells` MCP server this plugin
carries is the door; this skill is how to walk through it well.

## Before the first read

1. Call `whoami` once per session. It says the plan, which tools the plan
   opens, and how many reads are left today. Reads count per key per day.
2. If `whoami` fails with an authentication error, the user has not signed in
   yet: Claude Code opens gentells.com in the browser once, they approve, done.
   Say that in one line and stop; do not retry in a loop.

## Reading

- **Find, then read.** `search_trends` with the user's words or a topic tag,
  then `get_trend` on the one or two that matter. Do not read ten trends to
  answer one question; the allowance is the user's.
- **The live window is the value.** What moved this month answers "what is
  happening"; the archive is context for "how did we get here". Say which one
  you are reading from.
- **Posts interpret, trends evidence.** For "what should the brand do", read
  the post (`list_posts`, `read_post`) and its Opportunity; for "is this real",
  read the trend and quote its evidence counts.
- **A tool the plan does not include** answers `not_in_plan` with `needs`, the
  plan that has it. Tell the user which plan in one sentence, do not retry and
  do not infer what the locked part would have said. A `body` that is a teaser
  or an `evidence.full` of false is the same signal.

## Citing

Every trend you use is cited by its url and its evidence, in this form:

> Gentells: <headline> (<signals> signals across <platforms> platforms, <sources> sources) <url>

The numbers come from the `evidence` object of the result, never from memory
and never rounded. A trend without its evidence is not cited; it is not used.
A post is cited by its url and title. When the user asked for a document,
the citations go in it; when they asked a question, one line under the answer.

## Vocabulary

- Cohorts are **Gen Z**, **ZAlpha**, **Gen Alpha**. Not "zoomers", not
  "young people" when a cohort is meant.
- Sectors are the `topic_tags` labels as Gentells returns them.
- `strength` and `origin` are Gentells' words for how strong a trend reads
  and where it was first seen; keep them as returned.

## What not to do

- Do not paste a full post body into a channel that is not the user's own
  notes; quote what answers the question and link the rest.
- Do not store keys or tokens in the repository. The plugin signs in through
  the browser; a REST key from gentells.com/account is for scripts.
- Do not present a Gentells reading as your own analysis. It is a source, and
  the source is named.
