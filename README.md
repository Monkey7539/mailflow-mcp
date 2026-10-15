# mailflow-mcp

An MCP server that lets Claude, and other MCP clients, work with the mail in a self-hosted [MailFlow](https://github.com/maathimself/mailflow): search and read it, organize it, and draft replies for you to send.

This is an independent companion project, not part of MailFlow. It talks to MailFlow only through MailFlow's HTTP API, using a MailFlow API token. Moves, folders and drafts therefore go through MailFlow's own handling, and nothing here touches IMAP or MailFlow's database directly.

## Status

In development. It depends on API tokens in MailFlow, which are proposed in [maathimself/mailflow#617](https://github.com/maathimself/mailflow/issues/617). Until a MailFlow release includes them, this server needs a MailFlow build that has the token feature.

## What it will do

- **Read:** list accounts and folders, list and search messages, and read a message or a thread.
- **Organize:** mark read or unread, star, archive, snooze, set a category, and move messages, though never into Trash or Junk.
- **Draft:** save a new message or a reply to Drafts, for you to review and send in MailFlow.

It can't send mail, delete it or empty folders. Email content it returns is marked as untrusted, because a message can contain instructions aimed at the AI reading it. What a given token can do is set by the scopes you give it in MailFlow.

## Ways to run it

- **stdio:** Claude Desktop or Claude Code starts it on your own computer, and it calls your MailFlow over HTTPS.
- **Streamable HTTP:** a small service next to MailFlow, for remote MCP clients such as claude.ai custom connectors. Each request's bearer token is passed through to MailFlow.

Setup instructions will come with the first release.

## License

[MIT](LICENSE)
