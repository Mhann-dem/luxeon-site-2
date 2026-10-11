# Luxeon website

Luxeon's website is a static site made from six standalone HTML pages. There is
no build step, package manager, server-side application, or database in this
repository. CSS and JavaScript are embedded in the pages.

## Pages

| File | Purpose |
| --- | --- |
| [index.html](./index.html) | Home page and overview of Luxeon's work |
| [about.html](./about.html) | About Luxeon and its approach |
| [services.html](./services.html) | Research, analytics, software, mobile, and applied AI services |
| [products.html](./products.html) | Consulting and research products, including the planned database |
| [database.html](./database.html) | Preview of the proposed research database and early-access form |
| [content.html](./content.html) | Research-video library page |

## Preview locally

Open `index.html` directly in a browser, or serve the repository root with a
static HTTP server. For example, if Python is installed:

```sh
python -m http.server 8000
```

Then open `http://localhost:8000`. No dependencies need to be installed.

## Verified implementation status and launch gaps

This status is based on the files in this repository; it does not verify what
may be deployed elsewhere.

| Area | Current state | Needed before launch |
| --- | --- | --- |
| Website | Six static HTML pages with embedded CSS and JavaScript. | Choose/confirm a static host and deployment domain. |
| Database and API | The research database page is a preview. There is no backend, database, dataset ingestion, or API implementation here. The displayed request/response is illustrative page content. | Define the data model, sources and licenses, quality checks, refresh/versioning process, search and API contracts, authentication, rate limits, operations, backups, and access controls. Confirm the sample date, row count, and sources before presenting them as real. |
| Early-access signup | The page has no configured remote endpoint (`SIGNUP_ENDPOINT` is `null`). Its fallback saves the entered name and email only in that visitor's browser `localStorage`, then displays a success message. It does not create a central mailing list. | Connect a real form/CRM endpoint, handle unsuccessful HTTP responses, add server-side validation and spam protection, and publish an appropriate privacy notice. Test successful and failed submissions. |
| Free content | The six video cards use `REPLACE_WITH_ID_*` YouTube IDs. They are placeholders, not working video links. | Add real videos and IDs, verify titles/descriptions and permissions, then test playback and keyboard interaction. |
| SEO and sharing | Pages have page-specific titles and descriptions. Open Graph sharing metadata and a text-only Twitter card are also set per page. | Confirm the production hostname before adding canonical URLs and an absolute-URL sitemap. Publish and test `robots.txt` and the sitemap, register the site with Google Search Console and Bing Webmaster Tools, and provide a production-hosted social preview image. |
| Quality and maintenance | There is no application build or test setup. Shared CSS/JavaScript and a large embedded SVG are repeated in the HTML pages. | Test all pages and forms on the production host. Consider extracting shared assets and add automated HTML/link checks if the site will be maintained frequently. |

## SEO notes

Keep each page's `<title>` and meta description unique and accurate when page
content changes. The social preview title and description should remain aligned
with those values. Canonical tags and a sitemap are intentionally not included:
they must use the confirmed production URL, not a guessed or local URL. After
deployment, verify page indexing, mobile rendering, metadata previews, HTTPS,
and redirects for the preferred hostname.
