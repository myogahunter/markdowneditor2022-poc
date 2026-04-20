# markdowneditor2022-poc

Replica of madskristensen/MarkdownEditor2022 CI workflow.

Demonstrates fork checkout + msbuild pre-build target injection:
- `pull_request_target` triggers on any fork PR (no gate, no approval)
- `build` job checks out the fork code (`pull_request.head.sha`)
- Runs `msbuild` which processes attacker-controlled `.csproj`
- Attacker adds a `PreBuild` target with `Exec` to run arbitrary commands
- `permissions: contents:write, actions:write, checks:write` on GITHUB_TOKEN

Used for authorized security research only.
