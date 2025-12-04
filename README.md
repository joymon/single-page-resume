# Single‑Page Resume (Hugo)
Data‑driven single‑page resume built with Hugo (JAMstack). Ideal for quickly publishing a professional profile with clean theming and zero server runtime. Live sample: [https://joymon.github.io/single-page-resume/](https://joymon.github.io/single-page-resume/)

![sample.png](/sample.png)

## Features
- Data‑first content via `data/resume.json`
- Orbit theme layouts in `themes/hugo-orbit-theme`
- i18n support under `themes/hugo-orbit-theme/i18n/*.yaml`
- GA4‑ready (see Analytics note below)
- Static output in `public/` (ignored by Git)

## Prerequisites
- Hugo Extended (tested with v0.152.2)
- Windows PowerShell (commands below) or preferred shell
- Git (optional, for deployment/Pages)

## Getting Started

Below are the steps to get your single page resume.

- Clone the repo
- Change the data/resume.json file with your details
- Get your profile photo rename it to profile.png and place at [/static/assets/images](/static/assets/images)
- Modify config.toml with your details. Enable or disable of sections can also be done there.
- Preview locally by running `hugo serve -D` from the repo root.

## Hosting

### In free GitHub pages
- Use the .github/workflows folder to do CI&CD
- Change the baseurl in config.toml file to be same as your GitHub pages url

### Anywhere else
- Change the baseurl in config.toml file to be same as your website url
- Run `hugo -D` to build the site
- It will publish the site to /public folder
- Upload the /public folder to your hosting space

## Dev Environment

- [Hugo Extended](https://gohugo.io/getting-started/quick-start/) — ensure your `hugo version` output includes "extended"
    - Tested with v0.152.2

## Install Hugo (Windows PowerShell)

```powershell
# Option 1: Winget (recommended)
winget install Hugo.Hugo.Extended

# Verify installation (look for "extended")
hugo version
```
More [installation options](https://gohugo.io/installation/).

## FAQ
- Hide sections: toggle flags in `config.toml` (e.g., enable/disable `projects`, `awards`).
- Analytics (GA4): Hugo warns if UA IDs are used. Configure GA4 using Hugo services; if not configured, the site builds without analytics.

### GA4 Configuration Example (Hugo)
Add to `config.toml`:

```
googleAnalytics = # Your GA4 Measurement ID
```
## Credits

- Theme: https://github.com/aerohub/hugo-orbit-theme

## License
This project uses the license in `LICENSE`. Reuse is permitted under the stated terms.
