# DEVCON Manila — Coming Soon

A single-file, dark-themed "coming soon" landing page for **DEVCON Manila Chapter**, built around an orbiting-planets motif that echoes the four colored dots in the official DEVCON wordmark (yellow, orange, violet, green). The chapter logo sits at the center as a glowing core, with each dot color represented as a planet on its own orbit ring.

![theme](https://img.shields.io/badge/theme-dark-0d0720) ![type](https://img.shields.io/badge/type-single--file%20HTML-8b5cf6) ![status](https://img.shields.io/badge/status-coming%20soon-7cb518)

## ✨ Features

- **Orbit system** — four CSS-animated rings, each carrying a planet colored to match the DEVCON logo dots, rotating at different speeds and directions around the chapter logo.
- **Glowing core** — the DEVCON logo sits center-stage with a soft pulsing violet glow, like a sun anchoring its planets.
- **Live starfield** — a lightweight canvas-based twinkling star background.
- **Countdown timer** — days / hours / minutes / seconds to your launch date, updated every second.
- **Notify-me form** — collects an email address client-side (front-end only — wire it up to your own backend or email service, see [Connecting the form](#connecting-the-notify-form) below).
- **Fully responsive** — scales down gracefully to mobile, with the orbit system resizing fluidly.
- **Accessible by default** — visible keyboard focus states, `aria-live` status messages, and full support for `prefers-reduced-motion` (orbits and pulsing stop for users who've asked for reduced motion).
- **Zero dependencies, zero build step** — it's one `.html` file. The logo is embedded directly as a base64 image, so there's nothing else to host or link.

## 🚀 Quick start

1. Clone or download this repo.
2. Open `index.html` directly in any browser — no build step, no server required.
3. To deploy, drop `index.html` into any static host (GitHub Pages, Netlify, Vercel, or a plain web server).

```bash
git clone https://github.com/your-org/devcon-coming-soon.git
cd devcon-coming-soon
open index.html   # or just double-click it
```

### Deploying to GitHub Pages

1. Push this repo to GitHub.
2. Go to **Settings → Pages**.
3. Set the source branch to `main` (or wherever `index.html` lives) and the folder to `/ (root)`.
4. Your coming-soon page will be live at `https://your-org.github.io/devcon-coming-soon/`.

## 🛠 Customizing

Everything lives in `index.html`. Here's where to look for common edits:

| What you want to change | Where to look |
|---|---|
| Launch date for the countdown | `const LAUNCH_DATE = new Date('2026-09-01T09:00:00+08:00')` in the `<script>` section |
| Headline / subtext copy | `<h1>` and `<p class="sub">` inside `<main>` |
| Social links | The `<div class="socials">` block — swap the `href` values |
| Colors / theme tokens | The `:root { ... }` block at the top of `<style>` — all colors are CSS variables |
| Orbit speed / ring size | `.spin-1` through `.spin-4` (`animation-duration`) and `.ring-1` through `.ring-4` (`width` / `height`) |
| Logo | Replace the base64 `data:image/png;base64,...` strings in the two `<img>` tags with your own image, or swap in a relative file path like `src="logo.png"` |

### Connecting the notify form

The form currently only shows a success message on submit — it doesn't send the email anywhere. To actually collect signups, replace the `TODO` block inside the `notify-form` submit handler with a request to:

- A form service like **Formspree**, **Getform**, or **Basin** (no backend needed), or
- Your own API endpoint / serverless function, or
- An email marketing tool's signup API (Mailchimp, Buttondown, etc.)

```js
// Example using a form service:
fetch('https://your-form-endpoint.example.com', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ email })
});
```

## 🎨 Design notes

The palette and motion were chosen to extend the existing DEVCON Manila brand rather than invent a new one:

- **Background** — a near-black violet (`#07040f` → `#160b34`) instead of plain black, so the page reads as "deep space" rather than generic dark mode.
- **Planets** — exact colors lifted from the four dots in the DEVCON wordmark (`#f2c811` yellow, `#f2811e` orange, `#7b2fe0` violet, `#7cb518` green), each on its own ring with a distinct orbit speed.
- **Type** — Space Grotesk for display headings and numerals (countdown, headline), Inter for body copy and UI text.
- **Motion** — orbits, a breathing core glow, and a twinkling starfield run continuously but subtly; everything respects `prefers-reduced-motion`.

## 📄 License

Use and adapt freely for DEVCON Manila Chapter community purposes. Replace the logo and social links with your chapter's own assets before deploying.

---

Built with 💜 for the Manila developer community.
