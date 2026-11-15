# Doctor Fab: Instructions for Future Assistants

## Ownership and Working Agreement

Dr. Fab owns the content, business decisions, accounts, and technical direction of
doctorfab.org. She is not a programmer. Explain work in plain English, do the
technical work for her, and never assume access to an earlier chat.

Read [OWNER-GUIDE.md](OWNER-GUIDE.md), [START-HERE-DR-FAB.md](START-HERE-DR-FAB.md),
and [README-HOSTINGER.md](README-HOSTINGER.md) before changing anything. Check the
current files and live state; dated notes are not proof of current configuration.

Standing rules:

- Say what will change, which visitors or accounts it affects, and whether it
  will cost money. Wait for an explicit yes before editing or changing settings.
- Show the tested changes before publishing. Obtain an explicit yes to publish
  unless the owner has already approved publishing that exact scope.
- Run `git status --short --branch` at the start and **before every push**. Review
  the diff and staged file list. Preserve unrelated work and stage named files.
- Never run `git reset --hard`, force-push, or rewrite shared history. Undo with
  a reviewed, approved revert commit. Do not delete someone else's work.
- Never ask her to paste keys, passwords, recovery codes, or login cookies into
  chat. Never print them, put them in screenshots, commit them, or send them to
  another service. She enters secrets directly in the provider's private form
  or Hostinger's private configuration file.
- Do not weaken the Companion's crisis handling, non-therapy boundaries, choice
  to stop, privacy protections, request limits, or rate limiting.
- Stop and ask when anything is unexpected: unknown changes, a different remote,
  missing private configuration, failed checks, new costs, or uncertain ownership.
  Do not improvise a destructive repair or silently expand the task.
- Do not buy services, transfer accounts, change DNS, change prices, publish new
  clinical claims, or collect sensitive information without specific approval.
- Keep internal documents free of credentials, personal computer paths, previous
  owner identifiers, and hard-coded project repository URLs. Say "your GitHub
  account"; discover the current remote locally without displaying credentials.

## What This Site Is

A custom HTML/CSS/vanilla-JavaScript website for Doctor Fab's trauma-informed
clinical work, parent coaching, resources, and reflection tools. Hostinger serves
the files for https://doctorfab.org/ and runs the PHP Companion endpoint. This is
not a Hostinger Website Builder project. There is no npm build, framework, CMS,
or database to set up for routine content changes.

The Companion sends limited conversation text to Anthropic on the server. It is
a supportive reflection tool, not a therapist, diagnosis service, or crisis
service. Contact pathways prepare email; they are not a patient portal, confirmed
booking, payment system, or automatically maintained mailing list.

## File Map

| File or folder | Purpose |
| --- | --- |
| `index.html` | Homepage, offers, contact pathways, and embedded Companion. |
| `autism-parent-coaching.html` | Parent coaching information and email inquiries. |
| `sanctuary.html` | Standalone Sanctuary and Companion. |
| `resources.html`, `resources/` | Resource directory and individual reading pages. |
| `lexicon.html`, `lexicon/` | Lexicon directory and longer articles. |
| `sanctuary-of-plenty.html` | Audio collection; unlisted does not mean access-protected. |
| `styles.css` | Shared design tokens, page layouts, and responsive styles. |
| `site.js` | Shared mobile navigation. |
| `companion.js` | Companion, local fallback exercises, contact interactions, and filters. |
| `assets/generated/` | Newer generated brand images and illustrations. |
| `assets/resources/` | Public downloadable PDFs. |
| `assets/sanctuary-of-plenty/` | Publicly reachable audio and artwork. |
| Other files in `assets/` | Earlier AI brand boards and source images; not all are used. |
| `api/companion.php` | Request validation, crisis response, rate limiting, Anthropic call. |
| `api/companion-system-prompt.md` | Clinician-editable AI role, voice, and safety instructions. |
| `config.example.php` | Placeholder-only private configuration template. Never add a real key. |
| `.htaccess` | HTTPS/apex redirects, cache rules, and private-file blocking. |
| `storage/.htaccess` | Additional protection for runtime rate-limit data. |
| `www/` | Existing alternate-host redirect files; preserve unless a change is approved. |
| `scripts/start-local-preview.command` | Mac helper for a local static preview. |
| `START-HERE-DR-FAB.md` | Owner's short takeover checklist. |
| `OWNER-GUIDE.md` | Plain-English operating guide and request examples. |
| `README-HOSTINGER.md` | Technical publishing, configuration, and verification notes. |
| `HOSTINGER-COPY.md` | Historical copy kit, not the current site or publishing instructions. |

An untracked `BOOKING_AND_PAYMENT_PLAN.md` may exist on the original computer.
It is an unpublished proposal, not an implemented payment feature. Do not stage,
publish, or turn its proposed prices into public offers without approval.

## Publishing and Local Preview

**Pushing to `main` publishes to the live website through Hostinger.** A successful
Git push alone does not prove deployment succeeded. Check Hostinger's deployment
result and the actual changed address. Use the current repository in your GitHub
account; do not assume an old owner's URL or saved authorization still works.

