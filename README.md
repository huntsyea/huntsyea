<div align="center">

<img src="assets/daddys-home.gif" alt="Tony Stark walking into his workshop: Wake up! Daddy's home" width="600" />

I build products, and AI agents write the code. Right now I'm building a fitness and nutrition agent.

[huntsyea.com](https://huntsyea.com) · [@huntsyea](https://x.com/huntsyea) · [info@huntsyea.com](mailto:info@huntsyea.com)

</div>

---

## I build stuff. I don't write code.

Since August 10 I've run 1,918 agent threads: 681 in Claude Code, 648 in Pi, 518 in Codex, and the rest in Cursor, OpenCode and Grok. Usually several run at once, each in its own worktree.

That only works because I have a loop that catches their mistakes:

1. **Spec first.** I get grilled on the idea until it holds up, then pin down the vocabulary in a glossary and the decisions in ADRs. Agents drift less when the nouns are fixed.
2. **Tickets small enough for one agent.** Each one is a vertical slice that a single thread can finish.
3. **Two separate reviews.** One checks the repo's rules and the other checks the spec. They're separate because an agent can pass one and fail the other.
4. **Fix, then review again.** One branch went through five whole-branch reviews before I signed off.

## Current Projects

### [kitchen-frame](https://github.com/huntsyea/kitchen-frame)

<img src="https://raw.githubusercontent.com/huntsyea/kitchen-frame/main/docs/images/home-light.jpg" alt="kitchen-frame home screen" width="600" />

A $50 Android photo frame on our kitchen wall that boots straight into a full-screen dashboard. It shows the family calendar, weather, Todoist groceries, recipes and Home Assistant music. My agents push messages to it over a WebSocket. If nobody touches it for 5 minutes, it turns into a clock.

It's a Svelte 5 app served by a Cloudflare Worker, which also keeps every API token off the frame. The idea came from Wes Bos's [photo-frame-dashboard](https://github.com/wesbos/photo-frame-dashboard).

### [hermes-evenhub-bridge](https://github.com/huntsyea/hermes-evenhub-bridge) + [hermes-even-hub-app](https://github.com/huntsyea/hermes-even-hub-app)

Talk to a [Hermes](https://github.com/NousResearch/hermes-agent) agent through Even Realities G2 glasses. The reply streams onto a 576×288 display token by token, and tool calls show up while they run. Speech is transcribed on the Mac with Parakeet on the Apple Neural Engine.

The bridge is a Python plugin that adds the glasses as a Hermes gateway platform. The app is a TypeScript Even Hub WebView. The two halves share one JSON frame protocol.

```bash
hermes plugins install huntsyea/hermes-evenhub-bridge
```

### [esp32-companion](https://github.com/huntsyea/esp32-companion) + [hermes-esp32](https://github.com/huntsyea/hermes-esp32)

A pocket voice companion built on a Waveshare ESP32-S3 with a 1.54" touchscreen. Hold to talk, and it sends your voice to my Hermes agent over a secure LAN WebSocket. The reply plays back as speech while an animated Blobatar face shows what the conversation is doing. It also has a clock screen and a connection status screen.

The firmware is built on [XiaoZhi ESP32](https://github.com/78/xiaozhi-esp32). hermes-esp32 is the Hermes plugin on the other end. It packages each recording as Ogg Opus for Hermes's speech-to-text and streams the spoken reply back as 16 kHz Opus packets. If you interrupt, it drops the unfinished turn so old audio never plays.

### [classical-virtues](https://github.com/huntsyea/classical-virtues)

Stories about the classical virtues, with narration, built for reading. Next.js and BaseHub.

## On the bench

- **Echo Show and Echo Spot without Alexa.** They boot Alpine Linux and work as local Home Assistant voice satellites. I'm building on two forks, [techo5](https://github.com/huntsyea/techo5) and [techo5-spot](https://github.com/huntsyea/techo5-spot).
- **iMessage agents** that coach training, keep me accountable and handle household logistics.
- **A skill-tree learning app.** Before designing it I studied the progression systems in AoE4, Baldur's Gate 3, RDR2 and AC Valhalla.
- **Plugins for [bb](https://github.com/huntsyea/bb)**, the agent IDE where those 1,918 threads ran.

## Stack

![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![Astro](https://img.shields.io/badge/Astro-BC52EE?style=flat-square&logo=astro&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![three.js](https://img.shields.io/badge/three.js-000000?style=flat-square&logo=threedotjs&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)
![Neon](https://img.shields.io/badge/Neon-00E599?style=flat-square&logo=neon&logoColor=black)
![Home Assistant](https://img.shields.io/badge/Home%20Assistant-18BCF2?style=flat-square&logo=homeassistant&logoColor=white)
![ESP32](https://img.shields.io/badge/ESP32-E7352C?style=flat-square&logo=espressif&logoColor=white)
![Claude Code](https://img.shields.io/badge/Claude%20Code-D97757?style=flat-square&logo=claude&logoColor=white)
![Codex](https://img.shields.io/badge/Codex-000000?style=flat-square&logo=data:image/svg%2bxml;base64,PHN2ZyBmaWxsPSJ3aGl0ZSIgcm9sZT0iaW1nIiB2aWV3Qm94PSIwIDAgMjQgMjQiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHRpdGxlPk9wZW5BSTwvdGl0bGU+PHBhdGggZD0iTTIyLjI4MTkgOS44MjExYTUuOTg0NyA1Ljk4NDcgMCAwIDAtLjUxNTctNC45MTA4IDYuMDQ2MiA2LjA0NjIgMCAwIDAtNi41MDk4LTIuOUE2LjA2NTEgNi4wNjUxIDAgMCAwIDQuOTgwNyA0LjE4MThhNS45ODQ3IDUuOTg0NyAwIDAgMC0zLjk5NzcgMi45IDYuMDQ2MiA2LjA0NjIgMCAwIDAgLjc0MjcgNy4wOTY2IDUuOTggNS45OCAwIDAgMCAuNTExIDQuOTEwNyA2LjA1MSA2LjA1MSAwIDAgMCA2LjUxNDYgMi45MDAxQTUuOTg0NyA1Ljk4NDcgMCAwIDAgMTMuMjU5OSAyNGE2LjA1NTcgNi4wNTU3IDAgMCAwIDUuNzcxOC00LjIwNTggNS45ODk0IDUuOTg5NCAwIDAgMCAzLjk5NzctMi45MDAxIDYuMDU1NyA2LjA1NTcgMCAwIDAtLjc0NzUtNy4wNzI5em0tOS4wMjIgMTIuNjA4MWE0LjQ3NTUgNC40NzU1IDAgMCAxLTIuODc2NC0xLjA0MDhsLjE0MTktLjA4MDQgNC43NzgzLTIuNzU4MmEuNzk0OC43OTQ4IDAgMCAwIC4zOTI3LS42ODEzdi02LjczNjlsMi4wMiAxLjE2ODZhLjA3MS4wNzEgMCAwIDEgLjAzOC4wNTJ2NS41ODI2YTQuNTA0IDQuNTA0IDAgMCAxLTQuNDk0NSA0LjQ5NDR6bS05LjY2MDctNC4xMjU0YTQuNDcwOCA0LjQ3MDggMCAwIDEtLjUzNDYtMy4wMTM3bC4xNDIuMDg1MiA0Ljc4MyAyLjc1ODJhLjc3MTIuNzcxMiAwIDAgMCAuNzgwNiAwbDUuODQyOC0zLjM2ODV2Mi4zMzI0YS4wODA0LjA4MDQgMCAwIDEtLjAzMzIuMDYxNUw5Ljc0IDE5Ljk1MDJhNC40OTkyIDQuNDk5MiAwIDAgMS02LjE0MDgtMS42NDY0ek0yLjM0MDggNy44OTU2YTQuNDg1IDQuNDg1IDAgMCAxIDIuMzY1NS0xLjk3MjhWMTEuNmEuNzY2NC43NjY0IDAgMCAwIC4zODc5LjY3NjVsNS44MTQ0IDMuMzU0My0yLjAyMDEgMS4xNjg1YS4wNzU3LjA3NTcgMCAwIDEtLjA3MSAwbC00LjgzMDMtMi43ODY1QTQuNTA0IDQuNTA0IDAgMCAxIDIuMzQwOCA3Ljg3MnptMTYuNTk2MyAzLjg1NThMMTMuMTAzOCA4LjM2NCAxNS4xMTkyIDcuMmEuMDc1Ny4wNzU3IDAgMCAxIC4wNzEgMGw0LjgzMDMgMi43OTEzYTQuNDk0NCA0LjQ5NDQgMCAwIDEtLjY3NjUgOC4xMDQydi01LjY3NzJhLjc5Ljc5IDAgMCAwLS40MDctLjY2N3ptMi4wMTA3LTMuMDIzMWwtLjE0Mi0uMDg1Mi00Ljc3MzUtMi43ODE4YS43NzU5Ljc3NTkgMCAwIDAtLjc4NTQgMEw5LjQwOSA5LjIyOTdWNi44OTc0YS4wNjYyLjA2NjIgMCAwIDEgLjAyODQtLjA2MTVsNC44MzAzLTIuNzg2NmE0LjQ5OTIgNC40OTkyIDAgMCAxIDYuNjgwMiA0LjY2ek04LjMwNjUgMTIuODYzbC0yLjAyLTEuMTYzOGEuMDgwNC4wODA0IDAgMCAxLS4wMzgtLjA1NjdWNi4wNzQyYTQuNDk5MiA0LjQ5OTIgMCAwIDEgNy4zNzU3LTMuNDUzN2wtLjE0Mi4wODA1TDguNzA0IDUuNDU5YS43OTQ4Ljc5NDggMCAwIDAtLjM5MjcuNjgxM3ptMS4wOTc2LTIuMzY1NGwyLjYwMi0xLjQ5OTggMi42MDY5IDEuNDk5OHYyLjk5OTRsLTIuNTk3NCAxLjQ5OTctMi42MDY3LTEuNDk5N1oiLz48L3N2Zz4=)
![Pi](https://img.shields.io/badge/Pi-000000?style=flat-square&logo=pi&logoColor=white)
![Cursor](https://img.shields.io/badge/Cursor-000000?style=flat-square&logo=cursor&logoColor=white)

---

My latest essay is *You Are Abstracting Too Early!* Read it at [huntsyea.com](https://huntsyea.com), or tell me on [X](https://x.com/huntsyea) why I'm wrong.
