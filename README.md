# DSH Tailscale Troubleshooting

A Codex skill for diagnosing DeepSeek Harness web access through Tailscale and resolving confirmed trusted-host configuration problems.

The skill checks the actual service, proxy and failed API before proposing a fix. It does not contain hostnames, access tokens or machine-specific settings.

## Install

Ask Codex to install the `skills/dsh-tailscale-troubleshooting` skill from this GitHub repository, or copy that directory into `~/.codex/skills/` and restart Codex to refresh skill discovery.

## Use

Ask Codex to troubleshoot a DeepSeek Harness page that does not work over Tailscale, or invoke `$dsh-tailscale-troubleshooting` explicitly.
