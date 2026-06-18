# Blog

Static Astro blog with Markdown/MDX content.

## Local development

```sh
npm ci
npm run dev
```

Articles live in `src/content/blog`. Use `.md` for normal posts and `.mdx` when a post needs components.

## Repository configuration

Configure these GitHub Actions repository secrets:

- `SITE_URL`: canonical production URL, including `https://` and without a trailing slash.
- `BLOG_DEPLOY_WEBHOOK_URL`: production notification endpoint, including `/_hooks/blog`.
- `BLOG_DEPLOY_WEBHOOK_SECRET`: the same random value installed on the VPS.

Optionally configure `PUBLIC_UTTERANCES_REPO` as a repository variable in public `owner/name` form. Install the Utterances GitHub App on that repository before enabling it.

Pushes to `main` build the site and publish `blog.tar.gz` plus `blog.tar.gz.sha256` as a GitHub Release. The Action then sends an HMAC-signed notification so the VPS pulls the release. GitHub Actions has no VPS login credentials.
