
# Fixium - PocketMine Plugin for MCPE 0.15.10

**Fixium** is a powerful optimization and debugging plugin for PocketMine servers running MCPE 0.15.10, developed by **HighLights**. It improves performance, manages server resources, and generates snapshots for advanced analysis.

---

## 🧠 Introduction

Fixium helps administrators monitor and optimize server performance with minimal effort. It captures real-time snapshots containing memory, entity, player, and TPS data. Combined with Fixium Graphic Maker (FGM), it provides easy-to-read performance graphs.

---

## ⚙️ Included Modules

Fixium is modular and includes the following components:

### 1. TOD (TickOverloadDetector)
Detects plugin execution times in milliseconds (MS), identifying the most resource-intensive ones.

### 2. EntityFix
Prevents the spawning of empty, invalid, or closed entities, reducing unnecessary lag.

### 3. AutoCleaner
Automatically removes unused or ownerless entities to declutter the world and save memory.

### 4. WorldLoader
Preloads all configured worlds on server start to avoid player-related chunk loading issues.

### 5. ChunkFreezeFix
Automatically unloads frozen (inactive) chunks to free memory and processing time.

### 6. FixiumProfiler
Captures snapshots of server data for visual analysis using FGM. Snapshots include memory usage, player count, TPS, and more.

### 7. FixiumTickLimiter
Reduces CPU usage by simulating fewer ticks in worlds without players. Automatically resumes normal simulation when players join.

### 8. SoftViewDistanceLimiter  
Applies a dynamic view distance for players based on activity:
- If a player is AFK or stationary, their visible chunk distance is reduced.
- Restores full view distance when the player moves or interacts.
- Helps reduce chunk loading and memory usage without changing server-wide config.

### 9. PluginRestarter  
Detects inactive, disabled, or memory-intensive plugins and alerts the console + online staff with `fxm.alert` permission.

- Logs plugin failures or memory issues to console using `Logger::log()`.
- Does **not** reload plugins automatically to ensure server stability.
- Command `/fxm -r <pluginName>` reloads a specific plugin.
- Command `/fxm -r --a` reloads all plugins.

> Ensures plugin stability while giving full control to server administrators.

---

## 🛠️ Available Commands

Fixium provides several commands for monitoring and diagnostics:

### `/fixium`
Displays general plugin information, useful links, and credits.

### `/worlds`
Lists all loaded worlds with detailed info:
- World name
- Load status (Loaded/Unloaded)
- Size on disk
- Memory usage
- Chunks loaded
- Garbage count (if applicable)
- Tick activity

### `/plcheck <pluginName|--all>`
Checks plugin status and diagnostics:
- Shows whether each plugin is active or inactive
- Displays memory and folder usage
- Lists version, author, and description

### `/fxm -r <pluginName|--a>`
Manual plugin reload interface:
- `--a` = reload all plugins
- `<pluginName>` = reload a specific plugin (must be exact)

Used in combination with **PluginRestarter** alerts.

---

## 📊 How to Use Fixium Graphic Maker (FGM)

FGM is a web-based tool that renders `.fxm` snapshot files into interactive charts.

### Steps:

1. Go to the `snapshots/` folder inside your server's Fixium plugin directory.  
2. Open any `.fxm` file.  
3. Copy the line that begins with `encoded: ...`  
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
Join us on Discord or submit an issue or PR on GitHub.

---

## 🧪 Debug Info

- Plugin Name: `Fixium`
- Version: `0.0.1-beta.0.3` (pre-release)
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
