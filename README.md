# Gentells for Claude Code

Youth culture intelligence from [Trendwolves](https://trendwolves.com), read by
your agent. The plugin carries the Gentells MCP server (trends with their
evidence, posts, reports, on your plan) and one skill, `/gentells:trends`, that
teaches the agent to cite a trend by its evidence, prefer the live window over
the archive, and use the house vocabulary.

## Install

```
claude plugin marketplace add Trendwolves/gentells-plugin
claude plugin install gentells@gentells
```

The first tool call opens gentells.com in your browser to sign in once. Any
account works; what the agent may read follows your plan, and a tool outside
your plan answers with the plan that has it.

## Without the plugin

Any MCP client connects to `https://gentells.com/mcp` (OAuth, sign in once in
the browser). Scripts use the REST API at `https://gentells.com/api/v1` with a
key from `https://gentells.com/account`. Both carry the same guidance in their
descriptions and in `https://gentells.com/llms.txt`.

## Tools

| tool | what it reads |
| --- | --- |
| `whoami` | your plan, what it opens, reads left today |
| `search_trends` | trends by words or topic, with evidence counts |
| `get_trend` | one trend in full; sources and graph where the plan includes them |
| `list_posts`, `read_post` | the posts that interpret trends for brands |
| `list_reports` | the reports and whether your plan may download them |

## License

MIT for the plugin. What it reads is Gentells' and stays under your plan's terms.
