---
title: "Teaching CCSO: Breaking Juice Shop with the Red Team"
description: "Leading a Red Team workshop series for 30+ CCSO members using OWASP Juice Shop, from basic request tampering to full session hijacks."
date: 2025-11-05
tags: ["Cybersecurity", "CCSO", "RedTeam", "PennState", "Training"]
---

I spent a stretch this fall leading a Red Team workshop track for the Penn State Competitive Cyber Security Organization, using OWASP Juice Shop as the target.

Juice Shop is an intentionally vulnerable web app with 60+ flaws baked in, everything from XSS and SQL injection to broken authentication and insecure deserialization. It's a great teaching tool because the flaws are realistic, but the app is safe to tear apart without consequences.

## From request tampering to full exploitation

We started with the basics: intercepting and tampering with requests, understanding how client-side checks can be bypassed, and reading server responses closely enough to spot what's actually being validated (and what isn't). By the end of the series, members who'd never touched a proxy tool before were pulling off full session hijacks and exploiting the database directly.

Watching that progression across 30+ members in a matter of weeks was one of the more satisfying things I've done with the club. It's one thing to know an attack technique yourself. It's another to break it down clearly enough that a room full of people with wildly different starting points all get there.

Big shoutout to Aidan Ethier and Walker Kennedy, who ran the parallel Blue Team track: securing SSH, RDP, and WinRM, reviewing service configs, and hardening against the exact misconfigurations we were exploiting on the Red side. Running both sides side-by-side made the whole series click for people in a way a single-track workshop wouldn't have.
