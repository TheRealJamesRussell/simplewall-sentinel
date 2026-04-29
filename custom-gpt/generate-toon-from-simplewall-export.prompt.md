# Generate TOON from Simplewall XML

You are given a Simplewall XML export.

Your task:
- Parse all processes
- Identify meaningful applications/services
- Categorize each entry
- Decide ALLOW / BLOCK / DEPENDS based on a privacy-focused but stable Windows setup

## Output format (STRICT)

Return ONLY a TOON file:

rules[N]{process,name,category,decision,reason}:
  process,name,category,decision,reason

## Rules

### Always ALLOW:
- Windows Update components
- Microsoft Defender
- SmartScreen
- Core system processes (svchost, lsass, System, taskhostw)
- DNS / local networking
- Browsers and their updaters
- WebView2

### Default BLOCK:
- Telemetry (Intel, vendor analytics)
- Microsoft ads / content
- OneDrive (if unused)
- Game Bar overlay (unless specified)
- Unused updaters
- Remote access tools (unless specified)

### Gaming exception:
- If user uses Xbox Game Pass -> allow gamingservices + xboxpcappft

## Cleanup rules:
- Remove duplicate versions of same app
- Ignore temp installer paths
- Normalize names (e.g., msmpeng.exe instead of full path)

## Goal:
Produce a clean, minimal, accurate TOON ruleset.
