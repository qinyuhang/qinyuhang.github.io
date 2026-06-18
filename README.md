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
- `BLOG_DEPLOY_WEBHOOK_URL`: production notification endpoint, including `/_hooks/blog`.
- `PUBLIC_UTTERANCES_REPO`: optional public repository in `owner/name` form. Install the Utterances GitHub App on that repository before enabling it.

Configure the Actions secret `BLOG_DEPLOY_WEBHOOK_SECRET` with the same random value installed on the VPS.

Pushes to `main` build the site and publish `blog.tar.gz` plus `blog.tar.gz.sha256` as a GitHub Release. The Action then sends an HMAC-signed notification so the VPS pulls the release. GitHub Actions has no VPS login credentials.
