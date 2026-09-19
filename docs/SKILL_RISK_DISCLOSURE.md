# Skill Risk Disclosure

Skills are executable workflows, not only documentation. A useful catalog should make their side effects and trust boundaries visible before installation.

This repository does not require every skill to use a machine-readable security schema yet, but new or materially changed skills should disclose the following when applicable.

## Required disclosure questions

For each skill, answer these questions in its documentation or pull request:

1. **Network access** — Does the skill access external websites, APIs, MCP servers, or other remote services?
2. **Credentials** — Does it require an API key, OAuth connection, cookie, token, or other secret?
3. **File access** — Does it read, create, modify, move, or delete local files?
4. **External actions** — Can it send messages, create issues, publish content, change remote data, or trigger other real-world side effects?
5. **Destructive actions** — Can it delete data, overwrite files, revoke access, deploy, purchase, or perform another difficult-to-reverse operation?
6. **User confirmation** — Which actions require explicit confirmation immediately before execution?
7. **Third-party dependency** — Which external service or package must remain trustworthy/available?
8. **Data handling** — What user content is sent to a third party, if any?

## Suggested risk summary

A skill may include a short section like:

```markdown
## Safety and permissions

- Network access: Yes — GitHub API
- Credentials: GitHub connection/token
- Local file writes: No
- External writes: Yes — creates issues
- Destructive actions: No
- Confirmation: Required before creating or editing remote content
- Third-party dependencies: GitHub
```

## Catalog interpretation

Risk disclosure is descriptive, not a quality score.

A networked or write-capable skill is not automatically unsafe, and a read-only skill is not automatically trustworthy. The purpose is to let users understand the permission and side-effect boundary before use.

## Contribution review

Reviewers should reject or request changes when:

- a skill performs external writes but presents itself as read-only;
- secrets are embedded in examples or committed files;
- destructive actions occur without a clear confirmation boundary;
- downloaded or page-provided instructions are treated as higher-priority commands;
- third-party content is executed without validation;
- the documentation materially understates what data leaves the user's environment.

The catalog should prefer explicit, minimal permissions over broad permissions that are not required for the documented workflow.
