# B2X Marketing — Plugin Marketplace

Plugin marketplace for [Claude Code](https://claude.ai/claude-code) containing B2X Marketing's consulting tools.

## Installation

Add this marketplace to Claude Code (one-time setup):

```
/plugin marketplace add B2X-Marketing/b2x-plugins
```

Then install the plugins you need:

```
/plugin install strategy@b2x-plugins
/plugin install search-intelligence@b2x-plugins
```

## Available Plugins

### Strategy

Marketing consulting toolkit with 4 skills:

| Skill | Description |
|-------|-------------|
| `/strategy:marketing-strategy` | 8-layer guided strategy engagement (Golden Circle → Content Plan) |
| `/strategy:market-research` | 6-dimension market intelligence (light and deep modes) |
| `/strategy:swot-analysis` | SWOT + TOWS analysis with visual HTML matrix |
| `/strategy:voice-profile` | Voice profile management for consistent writing |

### Search Intelligence

AEO/GEO auditing suite for AI discoverability:

| Skill | Description |
|-------|-------------|
| `/search-intelligence:aeo-site-audit` | D1+D2: Technical infrastructure + citation readiness |
| `/search-intelligence:authority-distribution-audit` | D3: Authority signals + off-site distribution map |
| `/search-intelligence:ai-visibility-monitor` | D4: AI citation monitoring across ChatGPT, Perplexity, Gemini, Claude |

## Updates

Plugins update automatically when Claude Code launches. To force an update:

```
/plugin marketplace update
/plugin upgrade
```
