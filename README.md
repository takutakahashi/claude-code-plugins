# Claude Code Plugins Marketplace

A collection of useful skills and agents for Claude Code.

## Installation

Add this marketplace to your Claude Code:

```bash
/plugin marketplace add takutakahashi/claude-code-plugins
```

Then enable the plugins you want:

```bash
/plugin enable build-test-tools@claude-code-plugins
```

## Available Plugins

### build-test-tools

Automated build and test execution tools for Claude Code.

**Features:**
- Automatic project type detection (Node.js, Python, Rust, Go, Java, Ruby, etc.)
- Build execution with error analysis
- Test execution with failure diagnostics
- Automatic fix suggestions
- Linting integration

**Included Components:**

| Type | Name | Description |
|------|------|-------------|
| Agent | `build-test-runner` | Builds projects and runs tests with automatic failure analysis |
| Skill | `build-test-auto` | Automatically triggered when code changes are made or tests need verification |

**Usage:**

```
# Explicit invocation via Task tool
Use the build-test-runner subagent to build and test the project

# Natural language
Build and run tests for this project
Fix the failing tests
```

**Supported Project Types:**

| Project Type | Build File | Build Command | Test Command |
|-------------|-----------|---------------|--------------|
| Node.js | `package.json` | `npm run build` | `npm test` |
| Python | `pyproject.toml` / `setup.py` | `pip install -e .` | `pytest` |
| Rust | `Cargo.toml` | `cargo build` | `cargo test` |
| Go | `go.mod` | `go build ./...` | `go test ./...` |
| Java (Maven) | `pom.xml` | `mvn compile` | `mvn test` |
| Java (Gradle) | `build.gradle` | `./gradlew build` | `./gradlew test` |
| Ruby | `Gemfile` | `bundle install` | `bundle exec rspec` |
| Make | `Makefile` | `make` | `make test` |

## Directory Structure

```
claude-code-plugins/
├── .claude-plugin/
│   └── marketplace.json       # Marketplace manifest
├── plugins/
│   └── build-test-tools/      # Build & Test plugin
│       ├── .claude-plugin/
│       │   └── plugin.json    # Plugin manifest
│       ├── agents/
│       │   └── build-test-runner.md
│       └── skills/
│           └── build-test-auto/
│               └── SKILL.md
├── README.md
└── LICENSE
```

## Contributing

1. Fork this repository
2. Create a new plugin in `plugins/your-plugin-name/`
3. Add plugin manifest at `plugins/your-plugin-name/.claude-plugin/plugin.json`
4. Update `.claude-plugin/marketplace.json` to include your plugin
5. Submit a pull request

### Plugin Structure

Each plugin should have:

```
plugins/your-plugin/
├── .claude-plugin/
│   └── plugin.json     # Required: Plugin manifest
├── agents/             # Optional: Custom subagents
│   └── your-agent.md
├── skills/             # Optional: Skills
│   └── your-skill/
│       └── SKILL.md
├── commands/           # Optional: Slash commands
│   └── your-command.md
└── README.md           # Recommended: Plugin documentation
```

## License

MIT License - see [LICENSE](LICENSE) for details.
