# 🛡️ Simplewall Sentinel

Analyze Simplewall firewall alerts and get clear, practical decisions on what to allow or block, optimized for a **privacy-focused but stable Windows setup**.

---

## 🚀 What This Is

Simplewall Sentinel is a lightweight system that:

- Interprets Simplewall alerts (screenshots or exports)
- Explains what each connection does
- Recommends **ALLOW / BLOCK / DEPENDS**
- Maintains a **persistent rule set** using a compact `.toon` format so the agent has context
- Learns your decisions over time

---

## 🧠 Key Idea

Instead of guessing every time:

👉 You build a **personal firewall intelligence layer**

- Block telemetry, ads, unused services  
- Allow security, updates, and apps you actually use  

---

## 🧰 Setup Options

### 🤖 Option 1: Custom GPT

You do not need to download the repo for this option.

1. Create a Custom GPT in ChatGPT  
2. Open and copy the contents of:

```
custom-gpt/custom-gpt-instructions.md
```

3. Upload:

```
custom-gpt/simplewall_rules.template.toon
```

4. Done

---

### 💻 Option 2: Local Agent Setup

Download only the local agent files:

```
mkdir simplewall-sentinel
cd simplewall-sentinel
curl -L -o ai_instructions.md https://raw.githubusercontent.com/TheRealJamesRussell/simplewall-sentinel/Main/local-agent/ai_instructions.md
curl -L -o simplewall_rules.toon https://raw.githubusercontent.com/TheRealJamesRussell/simplewall-sentinel/Main/local-agent/simplewall_rules.toon
```

ai_instructions.md is the ONLY instruction file in the repo.

ai_instructions.md is the core brain for all local AI agents.

The user must rename ai_instructions.md depending on the tool they are using:

- Codex → rename to AGENTS.md
- Claude → rename to CLAUDE.md
- Gemini → rename to GEMINI.md
- Any other tool → follow that tool’s expected filename

The AI agent reads ai_instructions.md after renaming, analyzes Simplewall screenshots, and reads AND updates simplewall_rules.toon automatically.

Start your agent in the folder with the renamed instruction file and simplewall_rules.toon.

---

## 🧾 TOON Format (Core Memory System)

We use a **token-efficient format** to store context and rules line by line for the agent to make decisions. The agent checks the `.toon` file first so it can use past decisions as context for future alerts.

For example, if the `.toon` file shows that the user uses Xbox Game Pass, the agent can recognize that an important Xbox network call should usually be allowed.

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

## 🔄 Updating TOON From Existing Simplewall Rules

This is only needed if you have been using Simplewall for a while and want to convert your existing local setup into a `.toon` file for the agent.

1. Open Simplewall  
2. File → Export  
3. Save `.xml`
4. Use:

```
custom-gpt/generate-toon-from-simplewall-export.prompt.md
```

Paste your XML to get a `.toon` profile that reflects the rules you already created locally.

---

## 🏁 Result

A fully personalized firewall system that understands your setup.

---

## 📛 Name

Simplewall Sentinel

---

## 📝 Description

Analyzes Simplewall alerts and recommends allow/block decisions for a privacy-focused, stable Windows setup with persistent rule memory.
