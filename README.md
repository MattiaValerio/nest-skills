# NestJS Best Practices Skills

[![skills.sh](https://skills.sh/b/mattiavalerio/nest-skills)](https://skills.sh/mattiavalerio/nest-skills)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Rules](https://img.shields.io/badge/rules-40-green.svg)](skills/nestjs-best-practices/rules)

**40 NestJS best-practice rules for AI coding agents** (Claude Code, Codex, Cursor, OpenCode and more). Each rule has an incorrect and a correct code example, so agents write idiomatic, secure, testable NestJS instead of guessing.

Installable alongside other skill sets such as [mattpocock/skills](https://github.com/mattpocock/skills).

## Installation

Install with [skills](https://github.com/vercel-labs/skills):

```bash
# This repo
npx skills add mattiavalerio/nest-skills

# Globally (available in every project), or for specific agents
npx skills add mattiavalerio/nest-skills --global
npx skills add mattiavalerio/nest-skills -a claude-code -a cursor
```

To use it together with Matt Pocock's skills, install both. They do not conflict: this repo only adds `nestjs-best-practices`.

```bash
npx skills add mattpocock/skills
npx skills add mattiavalerio/nest-skills
```

### Supported agents

Claude Code, OpenCode, Codex, Cursor, Antigravity, Roo Code, and any other agent supported by [skills](https://github.com/vercel-labs/skills).

## What it covers

| Category | Impact | Examples |
|----------|--------|----------|
| Architecture | CRITICAL | feature modules, circular dependencies, repository pattern, events |
| Dependency Injection | CRITICAL | constructor injection, provider scopes, injection tokens, SOLID |
| Error Handling | HIGH | exception filters, HTTP exceptions, async errors |
| Security | HIGH | JWT auth, guards, input validation, rate limiting, XSS |
| Performance | HIGH | caching, query optimization, lazy loading, async hooks |
| Testing | MEDIUM-HIGH | Testing module, Supertest e2e, mocking external services |
| Database & ORM | MEDIUM-HIGH | transactions, N+1 queries, migrations |
| API Design | MEDIUM | DTOs and serialization, interceptors, pipes, versioning |
| Microservices | MEDIUM | message/event patterns, health checks, queues |
| DevOps | LOW-MEDIUM | ConfigModule, structured logging, graceful shutdown |

The full compiled guide is in [AGENTS.md](AGENTS.md), and each rule lives in [`skills/nestjs-best-practices/rules/`](skills/nestjs-best-practices/rules).

## Usage

The skill loads on its own when the agent works on NestJS code. You can also ask for it directly:

- "Add an orders module following the NestJS best practices."
- "Review this controller against the nestjs-best-practices rules."
- "Refactor this service to remove the circular dependency."

### Using it with other skills

Agents pick skills from their descriptions. `nestjs-best-practices` is model-invoked and its description matches NestJS work, so it loads when you (or a workflow skill such as `tdd` or `code-review`) touch NestJS code. To make that explicit in a project, add this to the project's `AGENTS.md` or `CLAUDE.md`:

```markdown
## Agent skills

This is a NestJS project. Whenever you write, test, review or refactor code here,
including while following another skill's workflow, also apply the
`nestjs-best-practices` skill and read the rule files relevant to the change.
```

## Repository structure

- `skills/nestjs-best-practices/` - The installable skill (this is what `skills add` copies into your project)
  - `SKILL.md` - Skill entry point and quick reference
  - `rules/` - Individual rule files (one per rule)
    - `_sections.md` - Section metadata (titles, impacts, descriptions)
    - `_template.md` - Template for creating new rules
    - `area-description.md` - Individual rule files
- `scripts/` - Build script that compiles the rules
- `metadata.json` - Document metadata (version, organization, abstract)
- `AGENTS.md` - Compiled guide (generated, do not edit by hand)

## Contributing

### Creating a new rule

1. Copy `skills/nestjs-best-practices/rules/_template.md` to `skills/nestjs-best-practices/rules/area-description.md`
2. Choose the area prefix:
   - `arch-` Architecture
   - `di-` Dependency Injection
   - `error-` Error Handling
   - `security-` Security
   - `perf-` Performance
   - `test-` Testing
   - `db-` Database & ORM
   - `api-` API Design
   - `micro-` Microservices
   - `devops-` DevOps & Deployment
3. Fill in the frontmatter and content, with clear incorrect and correct examples
4. Regenerate `AGENTS.md` (see below)

### Rule file structure

````markdown
---
title: Rule Title Here
impact: MEDIUM
impactDescription: Optional description
tags: tag1, tag2, tag3
---

## Rule Title Here

Brief explanation of the rule and why it matters.

**Incorrect (description of what's wrong):**

```typescript
// Bad code example
```

**Correct (description of what's right):**

```typescript
// Good code example
```

Reference: [NestJS Documentation](https://docs.nestjs.com)
````

### Conventions

- Files starting with `_` are special and excluded from the build
- Rule files are named `area-description.md` (for example `arch-avoid-circular-deps.md`)
- The section is inferred from the filename prefix
- Rules are sorted alphabetically by title within each section, and IDs (1.1, 1.2, ...) are generated during the build

### Impact levels

| Level | Description |
|-------|-------------|
| CRITICAL | Violations cause runtime errors, security vulnerabilities, or architectural breakdown |
| HIGH | Significant impact on reliability, security, or maintainability |
| MEDIUM-HIGH | Notable impact on quality and developer experience |
| MEDIUM | Moderate impact on code quality and best practices |
| LOW-MEDIUM | Minor improvements for consistency and maintainability |

### Building

```bash
cd scripts && npm install
npm run build   # or ./build.sh
```

This compiles the rules into the root `AGENTS.md`.

## Acknowledgments

- Structure inspired by the [Vercel React Best Practices](https://github.com/vercel-labs/agent-skills) skill
- Installation via [skills](https://github.com/vercel-labs/skills)

## License

[MIT](LICENSE)
