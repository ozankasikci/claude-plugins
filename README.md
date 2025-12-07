# Ozan's Claude Code Plugins

A curated collection of Claude Code plugins for autonomous development workflows.

## Available Plugins

### AutoGoals

**Autonomous long-term goal execution system for Claude Code.**

Define multiple interconnected project goals in YAML, and let Claude Code work autonomously for hours implementing them one by one with interactive planning, autonomous execution, and automated verification.

**Features:**
- Multi-goal execution with dependency management
- Interactive Socratic planning before implementation
- Autonomous TDD-based implementation
- Automated verification with retry logic
- State persistence across sessions
- Git worktree isolation per goal

**Repository:** [ozankasikci/autogoals](https://github.com/ozankasikci/autogoals)

## Installation

### Add this marketplace

```bash
/plugin marketplace add ozankasikci/claude-plugins
```

### Install AutoGoals

```bash
/plugin install autogoals@ozankasikci-plugins
```

Or install directly from the repository:

```bash
/plugin install ozankasikci/autogoals
```

## Quick Start with AutoGoals

1. Create `goals.yaml` in your project root:

```yaml
version: "1.0"
project_name: "my-app"

goals:
  - id: "backend"
    name: "Backend Setup"
    description: "Create Node.js backend with Express and TypeScript"
    dependencies: []
    acceptance_criteria:
      - "npm test passes"
    verification_commands:
      - "npm test"
    max_retries: 2
    branch_name: "goal/backend"

  - id: "frontend"
    name: "Frontend Setup"
    description: "Create React frontend with TypeScript"
    dependencies: ["backend"]
    acceptance_criteria:
      - "npm run build succeeds"
    verification_commands:
      - "npm run build"
    max_retries: 2
    branch_name: "goal/frontend"
```

2. Start Claude Code - AutoGoals activates automatically when it detects `goals.yaml`

3. Or manually start with `/start`

## Commands

- `/start` - Initialize and begin goal execution
- `/status` - Show progress dashboard
- `/pause` - Pause autonomous execution
- `/resume` - Resume from current state

## License

Plugins in this marketplace are licensed under their respective licenses. AutoGoals is licensed under the MIT License.

## Contributing

Have feedback or suggestions? Open an issue on the respective plugin repository.
