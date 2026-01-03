# build-test-tools

Automated build and test execution tools for Claude Code.

## Features

- **Automatic Project Detection**: Identifies project type from build files
- **Build Execution**: Runs appropriate build commands with error analysis
- **Test Execution**: Runs test suites with verbose output
- **Failure Analysis**: Provides root cause analysis for failing tests
- **Auto-Fix Suggestions**: Suggests and applies fixes for common issues
- **Lint Integration**: Runs linting after tests pass

## Components

### Agent: build-test-runner

A subagent that can be invoked to build and test projects.

**Usage:**
```
Use the build-test-runner subagent to build and test the project
```

### Skill: build-test-auto

A skill that is automatically triggered when:
- Code changes are made
- Tests fail
- Before creating pull requests
- When verifying code quality

## Supported Projects

| Type | Detection | Build | Test |
|------|-----------|-------|------|
| Node.js | `package.json` | `npm run build` | `npm test` |
| Python | `pyproject.toml`, `setup.py` | `pip install -e .` | `pytest` |
| Rust | `Cargo.toml` | `cargo build` | `cargo test` |
| Go | `go.mod` | `go build ./...` | `go test ./...` |
| Java (Maven) | `pom.xml` | `mvn compile` | `mvn test` |
| Java (Gradle) | `build.gradle` | `./gradlew build` | `./gradlew test` |
| Ruby | `Gemfile` | `bundle install` | `bundle exec rspec` |
| Make | `Makefile` | `make` | `make test` |

## Installation

```bash
/plugin marketplace add takutakahashi/claude-code-plugins
/plugin enable build-test-tools@claude-code-plugins
```

## License

MIT
