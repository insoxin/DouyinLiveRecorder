# DouyinLiveRecorder Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches development patterns for DouyinLiveRecorder, a Python-based live streaming recording tool that supports multiple platforms. The codebase focuses on stream URL parsing, recording functionality, and Telegram bot integration for remote management. The project follows conventional commit patterns and emphasizes iterative improvement of platform-specific parsers and bot commands.

## Coding Conventions

### File Naming
- Use `snake_case` for all Python files
- Main logic in `main.py`
- Platform parsing logic in `src/spider.py`
- Configuration in `config/config.ini`

### Import Style
```python
# Mix of absolute and relative imports
import os
import sys
from src.spider import parse_url
from telegram import Bot
```

### Commit Messages
- Follow conventional commit format
- Use prefixes: `fix:`, `feat:`, `refactor:`, `docs:`, `chore:`
- Keep messages concise (~35 characters average)
- Examples:
  ```
  fix: telegram bot command parsing
  feat: add new platform support
  refactor: improve spider logic
  ```

## Workflows

### Telegram Bot Feature Development
**Trigger:** When someone wants to add new Telegram bot commands or improve existing ones
**Command:** `/add-telegram-command`

1. Open `main.py` and locate the Telegram bot command handlers
2. Implement new command logic following existing patterns:
   ```python
   def handle_new_command(update, context):
       # Command implementation
       pass
   ```
3. Update `README.md` with new command documentation
4. Test command behavior with various inputs and edge cases
5. Update `config/config.ini` if new configuration options are needed
6. Create pull request with clear description of new functionality

### Spider Parsing Fixes
**Trigger:** When platform APIs change or parsing logic needs improvement
**Command:** `/fix-platform-parser`

1. Identify which platform's parsing is failing by checking error logs
2. Open `src/spider.py` and locate the relevant parsing function
3. Update regex patterns or API calls to match new platform structure:
   ```python
   def parse_platform_url(url):
       # Updated parsing logic
       pattern = r'new_regex_pattern'
       match = re.search(pattern, url)
       return match.group(1) if match else None
   ```
4. Test with various URL formats from the target platform
5. Handle edge cases and add proper error handling
6. Update `main.py` if interface changes are needed

### Main Py Fixes
**Trigger:** When core recording logic needs bug fixes or enhancements
**Command:** `/fix-core-logic`

1. Identify the specific issue in the main recording functionality
2. Open `main.py` and locate the problematic code section
3. Implement fix while maintaining existing functionality:
   ```python
   try:
       # Fixed recording logic
       pass
   except Exception as e:
       logger.error(f"Recording failed: {e}")
   ```
4. Test recording functionality with multiple stream sources
5. Ensure backward compatibility with existing configurations
6. Deploy changes and monitor for any regressions

### Copilot Assisted Development
**Trigger:** When developing new features or fixing complex issues with AI assistance
**Command:** `/copilot-feature`

1. Create initial plan commit outlining the feature or fix
2. Use GitHub Copilot to generate boilerplate code and suggestions
3. Implement feature incrementally with Copilot assistance
4. Create co-authored commits acknowledging AI contribution:
   ```
   feat: implement new feature

   Co-authored-by: GitHub Copilot <copilot@github.com>
   ```
5. Update relevant documentation files (`README.md`, config files)
6. Test thoroughly before creating pull request
7. Merge via pull request with proper review

## Testing Patterns

Testing follows a pattern-based approach:
- Test files use `*.test.*` naming convention
- Focus on integration testing of stream parsing and recording
- Manual testing of Telegram bot commands
- Platform-specific URL parsing validation

Example test structure:
```python
def test_platform_parsing():
    url = "https://example.com/stream"
    result = parse_url(url)
    assert result is not None
    assert "stream_url" in result
```

## Commands

| Command | Purpose |
|---------|---------|
| `/add-telegram-command` | Add new Telegram bot commands and functionality |
| `/fix-platform-parser` | Fix URL parsing for streaming platforms |
| `/fix-core-logic` | Fix core recording functionality issues |
| `/copilot-feature` | Develop features with GitHub Copilot assistance |