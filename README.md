# Virlo Plugin for Grok Build

Give Grok a social media brain. Ask what is trending on TikTok, YouTube Shorts, or Instagram
Reels and get live data back: emerging trends, viral videos ranked by weighted virality instead
of raw views, creator profiles with outlier videos and audience demographics, breakout sounds,
trending hashtags, and proven opening hooks. Grok can also start research agents that study a
niche once, or keep watching it on a schedule and report what changed.

This plugin connects Grok Build to [Virlo](https://virlo.ai)'s hosted MCP server. Built for
content marketers, social media operators, agencies, founders, and creators who work on organic
short-form video and want the data in the conversation instead of in another tab.

## Install

1. Install Grok Build and sign in (see the [Grok Build docs](https://docs.x.ai/build/overview)).
2. Start `grok`, run `/marketplace`, find **virlo**, and press `i` to install. Or from a terminal:

   ```bash
   grok plugin install virlo --trust
   ```

3. Open the MCP servers tab with `/mcp`, select **virlo**, and press `i` to sign in. Your browser
   opens the Virlo sign-in page. Sign-in is OAuth, so there is no API key to create, paste, or
   store. You can create a Virlo account during sign-in.
4. Once **virlo** shows ready, ask Grok anything about short-form video.

## What is in the plugin

| Component | Path | Purpose |
|---|---|---|
| MCP server | `.mcp.json` | Virlo's hosted server over HTTPS |
| Skill | `skills/virlo/SKILL.md` | Tool routing, credit costs, async job polling, weighted virality |
| Skill | `skills/short-form-trend-research/SKILL.md` | Turns trend data into a content plan |
| Commands | `commands/` | Four slash commands (below) |

There are no hooks, agents, scripts, or local binaries.

## Commands

| Command | What it does |
|---|---|
| `/virlo:trend-scout` | What is trending right now across all three platforms |
| `/virlo:niche-analysis` | Full niche workup: research agent, creators, recurring monitor |
| `/virlo:creator-deep-dive` | One creator's outlier videos, cadence, and audience |
| `/virlo:genre-monitor` | Stand up a recurring monitor for a genre or scene |

## Example prompts

```text
What is trending on TikTok in the home fitness niche this week?
Analyze this TikTok video and tell me why it went viral.
Look up this creator and show me their outlier videos and audience.
Start a research agent on the AI productivity niche and keep watching it.
```

## What this plugin does, exactly

Disclosed in full so you can judge it before installing.

- **It connects to one endpoint and nothing else:** Virlo's hosted MCP server at
  `https://dev.virlo.ai/api/mcp/mcp`, over HTTPS. There is no other network destination, no
  telemetry, and no analytics.
- **It runs no local code.** The plugin ships skills, commands, and one remote MCP server
  declaration. It contains no hooks, no scripts, no executables, and no `bin/` directory. It does
  not read or write files on your machine.
- **It authenticates as you, through OAuth.** The plugin never reads an environment variable,
  never asks for a key, and never handles a credential itself. Your Virlo session is held by the
  client, and Virlo's authorization server issues it.
- **It reads public social data.** It does not post, comment, follow, or connect to your own
  TikTok, YouTube, or Instagram accounts. It has no write access to any social platform.
- **It spends Virlo credits.** Research agents, creator lookups, video analysis, and some trend,
  hashtag, and sound reads bill against your Virlo balance per call. The `virlo` skill tells Grok
  to check your balance and quote the expected cost before any paid run, and to get your
  go-ahead before creating a recurring agent, because a recurring agent bills on every run.
  Credits are purchased on virlo.ai, never inside Grok.

## Costs and billing

Virlo is pay-as-you-go against a prepaid balance. Reads of results you already created are free.
Starting new work costs credits, and so do instant data reads (trends, sounds, hooks, hashtags),
even when they come back empty. To see what one call cost, ask Grok to compare your balance
before and after it. Live per-tool pricing is at [dev.virlo.ai/docs/mcp](https://dev.virlo.ai/docs/mcp).

## Links

- Product: [virlo.ai](https://virlo.ai)
- MCP docs and tool reference: [dev.virlo.ai/docs/mcp](https://dev.virlo.ai/docs/mcp)
- Support: [virlo.ai/support](https://virlo.ai/support)
- Privacy: [virlo.ai/legal/privacy-policy](https://virlo.ai/legal/privacy-policy)
- Terms: [virlo.ai/legal/terms-of-service](https://virlo.ai/legal/terms-of-service)

## License

MIT. See [LICENSE](./LICENSE).
