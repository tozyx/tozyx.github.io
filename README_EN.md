# GenshinPiano Website

[简体中文](./README.md) | [English](./README_EN.md)

The official website repository for GenshinPiano, featuring software downloads, bilingual documentation, release notes, and an interactive 21-key practice studio with multiple instrument sounds.

- Website: [https://tozyx.github.io/](https://tozyx.github.io/)
- Application source: [tozyx/GenshinPiano](https://github.com/tozyx/GenshinPiano)
- Releases: [GitHub Releases](https://github.com/tozyx/GenshinPiano/releases)

> GenshinPiano is an unofficial fan-made project and is not affiliated with or endorsed by HoYoverse. This repository contains the website source code only, not the game itself or official game assets.

## Features

- Automatic browser-language detection with manual Chinese and English switching
- Product overview, downloads, FAQ, privacy policy, and other complete pages
- Searchable bilingual documentation
- Release information, downloads, and changelogs loaded from GitHub Releases
- Real application screenshots with an in-component language carousel
- Interactive 21-key practice studio supporting keyboard, mouse, and touch input
- Multiple in-game instrument sounds, follow mode, timed mode, seeking, and A/B looping
- Responsive desktop and mobile layouts with a landscape-focused mobile practice view
- Sitemap, robots.txt, basic SEO, and automated GitHub Pages deployment

## Technology

- [Astro](https://astro.build/)
- TypeScript
- Native HTML, CSS, and browser JavaScript
- pnpm
- GitHub Actions and GitHub Pages

The website is generated as static output and does not require an application server. Current release data is read from the public GitHub API in the browser, with a fallback link to GitHub Releases when the API is unavailable.

## Local Development

Requirements:

- Node.js 24 LTS; minimum supported version: 22.12
- pnpm 11

Install dependencies:

```powershell
pnpm install
```

Start the development server:

```powershell
pnpm dev
```

The website is available at:

```text
http://localhost:4321
```

Create a production build:

```powershell
pnpm build
```

The generated site is written to `dist/`.

Preview the production build locally:

```powershell
pnpm preview
```

## Project Structure

```text
.
├─ public/                    Static assets, icons, audio, and screenshots
├─ src/
│  ├─ components/            Navigation, footer, practice, showcase, and release components
│  ├─ layouts/               Shared page layout and SEO metadata
│  ├─ pages/                 Chinese pages
│  │  └─ en/                 English pages
│  └─ styles/                Global styles and responsive layouts
├─ .github/workflows/        GitHub Pages build and deployment workflow
├─ astro.config.mjs          Astro configuration
└─ package.json              Project scripts and dependencies
```

## Pages and Languages

Chinese pages use root paths such as `/features/`, `/download/`, `/docs/`, `/changelog/`, and `/faq/`. English pages use the `/en/` prefix, such as `/en/docs/`.

The selected language is saved in browser local storage. On the first visit, the website selects Chinese or English from the browser's preferred language.

## References and Acknowledgements

The online practice studio was designed and implemented with reference to these open-source projects:

- [Specy/genshin-music](https://github.com/Specy/genshin-music): reference for the Genshin 21-key layout, note-icon handling, instrument sound configuration, and interaction design. Some icons and audio samples used by the practice studio also originate from this project. Many thanks to Specy and all contributors.
- [VanillaNahida/WindsongLyre-Sim](https://github.com/VanillaNahida/WindsongLyre-Sim): referenced during early research for its web instrument interface and resource organization. Many thanks to VanillaNahida and all contributors.

The GenshinPiano website structure and practice implementation were developed independently. See [THIRD_PARTY_NOTICES.md](./THIRD_PARTY_NOTICES.md) for detailed attribution, licensing, and copyright information.

## License

Original website code in this repository is released under the [MIT License](./LICENSE). Third-party icons, audio, and other assets retain their respective copyright and licensing terms. See [THIRD_PARTY_NOTICES.md](./THIRD_PARTY_NOTICES.md) for details.

## Deployment

`GPiano` is the current website deployment branch. Pushing to this branch triggers GitHub Actions to:

1. Install pnpm and Node.js 24
2. Install dependencies using the lockfile
3. Run `pnpm build`
4. Upload `dist/`
5. Deploy the site to GitHub Pages

The deployment workflow can also be started manually from GitHub Actions.

Before publishing, run:

```powershell
pnpm build
git diff --check
```

## Content Maintenance

- Chinese pages: `src/pages/`
- English pages: `src/pages/en/`
- Full documentation: `src/pages/docs.astro` and `src/pages/en/docs.astro`
- Shared visual styles: `src/styles/global.css`
- Application screenshots: `public/screenshots/`
- Download and changelog data: [GenshinPiano Releases](https://github.com/tozyx/GenshinPiano/releases)

When adding a page, update `src/pages/sitemap.xml.ts` and both language navigation menus.