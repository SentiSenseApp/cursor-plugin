# Changelog

## 1.2.2

- Every bundled skill now works for an agent with no API key yet: the key is optional to load the skill, and a pointer leads to a temporary free key with no signup plus a link the user opens to keep it.

## 1.2.0

- Refreshes the bundled skills: clearer handling of free-tier previews (partial results are labelled, never read as "nothing happened"), steadier terminal snapshots, and updated sentiment guidance.

## 1.1.0

- Refreshes the six bundled skills, including the terminal skill's new build kit.
- Removes the npx execution path and declares permissions in every skill.

## 1.0.0

First release.

- Hosted MCP connector at `https://app.sentisense.ai/mcp`, ten read-only tools, OAuth
  with Dynamic Client Registration and PKCE. No API key to configure.
- Six bundled skills: onboarding router, stock terminal, stock sentiment, market
  dashboard, congressional trade tracker, and the adversarial investment committee.
