# SentiSense

**Ask your agent about the market and get a real answer.**

This plugin connects your agent to SentiSense, a read-only market intelligence service
covering roughly 960 of the most-watched US stocks and ETFs.

Ask what the market mood is today. Ask whether the crowd has turned bullish on a stock.
Ask what Congress bought last week, which institutions are adding to a position, whether
insiders are selling their own shares, where implied volatility sits against its own
history, or when a company next reports. Your agent picks the right tool and answers
inline, with the sources attached.

## Install

1. Open **Settings, then Plugins**.
2. Search for **SentiSense**.
3. Select **Install**, then complete the SentiSense sign-in prompt.

Or run `/add-plugin stock-market-data` in chat.

## Configuration

There is none. Auth is OAuth against SentiSense with Dynamic Client Registration and
PKCE: your agent registers itself and prompts you to sign in the first time it connects.
There is no API key to paste and no client id to configure.

Free accounts see preview data across every tool. A SentiSense account upgrade unlocks
full payloads through the same connection, with nothing to reconfigure here.

## MCP

```json
{
  "mcpServers": {
    "sentisense": {
      "type": "http",
      "url": "https://app.sentisense.ai/mcp"
    }
  }
}
```

Ten read-only tools: market mood, stock snapshot with sentiment and the SentiSense Score,
stock screening, sentiment-tagged news, options intelligence, the earnings calendar,
reported financials, analyst ratings and price targets, smart-money trades from SEC
filings (insider, institutional and congressional), and a connection health check.

Nothing is ever written, moved, or traded. Every tool is read-only, and the plugin has no
trading, ordering, or wallet surface of any kind.

## Skills

Six bundled skills add the workflows on top of the raw tools.

| Skill | What it does |
|:------|:-------------|
| `0-sentisense-onboarding` | Read first. Routes a question to the skill that owns it. |
| `stock-terminal` | Turns chat into a financial terminal. Short commands like `open NVDA` or `daily brief` return one composite screen. |
| `stock-sentiment` | The signal read: what the market feels about a stock and where the smart money is moving. |
| `stock-market-dashboard` | Writes a morning market briefing as a single self-contained HTML file you can keep and open offline. |
| `politicians-stock-tracker` | Congressional STOCK Act disclosures: who traded what, in which chamber, and how late they disclosed it. |
| `stocks-analysis` | An adversarial investment committee. Investor personas research a thesis, attack each other's cases against a shared evidence ledger, and reconcile into a verdict with recorded dissents. |

The full collection, including insider trading, institutional 13F, options, earnings and
screener skills, lives at [SentiSenseApp/skills](https://github.com/SentiSenseApp/skills)
and installs with `npx skills add SentiSenseApp/skills`.

## Data notes

- Coverage is roughly 960 of the most-watched US stocks and ETFs, not the whole market.
- Prices are delayed. Sentiment, market mood and news annotations are recomputed on a
  regular cadence rather than streamed.
- Congressional and insider data comes from official filings, so it carries the
  disclosure lag those filings are allowed by law.

## Disclaimer

For informational and educational purposes only. Nothing produced through this plugin is
investment advice, a personalized recommendation, or a solicitation to buy or sell any
security. You are responsible for your own decisions.

## Links

- Website: https://sentisense.ai
- API reference: https://sentisense.ai/skill.md
- Free account: https://app.sentisense.ai/get-api-key

## License

MIT
