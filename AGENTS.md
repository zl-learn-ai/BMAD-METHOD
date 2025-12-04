# AGENTS.md

This file provides guidance to Qoder (qoder.com) when working with code in this repository.

## Project Overview

BMAD-METHOD is a framework for AI-driven agile development built on **BMad Core** (Collaboration Optimized Reflection Engine). The codebase is structured as a modular system where:

- **BMad Core**: Universal framework for human-AI collaboration
- **BMad Method (BMM)**: Agile development workflows with 12 specialized agents
- **BMad Builder (BMB)**: Tools for creating custom agents and workflows
- **Creative Intelligence Suite (CIS)**: Innovation and problem-solving workflows

The framework uses natural language (YAML/Markdown) for all components—no code execution in the core framework. Agents are defined in YAML with strict schema validation, and workflows are markdown-based with step-file architecture.

## Commands

### Testing & Validation

```bash
# Run all quality checks (schemas, installation, bundles, lint, format)
npm test

# Run schema tests only
npm run test:schemas

# Run installation component tests
npm run test:install

# Test with coverage report
npm run test:coverage

# Validate all *.agent.yaml files against schema
npm run validate:schemas

# Validate web bundles
npm run validate:bundles
```

### Code Quality

```bash
# Lint JavaScript and YAML files
npm run lint

# Lint and auto-fix issues
npm run lint:fix

# Check formatting
npm run format:check

# Auto-format code
npm run format:fix
```

### Build & Bundle

```bash
# Build all web bundles for ChatGPT/Claude/Gemini
npm run bundle

# Rebuild existing bundles
npm run rebundle
```

### Installation Commands

```bash
# Install BMAD agents/workflows
npm run install:bmad
# or
node tools/cli/bmad-cli.js install

# Install specific agent
npm run bmad:agent-install

# Check installation status
npm run bmad:status
```

## Architecture

### Directory Structure

```
src/
├── core/                      # Core framework (module-agnostic)
│   ├── agents/               # Core agents (bmad-master, web-orchestrator)
│   ├── workflows/            # Universal workflows (brainstorming, party-mode)
│   ├── resources/            # Shared resources (excalidraw helpers)
│   └── _module-installer/    # Installation configuration
├── modules/                   # Domain-specific modules
│   ├── bmm/                  # BMad Method (agile development)
│   │   ├── agents/          # 12 specialized agents (PM, Architect, DEV, etc.)
│   │   ├── workflows/       # 34 workflows across 4 phases
│   │   ├── teams/           # Pre-configured agent groups
│   │   ├── testarch/        # Testing infrastructure
│   │   ├── docs/            # User documentation
│   │   └── data/            # Module data files
│   ├── bmb/                  # BMad Builder (agent/workflow creation)
│   │   ├── workflows/       # Creation workflows (step-file architecture)
│   │   ├── workflows-legacy/# Legacy workflows being migrated
│   │   └── reference/       # Example agents and workflows
│   └── bmgd/                 # Game development module
├── utility/                   # Framework utilities
│   └── models/fragments/    # Reusable XML handler fragments
tools/
├── cli/                       # CLI implementation
│   └── bundlers/            # Web bundle generators
├── schema/                    # Zod schema definitions
│   └── agent.js             # Agent YAML validation schema
├── flattener/                # Codebase documentation tool
├── validate-agent-schema.js  # Schema validation CLI
└── validate-bundles.js       # Bundle validation

test/
├── fixtures/agent-schema/    # 50+ test fixtures for schema validation
├── test-agent-schema.js      # Main test runner
└── test-installation-components.js
```

### Key Architectural Patterns

**Agent Schema** (`tools/schema/agent.js`):
- All agents must be `*.agent.yaml` files conforming to strict Zod schema
- Agents can be "core" (in `src/core/agents/`) or "module" agents (in `src/modules/{module}/agents/`)
- Module agents MUST have `module` field matching their path
- Menu triggers must be kebab-case (no asterisks, camelCase, snake_case, or spaces)
- Command targets: `workflow`, `validate-workflow`, `exec`, `action`, `tmpl`, `data`

**Workflow Architecture**:
- Step-file architecture: main `workflow.md` + individual step files in `steps/`
- Just-in-time (JIT) loading of steps
- Template-based execution with state management
- Intent-driven vs prescriptive spectrum

**Module System**:
- Modules are self-contained with agents, workflows, teams, and data
- `_module-installer/install-config.yaml` defines installation behavior
- Update-safe customization: user customizations persist through updates

**Web Bundles**:
- Agents compiled into single-file bundles for ChatGPT, Claude Projects, Gemini Gems
- Auto-injection of handler fragments based on menu command types
- XML format for web-orchestrator, YAML for core agents

### Scale-Adaptive Intelligence (BMM Module)

BMM automatically adjusts planning depth based on project complexity:
- **Level 0-1**: Quick Spec Flow (bug fixes, small features)
- **Level 2**: PRD with optional architecture
- **Level 3-4**: Full PRD + comprehensive architecture + UX design

Story lifecycle: `backlog → drafted → ready → in-progress → review → done`

## Development Guidelines

### Agent Development

1. All agents MUST be valid YAML conforming to `tools/schema/agent.js`
2. Run `npm run validate:schemas` before committing agent changes
3. Menu triggers must be kebab-case
4. Core agents cannot have `module` field; module agents must
5. Agent files must end with `.agent.yaml`

### Workflow Development

1. Use step-file architecture for new workflows
2. Main `workflow.md` orchestrates, steps in `steps/` subdirectory
3. Follow template pattern in `src/modules/bmb/docs/workflows/step-template.md`
4. Keep dev agents lean (context for coding, not docs)
5. Planning agents can be larger with complex tasks

### Testing Requirements

1. Add test fixtures to `test/fixtures/agent-schema/` for schema changes
2. All tests must pass before merging: `npm test`
3. Maintain 100% code coverage on schema validation
4. Test both valid and invalid cases

### Code Style

- Natural language (Markdown/YAML) for all framework components
- No code execution in core framework
- Follow existing conventions in each module
- Use existing libraries/utilities before creating new ones
- Validate YAML with `npm run format:check`

### Commit Workflow

1. Run `npm run lint:fix && npm run format:fix` before committing
2. Pre-commit hooks run lint-staged checks
3. All commits must pass CI checks (schemas, lint, format, tests)
4. Use conventional commit messages (feat:, fix:, docs:, refactor:, etc.)

## Important Notes

- **Node.js >= 20.0.0 required**
- All file changes go through `npm test` before merge
- Schema validation blocks PRs with invalid agent files
- Web bundles auto-generated from agent source files
- Multi-language support: separate settings for communication vs code output
- Document sharding: 90% token savings for large projects
- This is v6 (alpha)—complete architectural overhaul from v4
