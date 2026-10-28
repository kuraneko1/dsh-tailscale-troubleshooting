---
name: dsh-tailscale-troubleshooting
description: Diagnose and repair DeepSeek Harness web access through Tailscale, including API 403 errors, trusted host settings, reverse proxies, and WebSocket failures. Use when a DSH page fails to load or connect through a Tailscale URL.
---

# DeepSeek Harness and Tailscale access

Identify the actual failing request and service before making changes. A rendered page alone does not prove that its APIs or WebSocket work. Distinguish different ports and services, and do not assume every 403 has the same cause.

1. Inspect the reported browser error and URL, without displaying tokens, cookies, or credentials. Check DNS, TCP, HTTPS, Tailscale status and `tailscale serve status` as appropriate. Identify the proxy destination and the process listening there; inspect its command, service manager and environment carefully, avoiding secret disclosure. A temporary test instance may be unrelated to a long-running service.
2. Compare the same API endpoint on loopback and through the Tailscale URL. Where useful, test the loopback endpoint with the external Host header. If loopback succeeds but the external Host yields 403, inspect the installed DSH version's host/Origin trust documentation or implementation before attributing the failure to `trustedHosts`. A 401 or other response may instead indicate authentication or a different issue. WebSocket, browser cookies, Origin, proxy configuration and Tailscale access can also fail independently.
3. If the host trust fence is the confirmed cause and the user wants a fix, add only the actual external `host:port` using the supported `--trusted-host` option or the equivalent configuration for the installed version. Keep authentication enabled; do not bypass trust checks, expose the service publicly, bind wildcard interfaces, or change unrelated services. Preserve existing startup arguments and environment. Place persistent settings in the actual service or startup script only if applicable and requested; do not imply a command-line change persists after the process exits.
4. Determine whether a restart would interrupt active work or affect a temporary instance. Respect existing user authorization; when the impact is unclear and consequential, explain it and ask before interrupting. Preserve existing configuration and provide rollback where changes are made.
5. Verify the external API, authentication and WebSocket or functional browser state. A successful HTML response alone is insufficient. If a restart changes the token, obtain the new link from the service securely and share it only with the user; never include credentials in logs, committed files or diagnostic output. Explain any remaining workspace errors and whether the fix persists across restarts.
