# 🎛️ Fixium — PocketMine Plugin for MCPE 0.15.10

**Fixium** is a powerful optimization and debugging plugin for PocketMine servers running MCPE 0.15.10, developed by **HighLights**.  
It improves performance, manages server resources, and generates snapshots for advanced analysis.

---

## 🧠 Introduction

Fixium helps server admins monitor and optimize performance with minimal effort.  
It captures real-time snapshots containing memory usage, entity counts, player stats, and TPS data.

Combined with **Fixium Graphic Maker (FGM)**, it provides clear, interactive charts for understanding server health at a glance.

---

## ⚙️ Included Modules

Fixium is modular and includes the following key components:

### 1️⃣ TickOverloadDetector (TOD)  
Detects plugin execution times in milliseconds (ms), identifying the most resource-intensive plugins.

### 2️⃣ EntityFix  
Prevents spawning of empty, invalid, or closed entities, reducing unnecessary lag.

### 3️⃣ AutoCleaner  
Automatically removes unused or ownerless entities to declutter worlds and save memory.

### 4️⃣ WorldLoader  
Preloads all configured worlds at server start to avoid player-related chunk loading issues.

### 5️⃣ ChunkFreezeFix  
Automatically unloads frozen (inactive) chunks to free memory and CPU cycles.

### 6️⃣ FixiumProfiler  
Captures server snapshots for visual analysis via FGM, including memory usage, player counts, TPS, and more.

### 7️⃣ FixiumTickLimiter  
Reduces CPU load by simulating fewer ticks in worlds without players; automatically resumes normal simulation when players join.

### 8️⃣ SoftViewDistanceLimiter  
Dynamically adjusts player view distance based on activity:
- Reduces visible chunks when players are AFK or stationary.
- Restores full view distance upon movement or interaction.
- Helps reduce chunk loading and memory usage without changing global settings.

### 9️⃣ PluginRestarter  
Detects inactive, disabled, or memory-heavy plugins and alerts console + online staff with `fxm.alert` permission.

- Logs plugin failures or memory issues using `Logger::log()`.
- Does **not** reload plugins automatically to ensure server stability.
- Commands:
  - `/fxm -r <pluginName>` — Reload a specific plugin.
  - `/fxm -r --a` — Reload all plugins.

> Ensures plugin stability while giving full control to server administrators.

### 🔟 BlockLightUpdater  
Updates block light for stale chunks to prevent visual glitches and lighting-related lag.

### 1️⃣1️⃣ ChunkThrottle *(New)*  
Intelligently limits the number of active chunks per world based on player presence:
- Worlds with players use a high chunk limit (e.g., 300).
- Worlds without players use a low chunk limit (e.g., 75).
- Unloads distant chunks to maintain limits.
- Configurable with blacklist support to exclude specific worlds.

### 1️⃣2️⃣ LightUpdateLimiter *(New)*  
Controls the number of light updates to avoid server overload:
- Cancels light update events if a set limit is exceeded.
- Resets counters each tick with a scheduled task.
- Prevents lag caused by explosions, redstone, or complex circuits.

---

## 🛠️ Available Commands

Fixium provides several commands for monitoring and diagnostics:

### `/fixium`  
Displays general plugin info, useful links, and credits.

### `/worlds`  
Lists all loaded worlds with detailed info:  
- World name  
- Load status (Loaded/Unloaded)  
- Size on disk  
- Memory usage  
- Chunks loaded  
- Garbage counts (if applicable)  
- Tick activity

### `/plcheck <pluginName|--all>`  
Checks plugin status and diagnostics:  
- Shows if each plugin is active or inactive  
- Displays memory and folder usage  
- Lists version, author, and description

### `/fxm -r <pluginName|--a>`  
Manual plugin reload interface:  
- `--a` = reload all plugins  
- `<pluginName>` = reload specific plugin (exact name required)

Used with **PluginRestarter** alerts for stability management.

### `/dserver` *(New)*  
Displays advanced server diagnostics including:  
- Server name, PMMP version, codename  
- MCPE and API versions  
- Network protocol version  
- RakLib and PHP versions  
- OS info  
- Online players / max players  
- Loaded worlds count  
- Average TPS and CPU usage  
- MOTD, uptime, plugin version  
- Total entities and active chunks  
- Plugins loaded and current date/time

---

## 📊 How to Use Fixium Graphic Maker (FGM)

FGM is a web-based tool that renders `.fxm` snapshot files into interactive charts.

### Steps:

1. Navigate to the `snapshots/` folder inside your server's Fixium plugin directory.  
2. Open any `.fxm` file.  
3. Copy the line starting with `encoded: ...`  
4. Visit [FGM on GitHub Pages](https://highlightsofficial.github.io/FGM/)  
5. Paste the code and click "Generate Chart".

---

## 🔗 Useful Links

- 🔍 [Fixium Graphic Maker (FGM)](https://highlightsofficial.github.io/FGM/)  
- 💻 [HighLights GitHub Organization](https://github.com/orgs/HighLightsOfficial)  
- 🎥 [HighLights on YouTube](https://youtube.com/@highlightscompany?feature=shared)  
- 💬 [Join the Official Discord](https://discord.gg/k7Vt3UNBPj)  

---

## 💬 Contact

Got ideas, issues, or feedback?  
Join us on Discord or submit an issue or pull request on GitHub.

---

## 🧪 Debug Info

- Plugin Name: `Fixium`  
- Version: `0.0.1-beta.0.4` (pre-release)  
- PHP Compatibility: **PocketMine-MP 1.0.0 API** (MCPE 0.15.10)  
- Required Folders:  
  - `snapshots/`: stores `.fxm` snapshot files  
  - `logs/`: internal log files (used by modules like PluginRestarter)  
- Permissions:  
  - `fxm.alert`: Receive live alerts about plugin failures or optimization warnings  
  - `fixium.bypass.svdl`: Exclude player from AFK-based chunk unloading  

---

## 📄 License

This project is licensed under the **MIT License**.

---

> *“Great software is born from small optimizations done consistently.”*  
> — HighLights
