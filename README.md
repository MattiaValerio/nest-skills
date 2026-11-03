# NestJS Best Practices Skills

[![skills.sh](https://skills.sh/b/mattiavalerio/nest-skills)](https://skills.sh/mattiavalerio/nest-skills)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Rules](https://img.shields.io/badge/rules-40-green.svg)](skills/nestjs-best-practices/rules)

**40 NestJS best-practice rules for AI coding agents** (Claude Code, Codex, Cursor, OpenCode and more). Each rule has an incorrect and a correct code example, so agents write idiomatic, secure, testable NestJS instead of guessing.

Installable alongside other skill sets such as [mattpocock/skills](https://github.com/mattpocock/skills).

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

## Installation

Install with [skills](https://github.com/vercel-labs/skills):

```bash
# This repo
npx skills add mattiavalerio/nest-skills

# Alongside Matt Pocock's skills
npx skills add mattpocock/skills

# Globally, or for specific agents
npx skills add mattiavalerio/nest-skills --global
npx skills add mattiavalerio/nest-skills -a claude-code -a cursor
```

The skills are installed side by side with no conflicts: this repo only adds `nestjs-best-practices`.

### Making other skills use it

Agents pick skills from their descriptions. `nestjs-best-practices` is model-invoked and its description matches NestJS work, so it loads when you (or a workflow skill such as `tdd` or `code-review`) touch NestJS code. To make that explicit in a project, add this to the project's `AGENTS.md` or `CLAUDE.md`:

```markdown
## Agent skills

This is a NestJS project. Whenever you write, test, review or refactor code here,
including while following another skill's workflow, also apply the
`nestjs-best-practices` skill and read the rule files relevant to the change.
```

### Supported Agents

- Claude Code
- OpenCode
- Codex
- Cursor
- Antigravity
- Roo Code

## Structure

- `skills/nestjs-best-practices/` - The installable skill (this is what `skills add` copies into your project)
  - `SKILL.md` - Skill entry point and quick reference
  - `rules/` - Individual rule files (one per rule)
    - `_sections.md` - Section metadata (titles, impacts, descriptions)
    - `_template.md` - Template for creating new rules
    - `area-description.md` - Individual rule files
- `scripts/` - Build scripts and utilities
- `metadata.json` - Document metadata (version, organization, abstract)
- __`AGENTS.md`__ - Compiled output (generated)

## Getting Started

1. Install dependencies:
   ```bash
   cd scripts && npm install
   ```

2. Build AGENTS.md from rules:
   ```bash
   npm run build
   # or
   ./scripts/build.sh
   ```

## Creating a New Rule

1. Copy `skills/nestjs-best-practices/rules/_template.md` to `skills/nestjs-best-practices/rules/area-description.md`
2. Choose the appropriate area prefix:
   - `arch-` for Architecture (Section 1)
   - `di-` for Dependency Injection (Section 2)
   - `error-` for Error Handling (Section 3)
   - `security-` for Security (Section 4)
   - `perf-` for Performance (Section 5)
   - `test-` for Testing (Section 6)
   - `db-` for Database & ORM (Section 7)
   - `api-` for API Design (Section 8)
   - `micro-` for Microservices (Section 9)
   - `devops-` for DevOps & Deployment (Section 10)
3. Fill in the frontmatter and content
4. Ensure you have clear examples with explanations
5. Run the build script to regenerate AGENTS.md

## Rule File Structure

Each rule file should follow this structure:

```markdown
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

Optional explanatory text after examples.

Reference: [NestJS Documentation](https://docs.nestjs.com)


## File Naming Convention

- Files starting with `_` are special (excluded from build)
- Rule files: `area-description.md` (e.g., `arch-avoid-circular-deps.md`)
- Section is automatically inferred from filename prefix
- Rules are sorted alphabetically by title within each section
- IDs (e.g., 1.1, 1.2) are auto-generated during build

## Impact Levels

| Level | Description |
|-------|-------------|
| CRITICAL | Violations cause runtime errors, security vulnerabilities, or architectural breakdown |
| HIGH | Significant impact on reliability, security, or maintainability |
| MEDIUM-HIGH | Notable impact on quality and developer experience |
| MEDIUM | Moderate impact on code quality and best practices |
| LOW-MEDIUM | Minor improvements for consistency and maintainability |

## Scripts

- `npm run build` (in scripts/) - Compile rules into AGENTS.md

## Contributing

When adding or modifying rules:

1. Use the correct filename prefix for your section
2. Follow the `_template.md` structure
3. Include clear bad/good examples with explanations
4. Add appropriate tags
5. Run the build script to regenerate AGENTS.md
6. Rules are automatically sorted by title - no need to manage numbers!

## Acknowledgments

- Inspired by the [Vercel React Best Practices](https://github.com/vercel-labs/agent-skills) skill structure
- Compatible with [skills](https://github.com/vercel-labs/skills) for easy installation across coding agents

## Compatible Agents

These NestJS skills work with:

- [Claude Code](https://claude.ai/code) - Anthropic's official CLI
- [AdaL](https://sylph.ai/adal) - Self-evolving AI coding agent with MCP support

