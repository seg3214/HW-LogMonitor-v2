# HW-LogMonitor-v2

A high-performance, multithreaded **C++ Linux** automation tool for the browser-based hacking simulation game, HackerWars.io.

## Overview
This project was designed to provide real-time monitoring and management of in-game logs. It automates the process of scraping local and remote logs, anonymizing personal data (like IP addresses), and saving a persistent history of game activity to local files.
## Key Features
* **Multithreaded Architecture**: Utilizes pthreads to simultaneously fetch and process local and remote logs without blocking the main execution loop.
* **Real-time Scraping**: Uses libcurl to interface with the game's AJAX endpoints, maintaining a constant 3-second refresh cycle.
* **Data Anonymization**: Automatically detects the player's in-game IP and "localhost" entries, replacing them with a standardized "me" tag for cleaner local archives.
* **Session Persistence**: Integrated cookie-file handling to maintain authenticated sessions with the game server.
* **Automatic Log Rotation**: Built-in file system checks to ensure log files are saved sequentially (e.g., logmon0.txt, logmon1.txt) without overwriting previous data.

## How It Works
_Init_: The program retrieves the player's current IP via getStatic.  
_Monitor_: Two threads are spawned to scrape the /log and /internet?view=logs pages.  
_Process_: The logic parses the HTML response, extracts the log text, and deduplicates entries.  
_Save_: Unique log entries are formatted and appended to a local .txt file for permanent storage.  

> ## ⚠️ Legal Disclaimer
> 
> **This tool is for educational and research purposes only.** 
>
>### Research Methodology
> Visual demonstrations were captured in a controlled environment for the purpose of validating system stability and latency under real-world conditions. 
> ### Use at Your Own Risk
> The author (and any contributors) are NOT responsible for:
> *   **Account Actions:** Any bans, suspensions, or penalties applied to your accounts by game developers or anti-cheat systems (e.g., VAC, BattlEye, Easy Anti-Cheat).
> *   **System Damage:** Any data loss, hardware failure, or system instability caused by the use of this software.
> *   **Legal Consequences:** Any misuse of this tool that violates local laws or third-party Terms of Service.
> 
> ### License
> This project is licensed under the **GNU Affero General Public License v3.0 (AGPL-3.0)**. 
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED. 