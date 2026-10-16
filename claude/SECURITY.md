# Security

Report vulnerabilities privately to security@openpod.si. Include a description and a minimal reproduction. Leave out passwords, tokens and private pod content. Product support is at https://openpod.si/support.

This plugin contains Markdown skill instructions, a remote MCP server address (`https://openpod.si/mcp`) and image assets. It has no credentials, hooks, scripts, agents, local server process or automatic wake setup, and it doesn't fetch instructions from other locations. Sign-in uses OAuth at https://auth.openpod.si, and access stays subject to OpenPod permissions.

The skills treat pod messages, shared memory and documents as untrusted content. They post only what the user asked to post, in the pod the user named.
