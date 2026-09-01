# Gary's Family Resort Preview Site

This folder is a complete, deployable static website. Copy the contents of this folder into the root of a new repository.

## Included pages

- Homepage: `/`
- Menu and prices: `/menu/`
- Cabins: `/cabins/`
- Privacy policy: `/privacy-policy/`

No build step or package installation is required. The site uses plain HTML, CSS, JavaScript, and local image assets.

## Deploying

The repository can be published through any static host, including GitHub Pages, Netlify, Cloudflare Pages, or another provider.

Use these settings when a provider asks:

- Build command: none
- Publish directory: repository root
- Framework preset: none or static HTML

This package includes a `CNAME` file for `davisiantech.com`, along with canonical URLs, social-sharing metadata, `robots.txt`, and `sitemap.xml` configured for that domain.

Before publishing, point the DNS records for `davisiantech.com` to the selected hosting provider. The exact DNS records depend on that provider.

## Menu, announcement, and hours updates

The file `.github/workflows/menu-refresh.yml` checks Gary's published Google Sheet every 30 minutes and updates:

- Menu items and prices
- Announcement text and dates
- Regular and special hours
- Zipline hours
- Season dates

For GitHub Actions to commit those updates, enable read and write workflow permissions in the new repository under:

`Settings > Actions > General > Workflow permissions`

The current published data is already included in `assets/js/menu_data.js`, so the site works immediately even before the workflow runs.

## Instagram updates

The current Instagram images and feed data are included. Automatic Instagram updates are optional.

To enable them, add these repository secrets:

- `INSTAGRAMACCESSTOKEN`
- `GH_PAT`

Then enable the workflow in `.github/workflows/instagram-refresh.yml`. Without those secrets, leave that workflow disabled and the included images will continue to display.

## Local preview

Run a basic static server from the repository root, then open its local URL. Opening `index.html` directly also works for the main content, but a local server is recommended because the Instagram feed is loaded from a JSON file.