For an approved change: inspect status, make the smallest change, test locally,
show the diff and plain-English summary, confirm publishing approval, commit only
the intended files, run status again, and push normally. Check live pages and
affected features afterward. Leave DNS, SSL, and the intentionally disabled CDN
alone unless the owner approves a separate infrastructure change.

From the repository root, preview static content with:

```sh
python3 -m http.server 8765 --bind 127.0.0.1
```

Open http://127.0.0.1:8765/index.html. The double-click helper runs the same server.
If the port is occupied, choose another port; do not kill an unknown process.
Stop your preview when finished. The static preview **does not execute PHP or
enforce `.htaccess`** and can serve PHP source. Do not put secrets in its folder
or expose it beyond localhost. A PHP development server also does not enforce
Apache rewrite rules. Verify the real Companion and access rules on Hostinger.

For approved visual work, test desktop and mobile, keyboard navigation, focus,
image loading, navigation links, and relevant contact/download interactions.
Do not conduct a redesign or visual audit as part of an unrelated handoff task.

## Private Anthropic Configuration

Hostinger File Manager: open the website's files, then the folder immediately
above `public_html`. The intended private file is:

```text
doctorfab-companion-config.php
public_html/
    api/companion.php
    config.example.php
```

The private file contains `anthropic_api_key`, `anthropic_model`, and the
rate-limit salt. It is outside the published folder and must not be copied into
this repository. `api/companion.php` checks it first with
`dirname(__DIR__, 2) . '/doctorfab-companion-config.php'`. Its legacy fallback is
`public_html/config.php`, also ignored by Git and blocked by `.htaccess`.
If the expected private file is missing, stop and ask; do not create a second
configuration or print an existing one to discover which key is active.

The documented configured model and the repository's template/fallback are
`claude-haiku-4-5-20251001`. The private `anthropic_model` value takes precedence;
read only that non-secret value if verification is necessary. Do not infer the
active model from a successful reply or from the template alone.

If a model is retired or unavailable:

1. Separate model availability from exhausted credits, revoked keys, request
   limits, and hosting failures. Do not expose raw configuration or credentials.
2. Consult Anthropic's official [model retirement notices](https://platform.claude.com/docs/en/about-claude/model-deprecations)
   and the models available to the owner's account. Verify the exact replacement
   identifier, Messages API compatibility, supported parameters, and cost.
3. Explain the proposed change and cost, then wait for approval. Never silently
   upgrade to an expensive model or remove safety instructions to make it work.
4. Change `anthropic_model` in the private Hostinger file. Update the placeholder
   template, PHP fallback, and these guides to match in the approved change.
   Changing only the fallback does not override the private configuration.
5. Test a harmless normal request and the crisis bypass; confirm the disclaimer,
   stop controls, validation, and limits remain intact. Use synthetic input only.

The full AI prompt is `api/companion-system-prompt.md`. The Markdown web-access
rule does not prevent PHP from reading it from disk. Do not remove the rule to
repair the Companion. The application stores rate-limit hashes/timestamps, not
conversation text; Anthropic still receives the messages. Do not promise HIPAA
compliance, confidentiality, or zero provider retention without separate review.
The current session/IP limit is not an account-wide spending cap. Keep a low
Anthropic spending limit and monitor usage.

## Design and Content Rules

- Preserve the approved pink, coastal/Cape-inspired, calm and professional brand.
  Use clean imagery and readable typography; avoid fussy patterned backgrounds,
  low-resolution collages, or words baked into promotional images.
- Use only approved AI-generated Doctor Fab likenesses and brand imagery, never
  real headshots. The original pink/coastal boards are inspiration, not finished
  banners. Ask before introducing a new likeness or replacing approved imagery.
- Reuse the current CSS tokens: rose `#cc829a`, soft rose `#f8dfe7`, navy
  `#153947`, sea-glass `#8fb9b7`, shell `#fbf7f1`, paper `#fffdf9`; Georgia serif
  headings and the existing Inter/system sans-serif stack. Do not introduce a
  new framework or redesign for a small content edit.
- Write warm, direct, choice-oriented language. Describe actual support and
  offers, not the aesthetic itself. Avoid hype, guaranteed outcomes, invented
  credentials, testimonials, prices, or claims of therapeutic efficacy.
- Preserve accessibility, including useful alt text and keyboard skip navigation.
  A skip link should be available on keyboard focus, not simply deleted because
  it was reported as visible. Investigate that only during approved visual work.
- Let the owner approve clinical wording, business offers, and Companion prompt
  changes. Never pressure visitors or imply a monitored crisis service.

## Handoff Status

Prepared 2026-11-15. Hostinger and the domain already belong to the owner. Transfer
to your GitHub account and replacement of the previous owner's Anthropic key are
still outstanding at preparation. Reauthorize publishing under the owner's own
account, prove it works, remove previous access, enable two-step login, and make
the repository private last. Verify another publication after making it private.

The requested visual audit is unfinished and explicitly outside this handoff.
Earlier reports about the first-page image, background pattern, and visible skip
link need a separately approved review; do not treat old screenshots as proof of
the current appearance. A reachable page is not a completed visual or clinical
safety audit.
