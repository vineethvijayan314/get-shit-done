# GSD User Profiling

Analyze and calibrate to developer style.

## Profile Logic

| Dimension | Range |
|-----------|-------|
| **Velocity** | Careful implementation <---> Rapid hacking |
| **Research** | Code-first <---> Documentation-first |
| **Communication** | Terse/Caveman <---> Verbose/English |
| **Tech Stack** | Ecosystem bias (React, Go, Python, etc.) |

## Process
1. `gsd-user-profiler` scans git logs.
2. Identifies "The Pattern".
3. Resolves Model Profile (Reasoning vs Velocity).
4. Synchronizes session context to match user preference.

## File
`.gsd/profiles/USER.json`: Personal configuration + style fingerprint.
