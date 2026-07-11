# VÍA — AI Stadium Companion for FIFA World Cup 2026

**Challenge:** Smart Stadiums & Tournament Operations
**Live demo:** _[add your GitHub Pages / Netlify link here]_

---

## The Problem

Large tournament venues create three recurring pain points for fans, volunteers, and organizers alike:

- **Crowd movement** — fans don't know where congestion is building until they're stuck in it
- **Waiting times** — gates, restrooms, and transit queues are invisible until you're in line
- **Real-time coordination** — language barriers slow down every interaction between fans and staff during the exact moments (finding a gate, reporting an issue) when speed matters most

VÍA addresses all three with a single GenAI-powered companion that fans, volunteers, and organizers can all use from the same platform.

## What It Does

**For fans — Fan Assist Portal**
- **Smart Crowd-Aware Navigation** — a live radial density map of the stadium bowl, color-coded by gate and concourse ring, with one-tap routing to a gate, restroom, accessible seat path, food, transit hub, or a safety report
- **Multilingual Fan AI Concierge** — real-time Q&A in 12 languages (English, Español, Français, Português, Deutsch, Italiano, العربية, 中文, 日本語, 한국어, हिन्दी, Русский), powered by live calls to Claude
- **Voice input & output** — ask questions by speaking (Web Speech API), and have answers read back aloud — built for accessibility as much as convenience
- **Crowd-Smart Transit Schedule** — live departure and demand info for subway, rideshare, shuttle, and accessible van options

**For organizers & volunteers — Command Center**
- Live operational ticker (gate wait times, crowd density, weather, kickoff countdown)
- Active alerts feed surfaced from concourse signals and fan reports
- Language-mix analytics, so staffing and signage can adapt to who's actually in the building

**For testing & iteration — AI Playground**
- A sandbox where organizers can test concierge prompts and quick-help flows before they ship to fans

## How GenAI Is Used

Every concierge response — whether triggered by a typed question, a voice query, or a one-tap quick-help action — is generated live by calling the Claude API with a system prompt that includes the fan's stadium, section, and selected language. This means answers are contextual and dynamic, not scripted: the same question gets a different, situationally-appropriate answer depending on where the fan actually is and what's happening around them.

If the live API is unreachable (for example, when the file is opened outside the Claude.ai environment that authenticates the request), VÍA gracefully falls back to an offline demo mode with keyword-matched example answers — so the experience stays fully functional for live demos and judging, even without a network path to the API.

## Tech Stack

- Vanilla HTML/CSS/JS — single-file, no build step, no dependencies to install
- [Anthropic Claude API](https://docs.claude.com) (`claude-sonnet-4-6`) for the concierge
- Web Speech API (`SpeechRecognition` + `SpeechSynthesis`) for voice input/output
- Pure SVG/CSS for the crowd-density map, hero graphics, and all iconography — no external image assets

## Screenshots

**Command Center** — live operational overview for organizers and volunteers
![Command Center](screenshots/command-center.png)

**Fan Assist Portal** — crowd-aware navigation + multilingual concierge + transit schedule
![Fan Assist Portal](screenshots/fan-assist-portal.png)

**AI Playground** — prompt-testing sandbox
![AI Playground](screenshots/playground.png)

## Running It

No build step. Open `index.html` in a browser, or serve the folder with any static host (GitHub Pages, Netlify, Vercel).

```bash
# quickest local check
python3 -m http.server 8000
# then open http://localhost:8000
```

## Future Improvements

- Replace simulated crowd-density and transit data with real venue sensor / GIS feeds
- Expand the organizer Command Center into a full dispatch tool for stewards
- Persist fan preferences (language, accessibility settings) across sessions
- Add real indoor-positioning so "my location" is detected automatically rather than entered manually

---

Built for the PromptWars Mini-Challenge.
