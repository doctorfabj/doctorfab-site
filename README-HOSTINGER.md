# Doctor Fab: Hosting and Publishing

Owner instructions are in [OWNER-GUIDE.md](OWNER-GUIDE.md). Assistants must first
read [AGENTS.md](AGENTS.md); takeover steps are in
[START-HERE-DR-FAB.md](START-HERE-DR-FAB.md).

## Existing Architecture

The site at https://doctorfab.org/ uses static HTML, CSS, vanilla JavaScript, PDFs,
images, and audio. Hostinger runs `api/companion.php` for server-side Anthropic
requests. There is no build step or database. This is a custom-code website,
not the separate Hostinger Website Builder project. `HOSTINGER-COPY.md` is a
historical copy kit, not a current deployment procedure.

The repository root publishes into `public_html`. `main` is the live branch:
**a push to `main` triggers a live Hostinger deployment**. Do not upload a ZIP,
replace the website, or create another repository for routine updates.

## Deployment and Ownership Transfer

1. Use the existing website repository in your GitHub account. Inspect status
   and the actual remote before starting; do not rely on an old account URL.
2. In Hostinger's doctorfab.org dashboard, inspect its Git connection (commonly
   under Advanced / Git). Keep the repository root, `main`, and the existing
   `public_html` destination. Reauthorize under the owner's own GitHub login after
   transfer if needed. Preserve the private configuration above `public_html`.
3. For each approved change, preview and test, review the diff, stage only intended
   files, and commit. Run `git status --short --branch` before every push. Stop
   on unexpected changes or a rejected push. Never force-push or reset history.
4. Push only after approval to publish this scope. Verify Hostinger's deployment
   result and the changed live files, not just GitHub's success message.
5. After transfer, prove a documentation-only deployment works using the owner's
   connection. Remove previous collaborators and stale access only after the new
   connection works. Enable two-step login and replace the Anthropic key.
6. Make the repository private last. Ensure Hostinger has access to the private
   repository and prove another approved deployment succeeds afterward.

For current dashboard instructions, consult
[Hostinger's Git publishing guide](https://www.hostinger.com/support/1583302-how-to-deploy-a-git-repository-in-hostinger/).
Do not change DNS, SSL, or CDN as part of an ordinary deployment. The apex domain
is canonical, `www` redirects to it, and the CDN was intentionally left off.

## Local Preview

From the project root:

```sh
python3 -m http.server 8765 --bind 127.0.0.1
```

Open http://127.0.0.1:8765/index.html. The Mac helper
`scripts/start-local-preview.command` does the same. Choose an unused port and
stop the process when finished. This only tests static content: it does not run
PHP or enforce `.htaccess`, and can expose PHP source. Never put private keys in
this preview folder or bind the server publicly. A built-in PHP preview server
does not test Apache/LiteSpeed rewrite rules either.

## Private Companion Configuration

The intended production layout is:

```text
website account folder/
    doctorfab-companion-config.php    PRIVATE: key, model, rate-limit salt
    public_html/
        config.example.php           placeholders only
        api/companion.php
        api/companion-system-prompt.md
        storage/.htaccess
```

In Hostinger File Manager, go one level above `public_html` and open
`doctorfab-companion-config.php`. The owner pastes her key directly into the
quoted `anthropic_api_key` value there, never into chat. For a key replacement,
preserve all other values, quotes, and punctuation. If the file is missing, stop
and ask; do not create a competing configuration.

For an explicitly approved fresh recovery setup only, copy the placeholder
structure from `config.example.php` into that private file, enter the key there,
and set a new long random `rate_limit_salt`. Keep backups containing secrets outside
the public root and repository. PHP cURL and outbound HTTPS must be available.

`load_config()` in `api/companion.php` checks the private sibling file first, then
the legacy fallback `public_html/config.php`. Both real filenames are ignored by
Git; `.htaccess` denies direct access to sensitive PHP filenames in the public
root. Do not create both configurations or put a real key in `config.example.php`.

`anthropic_model` in the private file selects the active model. The documented
model and code/template fallback are `claude-haiku-4-5-20251001`. The private value
overrides the fallback. For retirement or account-availability issues, follow the
approval, compatibility, pricing, and testing steps in [AGENTS.md](AGENTS.md).
Do not assume a key replacement requires a model change.

Create keys in [Claude Console](https://platform.claude.com/) and set a low
[account spending limit](https://platform.claude.com/settings/spend-limits).
After the new key is verified, the previous key's owner must revoke it. Request
limits in this application are not a guaranteed account-wide billing cap.

## Safety and Data Boundaries

The editable prompt is `api/companion-system-prompt.md`. Preserve the non-therapy,
non-diagnostic role, choice to pause or stop, and crisis routing to real human
help. Frontend and server checks can return a fixed crisis response without an
Anthropic call. They are safeguards, not a complete clinical safety validation.

Current limits: 30,000 request bytes, last 8 messages, 900 characters per message,
5,000 total characters, 10 requests per 600 seconds and 40 per rolling day for
the combined IP/session hash. Only rate-limit hashes and timestamps are stored
by the application in `storage/companion-rate-limit.json`; message text is sent
to Anthropic but not intentionally logged or saved by the application. Do not
claim provider zero retention or compliance without separate verification.

`companion.js` can offer a local prewritten exercise if the API fails. Seeing a
helpful paragraph alone does not prove the AI connection works; inspect a real
successful POST response containing `reply` and the owner's Anthropic usage.

## Internal Markdown Protection

Immediately after the storage rule, the root `.htaccess` contains:

```apache
# Keep internal guide and notes files (.md) out of public view.
RewriteRule \.md$ - [F,L,NC]
```

This denies web requests for all `.md` paths, including nested prompt files.
PHP can still read the prompt from disk. The files remain readable in your GitHub
account until the repository is made private; website blocking is not repository
privacy. It also does not protect HTML, PDFs, images, or unlisted audio pages.

## Verification After Publishing

- Confirm the homepage, coaching, Sanctuary, Resources, Lexicon, article pages,
  and audio page still return HTTP 200. Check linked CSS/JS and PDF downloads.
- Confirm `/AGENTS.md`, `/OWNER-GUIDE.md`, `/START-HERE-DR-FAB.md`,
  `/README-HOSTINGER.md`, `/HOSTINGER-COPY.md`, and
  `/api/companion-system-prompt.md` return HTTP 403, not their contents. Test both
  an ordinary path and a query-string variant; check HTTP/`www` behavior too.
- Send a harmless synthetic grounding request to `/api/companion.php` using POST
  with a JSON `messages` array of `{role: "user", content: "..."}`. Expect HTTP
  200 with a nonempty `reply`, not an error or local fallback. Never use client
  records, private conversation text, or a key in the test request.
- Send a synthetic crisis example and confirm `crisis: true`, a pause in the
  exercise, and the existing 988/emergency guidance. Never remove this behavior.
- For a key change, confirm the new owner's Anthropic usage reflects the test.
- Check for unexpected changes before any follow-up push. If verification fails,
  stop and explain the evidence. Propose a narrow repair or a reviewed revert;
  do not weaken access rules or safety checks to hide the failure.

The ownership handoff leaves the separate visual audit unfinished. Consult the
owner guide for pending transfer, access, key, and business decisions.
