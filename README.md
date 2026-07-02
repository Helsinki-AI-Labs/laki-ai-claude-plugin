# Laki.ai — Finnish & EU Law and Tax Research

A Claude plugin that connects Claude Code and Claude Cowork to
[Laki.ai](https://laki.ai)'s legal-research MCP server. It gives Claude
grounded, citable access to Finnish and EU law: Finnish statutes (with full
version history), case law (KKO, KHO, and more), preparatory works,
Verohallinto tax guidance, and collective agreements, plus EU law — the
treaties, the Charter of Fundamental Rights, and regulations and directives —
so answers come from the sources, with verbatim citations, instead of model
memory.

## Tools

The plugin adds one MCP server (`laki`) with seven research tools:

| Tool | What it does |
| --- | --- |
| `begin_research` | Starts a research session and delivers the research protocol. Always called first. |
| `search_legal_sources` | Searches Finnish statutes, case law, preparatory works, tax guidance, and collective agreements, plus EU treaties and legislation. |
| `read_document` | Reads a source with citation metadata, at section/paragraph granularity. |
| `get_table_of_contents` | Table of contents for a statute or other source. |
| `search_within_documents` | Full-text and semantic search inside specific documents. |
| `get_statute_section_history` | Version history of a statute section over time. |
| `finalize_research_graph` | Closes the session and returns the cited-source set. |

The server ships its own research instructions over the MCP protocol
(citation rules, source hierarchy, statute versioning) — the plugin adds no
prompt content of its own, so guidance is always in sync with the service.

## Requirements

- A Laki.ai account. Laki.ai is a hosted commercial service operated by
  Helsinki AI Labs Oy; a free tier is available and works with this plugin.
  Sign-in happens in your browser on first use, and you can create the
  account in that same flow.

## Install

From this repository (Claude Code):

```
/plugin marketplace add Helsinki-AI-Labs/laki-ai-claude-plugin
/plugin install laki-ai@laki-ai-plugins
```

After installing, start a new Claude Code session (or restart Claude Code) so
the plugin's `laki` MCP server is loaded.

Once accepted into the community plugin marketplace, the plugin will also be
installable with `/plugin install laki-ai@claude-community` (Claude Code) and
from [claude.com/plugins](https://claude.com/plugins) (Claude Cowork).

## Sign in (first use)

The server uses standard MCP OAuth. On the first session after installing,
Claude Code shows a notice that the `laki` server needs authentication:

1. Run `/mcp` and select **laki**.
2. Choose **Authenticate** — your browser opens for a one-time Laki.ai
   sign-in.
3. Done. Tokens are stored by Claude Code and refreshed automatically.

Non-interactive sessions (`claude -p`, Agent SDK) can't open a browser;
authenticate once in an interactive session first. If you prefer a personal
access token instead of OAuth (for example for Codex or the Anthropic API MCP
connector), see [laki.ai/headless](https://laki.ai/headless).

## Data & privacy

Research queries are processed by the Laki.ai service under your account, and
tool calls are logged to operate the service. See the
[privacy policy](https://laki.ai/fi/privacy) and
[terms](https://laki.ai/fi/terms) (both currently in Finnish).

## Support

Plugin problems (install, manifest, docs): open an issue at
[Helsinki-AI-Labs/laki-ai-claude-plugin](https://github.com/Helsinki-AI-Labs/laki-ai-claude-plugin/issues).
Laki.ai account or service questions: [info@laki.ai](mailto:info@laki.ai).

## License

[MIT](LICENSE) — covers this repository (the plugin manifest and
documentation). The Laki.ai service itself is a separate, hosted commercial
product with its own terms.
