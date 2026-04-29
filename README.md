# 🛡️ Simplewall Sentinel

Analyze Simplewall firewall alerts and get clear, practical decisions on what to allow or block — optimized for a **privacy-focused but stable Windows setup**.

---

## 🚀 What This Is

Simplewall Sentinel is a lightweight system that:

- Interprets Simplewall alerts (screenshots or exports)
- Explains what each connection does
- Recommends **ALLOW / BLOCK / DEPENDS**
- Maintains a **persistent rule set** using a compact `.toon` format
- Learns your decisions over time

---

## 🧠 Key Idea

Instead of guessing every time:

👉 You build a **personal firewall intelligence layer**

- Block telemetry, ads, unused services  
- Allow security, updates, and apps you actually use  
- Keep your system quiet and predictable  

---

## 📦 Repo Structure

```
simplewall-sentinel/
  README.md
  ai_instructions.md
  simplewall_rules.toon

  custom-gpt/
    custom-gpt-instructions.md
    generate-toon-from-xml.prompt.md
    simplewall_rules.template.toon
```

---

## 🧾 TOON Format (Core Memory System)

We use a **token-efficient rule format** instead of JSON:

```
rules[N]{process,name,category,decision,reason}:
  msmpeng.exe,Microsoft Defender,security,allow,core antivirus engine
  onedrive.sync.service.exe,OneDrive Sync,cloud,block,user does not use OneDrive
```

---

## 🧠 Decision Philosophy

### ✅ Always Allow
- Windows Update system
- Microsoft Defender / SmartScreen
- Core system processes
- DNS & local network traffic
- Browser + updater security traffic

### ❌ Default Block
- Telemetry (Intel, vendor analytics)
- Ads / Microsoft content suggestions
- OneDrive (if unused)
- Game Bar overlay (optional)
- Unused background updaters
- Remote access tools (unless used)

### 🎮 Special Case
- Xbox Game Pass → **allowed**
- Game Bar overlay → optional (default block)

---

## 🧰 Setup Options

### 🤖 Option 1 — Custom GPT (Easiest)

1. Create a Custom GPT in ChatGPT  
2. Paste contents of:

```
custom-gpt/custom-gpt-instructions.md
```

3. Upload:

```
simplewall_rules.template.toon
```

(or your own `.toon` file)

4. Done

---

### 💻 Option 2 — Local Agent Setup

1. Open project folder in your agent environment  
2. Use:

```
ai_instructions.md
simplewall_rules.toon
```

ai_instructions.md is the ONLY instruction file in the repo.

ai_instructions.md is the core brain for all local AI agents.

The user must rename ai_instructions.md depending on the tool they are using:

- Codex → rename to AGENTS.md
- Claude → rename to CLAUDE.md
- Gemini → rename to GEMINI.md
- Any other tool → follow that tool’s expected filename

The AI agent reads ai_instructions.md after renaming, analyzes Simplewall screenshots, and reads AND updates simplewall_rules.toon automatically.

3. Start your agent

---

## 🔄 Generating Your Own Rules

### Export from Simplewall

1. Open Simplewall  
2. File → Export  
3. Save `.xml`

---

### Convert to TOON

Use:

```
custom-gpt/generate-toon-from-xml.prompt.md
```

Paste your XML → get a full `.toon` profile

---

## 🧹 Recommended Cleanup

Before building your rules:

- Remove OneDrive (if unused)
- Remove Intel Driver & Support Assistant
- Remove Intel Computing Improvement Program
- Remove unused VPNs / remote tools

---

## 🎯 Goal

End state:

- 🔇 Minimal alerts
- 🧠 Clear decisions
- 🔒 Strong privacy
- ⚙️ Stable system

---

## ⚠️ Important Notes

- Blocking core system processes can break Windows
- Be careful with:
  - svchost.exe
  - taskhostw.exe
  - lsass.exe

---

## 🧪 Workflow

1. See Simplewall alert  
2. Send screenshot to agent  
3. Get explanation + decision  
4. Confirm decision  
5. Rule gets saved

---

## 🏁 Result

A fully personalized firewall system that understands your setup.

---

## 📛 Name

Simplewall Sentinel

---

## 📝 Description

Analyzes Simplewall alerts and recommends allow/block decisions for a privacy-focused, stable Windows setup with persistent rule memory.
