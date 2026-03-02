# CLI Commands

Complete reference for OmniAgent CLI commands.

## Global Options

```bash
omniagent [command] --config <path>  # Specify config file
omniagent [command] --help           # Show help
```

## Gateway

### gateway run

Start the gateway server.

```bash
omniagent gateway run [flags]
```

**Flags:**

| Flag | Description |
|------|-------------|
| `--config` | Path to config file |
| `--address` | Override gateway address |

**Examples:**

```bash
# Start with default settings
omniagent gateway run

# Start with config file
omniagent gateway run --config omniagent.yaml

# Start with custom address
omniagent gateway run --address 0.0.0.0:8080
```

## Skills

### skills list

List all discovered skills.

```bash
omniagent skills list
```

**Output:**

```
✓ 🎵 sonoscli - Control Sonos speakers via CLI
✓ 🐙 github - GitHub CLI operations
✗ ☀️ weather - Weather forecasts (missing: weather binary)
```

- `✓` - Skill is available (requirements met)
- `✗` - Skill unavailable (missing requirements)

### skills info

Show detailed information about a skill.

```bash
omniagent skills info <name>
```

**Example:**

```bash
omniagent skills info sonoscli
```

**Output:**

```
Name:        sonoscli
Description: Control Sonos speakers via CLI
Path:        /Users/john/.omniagent/skills/sonoscli
Emoji:       🎵

Requirements:
  Binaries: sonos
  Env Vars: (none)

Status: ✓ Available
```

### skills check

Check requirements for all skills.

```bash
omniagent skills check
```

**Output:**

```
Checking skill requirements...

✓ sonoscli
  - sonos binary: found at /usr/local/bin/sonos

✓ github
  - gh binary: found at /usr/local/bin/gh

✗ weather
  - weather binary: NOT FOUND
    Install: brew install weather

Summary: 2/3 skills available
```

## Channels

### channels list

List registered channels.

```bash
omniagent channels list
```

**Output:**

```
CHANNEL     ENABLED  STATUS
whatsapp    true     connected
telegram    false    -
discord     false    -
```

### channels status

Show detailed channel status.

```bash
omniagent channels status
```

**Output:**

```
WhatsApp:
  Status: connected
  Phone: +1 555-123-4567
  Session: whatsapp.db

Telegram:
  Status: disabled

Discord:
  Status: disabled
```

## Config

### config show

Display current configuration.

```bash
omniagent config show
```

**Flags:**

| Flag | Description |
|------|-------------|
| `--format` | Output format: `yaml`, `json` |

**Example:**

```bash
omniagent config show --format json
```

## Version

### version

Show version information.

```bash
omniagent version
```

**Output:**

```
omniagent v0.4.0 (abc1234) built 2026-03-01 with go1.25 for darwin/arm64
```

**Flags:**

| Flag | Description |
|------|-------------|
| `--json` | Output as JSON |

```bash
omniagent version --json
```

```json
{
  "version": "0.4.0",
  "commit": "abc1234",
  "build_date": "2026-03-01",
  "go_version": "go1.25",
  "platform": "darwin/arm64"
}
```

## Exit Codes

| Code | Description |
|------|-------------|
| 0 | Success |
| 1 | General error |
| 2 | Configuration error |
| 3 | Connection error |
