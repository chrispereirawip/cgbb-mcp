# CGBB · Council for Global Brand Building — remote MCP server and API

**Free trust.json for any brand's website: a quick GEO and AI-trust win.**

The [Council for Global Brand Building](https://cgbb.org) (CGBB, 品信會) offers brands free membership and a signed **CGBB Member trust.json**. Published at `https://yourdomain.com/.well-known/trust.json`, it lets any AI agent check, with one request to the CGBB registry, that the website belongs to a real organisation reviewed by the CGBB Secretariat and that the organisation controls the domain.

AI agents can apply on a brand's behalf through this remote MCP server or the HTTP API. A real person at the brand confirms by email, and the Secretariat reviews every application.

- Why it matters for GEO and AI visibility: https://cgbb.org/ai-trust/ (繁中: https://cgbb.org/zh/ai-trust/)
- Full guide for AI agents: https://cgbb.org/agents/
- Instructions for agents: https://cgbb.org/llms.txt

## Connect

| | |
|---|---|
| MCP server (remote) | `https://api.cgbb.org/mcp` |
| Transport | Streamable HTTP |
| Authentication | None |
| MCP Registry name | `org.cgbb/cgbb` |
| OpenAPI | https://api.cgbb.org/openapi.json |
| Agent card | https://cgbb.org/.well-known/agent-card.json |

Claude, ChatGPT, Cursor and other MCP clients: add a custom connector with the URL above.

```json
{
  "mcpServers": {
    "cgbb": { "type": "http", "url": "https://api.cgbb.org/mcp" }
  }
}
```

## Tools

| Tool | What it does |
|---|---|
| `about_cgbb` | What CGBB is, what the free trust.json contains, how it supports a brand's GEO and AI trust, and how to apply |
| `apply_for_membership` | Apply for free CGBB membership on behalf of a brand; returns an application id, a domain-verification token and next steps |
| `check_domain_verification` | Check the domain token (DNS TXT record or `/.well-known/cgbb-verification.txt`) |
| `get_application_status` | Status and next steps for an application |
| `verify_brand` | Live CGBB record for a domain, and whether a genuine trust.json is published |
| `get_trust_file` | The signed CGBB Member trust.json for an approved domain |

## Steps

1. Apply (`apply_for_membership`) with the brand's own domain and a real person's work email.
2. The brand publishes the domain token, and the contact person clicks CGBB's confirmation email. Then call `check_domain_verification`.
3. After Secretariat approval (usually a few business days), call `get_trust_file` and publish the file at `/.well-known/trust.json`.

Anyone can check a file at `https://api.cgbb.org/verify/{domain}`. Files are signed with Ed25519 over canonical JSON; public keys: https://api.cgbb.org/.well-known/cgbb-keys.json

## What the free level means

The CGBB Member level confirms approved membership and domain control. It is not a certification, rating or endorsement of products, services or conduct. Trust scores come only with the paid comprehensive Trust Review (CGBB Verified Trusted level): https://cgbb.org/upgrade/

## Contact

secretariat@cgbb.org · Privacy: https://cgbb.org/privacy/
