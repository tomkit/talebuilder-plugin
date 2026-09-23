# TaleBuilder for AI assistants

Make children's picture books from Claude, ChatGPT, Gemini, Grok and other AI assistants. Describe an idea ("a shy owl who wants to sing in the forest choir, for a first grader") and [TaleBuilder](https://www.talebuilder.com) writes a ten-page story, draws the characters and the cover as a free preview, and can then illustrate every page.

For parents. Books are made on your TaleBuilder account: you sign in once when you connect, and every book shows up in your library on talebuilder.com.

**Server URL:** `https://www.talebuilder.com/api/mcp` (remote MCP, Streamable HTTP, OAuth sign-in)

## Tools

| Tool | What it does | Cost |
| --- | --- | --- |
| `create_preview` | Writes the story and draws the characters and cover from an idea, a theme and a grade (K to 5) | Free, up to 3 a day |
| `get_story` | Shows a book by title words or id: progress, the storyboard, and the whole book to read in the chat where the app supports panels | Free, read-only |
| `finish_story` | Illustrates every page of a ready preview | 11 acorns (a new account's sign-up bonus covers the first book) |
| `list_my_stories` | Your 20 most recent books | Free, read-only |

A preview takes about 3 to 4 minutes; finishing a book takes about 8. The tools return right away with a link where you can watch the book being made.

## Connect

You sign in to TaleBuilder in your browser the first time the assistant uses a tool. New here? You can create an account on that page.

### Claude (claude.ai, Claude Desktop)
Settings, then Connectors, then **Add custom connector**. Paste `https://www.talebuilder.com/api/mcp` and connect.

### Claude Code
As a plugin:
```
/plugin marketplace add tomkit/talebuilder-plugin
/plugin install talebuilder@talebuilder
```
Or directly:
```
claude mcp add --transport http talebuilder https://www.talebuilder.com/api/mcp
```
Then run `/mcp` and choose TaleBuilder to sign in.

### ChatGPT
Turn on Developer mode (Settings, then Security and login), then add a plugin with the server URL. Developer mode is available on the plans OpenAI lists in its [developer mode guide](https://help.openai.com/en/articles/12584461).

### Gemini
- **Gemini app:** add `https://www.talebuilder.com/api/mcp` as a custom MCP connection under Connected Apps (Google currently offers this in the US, in English, for personal accounts 18 and over).
- **Gemini CLI:** `gemini extensions install https://github.com/tomkit/talebuilder-plugin`

### Grok
On grok.com, open Connectors, choose **New Connector**, then **Custom**, and paste the server URL.

### Cursor
[Add TaleBuilder to Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=talebuilder&config=eyJ1cmwiOiJodHRwczovL3d3dy50YWxlYnVpbGRlci5jb20vYXBpL21jcCJ9)

### VS Code
Add to `.vscode/mcp.json`:
```json
{
  "servers": {
    "talebuilder": { "type": "http", "url": "https://www.talebuilder.com/api/mcp" }
  }
}
```

### Any other MCP client
Use `https://www.talebuilder.com/api/mcp` with Streamable HTTP. Sign-in is OAuth 2.1 with dynamic client registration and PKCE; the client discovers it from the `401` response.

## What is in this repository

Only packaging; the server runs at talebuilder.com.

| File | For |
| --- | --- |
| `plugin.json`, `mcp.json` | OpenAI plugins ([Agent Plugins](https://agent-plugins.org) format) |
| `.claude-plugin/`, `.mcp.json` | Claude Code plugin and marketplace |
| `gemini-extension.json`, `GEMINI.md` | Gemini CLI extension |
| `server.json` | [MCP Registry](https://registry.modelcontextprotocol.io) |
| `assets/` | Icon and logo |

## Privacy and terms

[Privacy Policy](https://www.talebuilder.com/privacy) and [Terms of Service](https://www.talebuilder.com/terms). TaleBuilder is operated by Menlo Labs.

## Support

support@talebuilder.com
