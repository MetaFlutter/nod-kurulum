---
name: nod-kurulum
description: Install the official Nod desktop app, connect it to n8n over OAuth, and verify the connection. Use for initial Nod setup, switching between local and hosted setups, or troubleshooting a failed n8n connection.
---

# Nod kurulumu / Nod setup

1. **Install Nod.** Use the [official desktop install guide](https://nod.n8n.io/docs/get-started/install-desktop/) or [official releases](https://github.com/n8n-io/nod/releases). The packaged desktop app needs neither Node.js nor Docker. Choose **Connect to a server** during onboarding only if you already operate a Nod server. That screen takes the Nod server address and token.
2. **Identify the n8n instance and account.** Open the intended n8n instance in a browser and verify the signed-in account before granting OAuth access. Use a separate browser profile if you need to keep two account sessions. A browser profile does not isolate credentials already stored in Nod.
3. **Enable MCP and connect.** Follow the [n8n MCP setup guide](https://docs.n8n.io/connect/connect-to-n8n-mcp-server/). In Nod choose **Apps → n8n → Connect**. Enter the n8n base URL reachable from the Nod server. When both services run in the same network context, the default local address is `http://localhost:5678`. A hosted Nod server or isolated container has its own localhost. See the [Nod connection guide](https://nod.n8n.io/docs/use/n8n/).
4. **Approve only the scopes required for the task.** Choose workflow read for a read-only test where offered. Add workflow write when editing is requested and execution only when needed. Scope options can vary by version. Review the account and permissions on n8n's consent page.
5. **Verify.** Check the success screen and the connected client in n8n. For read access, ask Nod to list accessible workflows. Report OAuth and workflow access separately. Verify any mobile client independently.

## Troubleshooting

- If a local server does not respond, check the n8n process and its readiness endpoint. With the default local port, PowerShell can use `Invoke-RestMethod http://127.0.0.1:5678/healthz/readiness`.
- If authorization returns `invalid_target`, check Instance-level MCP and the base URL before retrying.
- If connecting a second account, verify whether the installed Nod build supports independent connections before replacing the existing connection.
- Record product versions, connection type, and verification results. Keep credentials and account identifiers out of shared logs.
