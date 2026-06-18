# Blog

Static Astro blog with Markdown/MDX content.

## Local development

```sh
npm ci
npm run dev
```

Articles live in `src/content/blog`. Use `.md` for normal posts and `.mdx` when a post needs components.

## Repository variables

Configure these GitHub Actions repository variables:

- `SITE_URL`: canonical production URL, including `https://` and without a trailing slash.
- `PUBLIC_UTTERANCES_REPO`: optional public repository in `owner/name` form. Install the Utterances GitHub App on that repository before enabling it.

Pushes to `main` build the site and publish `blog.tar.gz` plus `blog.tar.gz.sha256` as a GitHub Release. The VPS pulls the latest release; GitHub Actions has no VPS credentials.
