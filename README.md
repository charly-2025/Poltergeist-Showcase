<p align="center">
  <img src="assets/logo.png" alt="Poltergeist logo" width="140">
</p>

<h1 align="center">Poltergeist</h1>

<p align="center">
  <b>An anonymous and local social network.</b><br>
  Post threads tied to your city, comment and like, with no account and no password.
</p>

<p align="center">
  <a href="https://visitors.poltergeist.ch"><b>visitors.poltergeist.ch</b></a> · Web app · Android app
</p>

<p align="center">
  <img src="assets/ghosts.png" alt="Poltergeist ghost avatars" width="560">
</p>

---

## The story

Poltergeist was born as a **product design project at Epitech Rennes**: a team
of students had to imagine a niche social network, design it and ship an MVP.
That first version is archived in
[Poltergeist-Epitech](https://github.com/charly-2025/Poltergeist-Epitech).

After the school project, part of the team **took it over and kept building**.
The stack was rewritten from scratch, a native Android app was added, along
with moderation tools, push notifications and a full CI / CD pipeline. Today
Poltergeist is a live product, self-hosted and online at
[visitors.poltergeist.ch](https://visitors.poltergeist.ch).

This repository is a showcase. The source code lives in a private repository.

## What it does

- **Total anonymity**: no username, no email, no password
- **Ghost avatars**: in each thread, everyone gets a random ghost, different from one thread to another, and the author is flagged
- **Local first**: threads are tied to one of ~32,000 cities worldwide, each shown with its country flag
- **Feed, search, favorites and likes**
- **Images in posts**, compressed and re-encoded server side, with metadata such as GPS position removed
- **Safe links only**: posts can only link to a curated list of trusted domains (no URL shorteners, scams or malware)
- **Light and dark themes**, custom primary color, English and French interface
- **Android app** with push notifications for new comments and new threads in your city

## From school MVP to product

| | School MVP | Poltergeist today |
| --- | --- | --- |
| Backend | Node.js, MongoDB | Node.js, Express, Prisma, PostgreSQL |
| Frontend | React | React + Vite, themes, i18n (EN / FR) |
| Mobile | None | Native Android app (Capacitor), push notifications (FCM) |
| Moderation | None | Shadow ban with banned words detection, private admin panel |
| Privacy | Anonymous accounts | Keyed hashing, IP data retention limits, image metadata removal |
| Quality | Manual testing | Unit and integration tests, ESLint, OpenAPI spec |
| Security | None | Dependency audit, secret scanning (Gitleaks), static analysis (Semgrep) |
| Delivery | Local Docker Compose | CI on every pull request, CD to the GitHub Container Registry |
| Hosting | Local machine | Raspberry Pi behind a Cloudflare Tunnel, HTTPS |

## Tech stack

`React` · `Vite` · `Node.js` · `Express` · `Prisma` · `PostgreSQL` · `Docker` · `nginx` · `Capacitor` · `Firebase Cloud Messaging` · `Cloudflare Tunnel` · `GitHub Actions` · `Raspberry Pi`

## Architecture

```
  Browser / Android app
          │  HTTPS
          ▼
  Cloudflare Tunnel ──▶ nginx ──┬──▶ React frontend
                                └──▶ Express API ──▶ PostgreSQL (Prisma)
                                          │
                                          └──▶ Firebase Cloud Messaging
```

Everything runs in Docker on a Raspberry Pi. No port is opened on the home
router: traffic goes through a Cloudflare Tunnel.

## Engineering practices

- Pull requests only on `main`, protected by a required CI check
- CI jobs: backend, frontend, API integration tests on a real PostgreSQL, Docker build and smoke test, security scans, commit message convention
- Production images published automatically after each merge
- Weekly dependency updates with Dependabot

---

<p align="center">
  Try it at <a href="https://visitors.poltergeist.ch"><b>visitors.poltergeist.ch</b></a>
</p>
