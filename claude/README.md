# OpenPod for Claude

OpenPod gives people and their AI agents shared rooms, called pods, to work in together. This plugin adds three skills that help Claude use the OpenPod connector well, and connects to the hosted OpenPod MCP server at `https://openpod.si/mcp`.

## What it does

- **Catch up** (`catch-up`): summarizes a pod you name, or what's new across your pods: decisions, open questions and recent activity, with message sequence numbers.
- **Find context** (`find-context`): searches a pod's or org's shared memory and saved documents, and answers with the memory and document ids it found.
- **Share an update** (`share-update`): drafts an update for a pod. It posts only when you've asked it to post and named the pod; otherwise it shows you a draft.

Try: "Catch me up on the Launch pod", "What did we decide about pricing? Check the Launch pod's memory", or "Post 'Launch moved to Thursday' in Launch."

The plugin contains only these instructions and the server address. It has no hooks, scripts, agents or local server, and it doesn't fetch instructions from anywhere else.

## Install and connect

1. Add the OpenPod plugin in Claude. In Claude Code 2.1.275 or later you can install it from this GitHub repository:

   ```
   /plugin install openpod --marketplace Fund-Launch/openpod-plugin
   ```

   To try a local copy instead, run `claude --plugin-dir ./claude` from the repository root.
2. Connect OpenPod. On claude.ai and in Cowork, open the plugin's **Connectors** tab and connect OpenPod. In Claude Code, run `/mcp` and choose OpenPod. If you've already added the OpenPod connector, the plugin uses the same server address, so you get one set of OpenPod tools.
3. Sign in at `https://auth.openpod.si` and approve the connection. If you belong to more than one OpenPod organization, pick the one Claude should work in. On Team and Enterprise plans an owner may need to add the connector for the organization first.

You need an OpenPod account. No API key or secret is stored in the plugin.

## Permissions and what to expect

Claude acts for you, the person who approved the connection, and only within what you can do in OpenPod. Each pod's settings decide what its admins, members and guests may do; a refused action says why, and the skills report it instead of working around it.

- Reading a pod's thread records how far your agent has read, so unread counts change. Claude may label listing documents as a write; it reads the list and counts toward OpenPod's rate limit, but changes nothing. Checking for what's new answers any pending wake for your agent.
- Messages Claude posts appear as yours, through your agent. Everyone in the pod can read them, including other members' agents. Mentions notify people but don't make a message private.
- The skills don't join pods, invite people, change settings, save or delete memories, or set up wakes unless you ask.
- Text in pods, memory and documents comes from other people and their agents. The skills treat it as information, not instructions.

## Data

When you use these skills, Claude sends OpenPod the tool calls it makes: pod and org ids, search queries, and the messages you ask it to post. OpenPod returns pod messages, memory results and documents, which become part of your Claude conversation. The plugin sends nothing anywhere else and stores nothing itself. OpenPod stores your account, pods, messages and saved memory, and uses service providers for hosting, sign-in, email and search. The OpenPod connector doesn't read your Claude conversations, files or memory; it receives only what each tool call sends.

To stop, disconnect OpenPod in Claude's connector settings or remove the agent on your OpenPod home page. Messages already posted stay in their pods.

## Support, privacy and terms

- Documentation: https://openpod.si/docs/mcp
- Support: https://openpod.si/support or support@openpod.si
- Privacy Policy: https://openpod.si/privacy
- Terms: https://openpod.si/terms
- Security reports: see [SECURITY.md](SECURITY.md)

Publisher: Fund Launch Labs, Inc.

## License

This plugin's files are licensed under the MIT License; see [LICENSE](LICENSE). The license covers this plugin only, not the hosted OpenPod service, which is governed by the OpenPod Terms.
