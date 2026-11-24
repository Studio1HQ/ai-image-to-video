<div align="center">

<img src="https://raw.githubusercontent.com/Studio1HQ/Studio1HQ/main/assets/banners/ai-image-to-video.webp" alt="AI Image to Video Converter: Turn a still image and a prompt into a short video with Eachlabs" width="100%" />

<br />
<br />

# AI Image to Video Converter

### Turn a still image and a prompt into a short video with Eachlabs

A Next.js app that uploads an image to Firebase Storage, then triggers an Eachlabs AI workflow with your prompt and shows the generated video.

<br />

[![Built by Studio1](https://img.shields.io/badge/Built_by_Studio1-f97316?style=for-the-badge&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAxNjAgMTYwIiBmaWxsPSJub25lIj48cGF0aCBmaWxsLXJ1bGU9ImV2ZW5vZGQiIGNsaXAtcnVsZT0iZXZlbm9kZCIgZD0iTTAgMzVDMCAxNi42ODA3IDE0LjA3NDQgMS42NDg0NCAzMiAwLjEyNjk1M1YxNDFINTEuMDUyM0M1Mi40MzA4IDEzNy4zNDQgNTQuNzQ0NiAxMzMuNjg5IDU3Ljk5MzggMTMwLjAzM0M2MS4xNDQ2IDEyNi41MDggNjQuNjg5MiAxMjMuNDQgNjguNjI3NyAxMjAuODI5QzcyLjU2NjIgMTE4LjM0OSA3Ni4zNTY5IDExNi43ODIgODAgMTE2LjEyOVY4Ni43NTQ0Qzc1LjQ3MDggODcuOTI5MiA3MS4zODQ2IDg5LjY5MTkgNjcuNzQxNSA5Mi4wNDE1QzY0IDk0LjUyMjUgNjAuNzUwOCA5Ny40NiA1Ny45OTM4IDEwMC44NTRDNTYuNTM0NSAxMDIuNzIgNTUuMjU0NSAxMDQuNjU5IDU0LjE1MzkgMTA2LjY3MVYwSDEyNUMxNDQuMzMgMCAxNjAgMTUuNjY5OSAxNjAgMzVWMTI1QzE2MCAxNDQuMzMgMTQ0LjMzIDE2MCAxMjUgMTYwSDEyNFYxOEgxMDQuOTQ4QzEwMy41NjkgMjEuNjgxNiAxMDEuMjU1IDI1LjM2MjggOTguMDA2MiAyOS4wNDQ0Qzk0Ljg1NTQgMzIuNTk0MiA5MS4zMTA4IDM1LjY4NDEgODcuMzcyMyAzOC4zMTRDODMuNDMzOCA0MC44MTIgNzkuNjQzMSA0Mi4zODk2IDc2IDQzLjA0NzRWNzIuNjMwNEM4MC41MjkyIDcxLjQ0NzMgODQuNjE1NCA2OS42NzI0IDg4LjI1ODUgNjcuMzA1N0M5MiA2NC44MDc2IDk1LjI0OTIgNjEuODQ5MSA5OC4wMDYyIDU4LjQzMDdDOTkuNDY1NSA1Ni41NTEzIDEwMC43NDUgNTQuNTk4NiAxMDEuODQ2IDUyLjU3MjNWMTYwSDM1QzE1LjY3IDE2MCAwIDE0NC4zMyAwIDEyNVYzNVoiIGZpbGw9IiNmZmZmZmYiLz48L3N2Zz4K)](https://studio1hq.com)
[![Built with Eachlabs](https://img.shields.io/badge/Built_with_Eachlabs-141414?style=for-the-badge)](https://eachlabs.ai)

[Eachlabs docs](https://docs.eachlabs.ai) &nbsp;·&nbsp; [Eachlabs](https://eachlabs.ai) &nbsp;·&nbsp; [More examples](https://github.com/Studio1HQ) &nbsp;·&nbsp; [studio1hq.com](https://studio1hq.com)

</div>

<br />

## Overview

An image-to-video converter built with Next.js. You upload an image and describe the effect you want in a prompt. The app stores the image in Firebase Storage, then triggers an [Eachlabs](https://docs.eachlabs.ai/flow/getting-started) workflow with the image URL and prompt, and displays the resulting video.

It is a compact example of calling a hosted AI workflow from a Next.js API route and polling for the result.

## Features

- **Image upload**: the `/create` page uploads the chosen image to Firebase Storage.
- **Prompt-driven effect**: your prompt is sent to the Eachlabs workflow with the image URL.
- **Workflow trigger and polling**: a `POST` to `/api` starts the workflow and returns a trigger id. A `GET` to `/api?triggerId=...` fetches the execution result.
- **Result view**: the generated video is shown in the app, with a loader while it runs.
- **Cleanup**: the uploaded image is deleted from storage after the video is fetched.

## Tech stack

| Layer | Tool |
| --- | --- |
| Framework | [Next.js](https://nextjs.org) 15, React 18 |
| Video generation | [Eachlabs](https://docs.eachlabs.ai/flow/getting-started) workflows |
| Storage | [Firebase Storage](https://firebase.google.com/docs/storage/web/start) |
| Styling | [Tailwind CSS](https://tailwindcss.com) |
| Icons | [Lucide](https://lucide.dev) |

## Getting started

### Prerequisites

- Node.js 18 or later
- An Eachlabs account with an API key and a workflow id
- A Firebase app with [Storage](https://firebase.google.com/docs/storage/web/start) enabled

### Installation

```bash
git clone https://github.com/Studio1HQ/ai-image-to-video.git
cd ai-image-to-video
npm install
```

### Environment variables

Copy `env.example` to `.env.local` and fill it in.

| Variable | Description |
| --- | --- |
| `EACH_API_KEY` | Eachlabs API key. |
| `EACH_WORKFLOW_ID` | Id of the Eachlabs workflow that creates the video. |
| `NEXT_PUBLIC_FIREBASE_API_KEY` | Firebase web app API key. |
| `NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID` | Firebase messaging sender id. |
| `NEXT_PUBLIC_FIREBASE_APP_ID` | Firebase app id. |

`src/app/firebase.ts` also contains the Firebase `authDomain`, `projectId`, `storageBucket` and `measurementId`. Replace them with the values from your own Firebase app config.

### Run

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) and click "Try now". Other scripts: `npm run build`, `npm run start` and `npm run lint`.

## How it works

1. `src/app/create/page.tsx` uploads the image to Firebase Storage under `images/<id>/image` and gets its URL.
2. It posts `{ image, effect }` to `/api`, where `effect` is your prompt.
3. `src/app/api/route.ts` calls `https://flows.eachlabs.ai/api/v1/<workflow id>/trigger` with your API key and returns the trigger id.
4. The page then calls `GET /api?triggerId=...`, which reads the workflow execution from Eachlabs and returns the output URL of the first step.
5. The video URL is rendered by `Result.tsx`.

## Resources

- [Eachlabs workflows](https://docs.eachlabs.ai/flow/getting-started): getting started with Eachlabs Flow.
- [Firebase Storage for the web](https://firebase.google.com/docs/storage/web/start): set up Storage.

<br />

---

<div align="center">

<a href="https://studio1hq.com">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Studio1HQ/website/main/brand/studio1-logo-on-dark.svg" />
    <img src="https://raw.githubusercontent.com/Studio1HQ/website/main/brand/studio1-logo-on-light.svg" alt="Studio1" width="160" />
  </picture>
</a>

Built by **[Studio1](https://studio1hq.com)**, the technical content and DevRel partner for devtool teams. Made with [Eachlabs](https://eachlabs.ai).<br />
Browse more open-source examples at [github.com/Studio1HQ](https://github.com/Studio1HQ).

[![Website](https://img.shields.io/badge/studio1hq.com-0b0807?style=for-the-badge&logo=googlechrome&logoColor=white)](https://studio1hq.com)
[![Book a call](https://img.shields.io/badge/Book_a_strategy_call-f97316?style=for-the-badge&logo=googlecalendar&logoColor=white)](https://cal.com/studio1/collab)
[![X](https://img.shields.io/badge/%40Studio1HQ-141414?style=for-the-badge&logo=x&logoColor=white)](https://x.com/Studio1HQ)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0a66c2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/company/studio1hq/)

<sub><a href="https://studio1hq.com">studio1hq.com</a> · Technical content, docs, video and DevRel for devtools</sub>

</div>
