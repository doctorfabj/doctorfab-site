# Your Doctor Fab Website

You are the owner of Doctor Fab: its words, images, offers, accounts, and technical
decisions. You do not need to learn programming to direct the work. Codex can make
the changes, explain them, and test them. You decide what gets published.

This guide is for you. [AGENTS.md](AGENTS.md) is the instruction sheet your future
Codex assistant must read. [START-HERE-DR-FAB.md](START-HERE-DR-FAB.md) is your short
takeover checklist. These files travel with the website files; your new assistant
does not need this project's old chat.

## Your Accounts

| Account | What it does and what you should control |
| --- | --- |
| Hostinger and doctorfab.org | Keep the website online and renew its address. These already belong to you. Check your renewal dates, payment method, recovery email, and backups. |
| Your GitHub account | Holds the master website files and their saved versions. Accept the existing site's ownership transfer; do not create a replacement website. Publishing an update to the version named `main` sends it to Hostinger. |
| Your ChatGPT / Codex account | Lets you direct your assistant to work on your copy of the website. Use your own login on your own computer. It does not automatically transfer or own your other accounts. |
| Your Anthropic account | Pays for the website's AI Companion. Its secret API key is the permission the website uses to request replies. This is separate from ChatGPT and from a personal Claude chat subscription. |
| Your website email inbox | Receives inquiries. The current website points to `doctorfabj@gmail.com`. Confirm you can sign in, send, receive, and recover this inbox. Owning the domain does not automatically give you an inbox such as `hello@doctorfab.org`. |

Keep passwords and recovery codes in your own password manager. Turn on two-step
login everywhere it is available. Do not send passwords or secret keys to Codex,
email them, or include them in screenshots.

If someone else has signed in using your account, removing them as a collaborator
is not enough. After you have confirmed your own access, use each account's
security settings to sign out old devices and replace any shared passwords.
Check that recovery email addresses and phone numbers are yours. Keep a working
recovery method throughout. Ask your assistant to help review any old publishing
permissions without removing the connection that now belongs to you.

## One-Time Setup

1. Accept the website transfer into your GitHub account. Check that the website's
   settings show you as its owner. Keep the existing name if possible.
2. Install [GitHub Desktop](https://desktop.github.com/) and sign in with your
   GitHub account. Choose **Clone a repository**, select the transferred website,
   and save its copy in Documents. Here, "clone" just means making a working copy
   on your computer. Do not download a ZIP instead; the working copy needs its
   saved-version connection.
3. Install Codex using the [official setup guide](https://developers.openai.com/codex/quickstart)
   and sign in with your own ChatGPT account. Open the website folder you just
   downloaded as your project. You do not need an OpenAI API key for this setup.
4. Start with the request below. Your assistant should read the three guides,
   check the current files, and explain what it found without making changes.

> I own Doctor Fab. Read AGENTS.md, OWNER-GUIDE.md, and START-HERE-DR-FAB.md first.
> Explain the current setup in plain English. Make no changes yet. For future
> work, tell me what you propose and wait for my yes before changing anything.
> Ask again before publishing unless I have explicitly approved that publication.

5. In Hostinger, open doctorfab.org's dashboard and its Git publishing connection.
   Make sure it uses your GitHub account, the transferred website, and `main`.
   Reconnect or reauthorize with your own login if needed. Do not create a new
   Hostinger Website Builder site or change the domain settings. Ask your assistant
   to guide you, stopping if anything looks different.
6. Prove you can publish independently before removing old access. Use the
   publishing-test request below. Check that Hostinger reports a successful
   update from your account; seeing the old website still online is not enough.

> Help me test publishing from my own accounts. Propose a tiny update to an
> internal guide that changes nothing visitors see, wait for my yes, publish it,
> and confirm Hostinger received that exact update. Then check the normal pages,
> the Companion, and that the internal guides are still blocked on the website.

GitHub keeps the previous owner as a collaborator after a transfer. Once your
publishing test passes, remove that access in the website's GitHub settings.
Review other people and old publishing permissions in GitHub and Hostinger, too;
do not remove the working connection owned by you. Then complete the key and
two-step-login steps below. **Make the GitHub project private last**, and repeat
the publishing test afterward so you know Hostinger can still read it.
See [GitHub's transfer guidance](https://docs.github.com/en/repositories/creating-and-managing-repositories/transferring-a-repository)
and [Hostinger's publishing guidance](https://www.hostinger.com/support/1583302-how-to-deploy-a-git-repository-in-hostinger/).

Making GitHub private does not make your website, audio, or downloads private,
and cannot recall copies people already downloaded while it was public.

## How Everyday Changes Work

Describe the change in ordinary language. Codex explains its plan; you say yes.
It makes a preview on your computer and checks the change. Review that preview.
When you are satisfied, say: **"Yes, publish these changes and check the live
website."** Saving work locally is not the same as publishing it. Sending it to
GitHub's `main` version is the step that updates the live site.

Keep one clear task at a time. Do not let two assistants change or publish the
same files simultaneously. Your assistant must pause when it finds something
unexpected. It must not erase history to fix a problem.

### Phrases You Can Use

**Change wording**

> On [page], replace "[old wording]" with "[new wording]". Keep the design and
> everything else unchanged. Tell me the plan and wait for my yes. Show me the
> preview before asking to publish.

**Add a page**

> Add a page called [name] using this content: [content]. Match the existing
> Doctor Fab design. Show me where it would appear in the menu and explain the
> plan before making changes. Do not invent services, prices, or clinical claims.

**Swap an image**

> Replace the image in [location] with the attached approved AI-generated image.
> Do not use a real headshot. Explain the change first, then check its sharpness,
> cropping, description for screen readers, and appearance on phones and computers.
> Show me the result before publishing.

**Add a PDF**

> Add this PDF to [page] with a download link labeled [title]. Tell me where it
> will be stored and linked, then wait for my yes. This is intended to be public;
> check with me if it contains personal details. Test the download before asking
> to publish.

**Edit the Companion's instructions**

> Review api/companion-system-prompt.md. I want the Companion to [describe change].
> Show me the proposed wording first and wait for my yes. Preserve its non-therapy
> boundaries, crisis response, privacy safeguards, and the visitor's choice to
> stop. After approval, test ordinary and crisis examples before publishing.

**Undo the last change**

> Identify the most recent published change and explain exactly what undoing it
> would affect. Wait for my yes, then undo only that change while keeping the
> saved history. Never erase history or overwrite unrelated work. Confirm the
> live site afterward.

## Put Your Own Anthropic Key in Place

An API key is a secret permission code, not wording for the website. The previous
owner's key is still in use at handoff preparation. Replace it before completing
the separation. A key previously shared in chat should be retired, even if it has
continued to work.

1. Open [Claude Console](https://platform.claude.com/) in your browser and sign in
   or create your own Anthropic account. Check that billing and recovery details
   belong to you. This is the developer console, not just the Claude chat app.
2. Add billing or credits as requested there. Set a low monthly spending limit
   that you are comfortable with, for example $10 if the account permits it, in
   [spending limits](https://platform.claude.com/settings/spend-limits). This is a
   suggested cap, not a prediction of your bill. Check any workspace limit too.
   Keep automatic credit top-ups off unless you deliberately want them.
3. Create a new API key in the Console's API Keys area. Keep it private in your
   password manager. Do not paste it into a chat or into a website page.
4. In Hostinger, open **Websites**, find **doctorfab.org**, and open **File
   Manager** from its Tools menu or dashboard. The file manager may open in a new
   tab. Open the website's files, then go up one folder from `public_html`.
5. Open **`doctorfab-companion-config.php`**, which should sit beside the
   `public_html` folder, not inside it. If it is missing or more than one likely
   file exists, stop and ask your assistant for help without sharing its contents.
   There is an older alternate location, `public_html/config.php`; do not create
   both or guess which one the website uses.
6. In that private file, find **`anthropic_api_key`**. Replace only the text
   between the quotes after the arrow with your new key. Keep the quotes, comma,
   and all other settings unchanged. Save the file. Do not edit `config.example.php`:
   that is a public example containing placeholders, not the working private file.
7. Open the live Sanctuary and try a simple, non-personal grounding request. Ask
   Codex to confirm the server actually returned an AI reply: the site can also
   show a prewritten exercise when AI is unavailable. Check your Claude Console
   usage to confirm your account received the request.
8. Once your key works, have the previous owner revoke the old key in their
   Anthropic account. If the replacement fails, keep the new key private and ask
   for help. Do not paste either key into chat.

The model name is in the same private file beside **`anthropic_model`**. The
documented model is **`claude-haiku-4-5-20251001`**. Do not change it just to replace
the key. If Anthropic sends a retirement notice or the Companion stops working,
ask:

> Check whether the Companion's model is still available to my Anthropic account.
> Explain any replacement, price change, and testing needed before changing it.
> Follow the recovery steps in AGENTS.md and keep all safety behavior intact.

## If Something Breaks

1. Do not keep publishing guesses. Note what you clicked, the page address, the
   time, and what happened. A screenshot is useful only if it contains no private
   information, keys, or client messages.
2. Ask Codex: **"The site is having this problem: [description]. Investigate
   without changing anything. Tell me the cause you can verify, the safest fix,
   and whether you need my approval to restore the last working version."**
3. If it started after a website update, use the undo request above. Your assistant
   should restore only the relevant change and keep the saved history.
4. If the entire site is unavailable, check Hostinger's website status, renewal,
   and latest publication result. Contact Hostinger support if necessary. Do not
   change the domain address settings or security certificate by trial and error.
5. If only the Companion fails, check Anthropic credits, spending limits, key
   status, and model notices. The rest of the site can still work. Do not remove
   safety checks, publish a key, or allow access to internal files as a workaround.
6. Before restoring a Hostinger backup, have your assistant explain what it will
   replace. A backup can bring back an old key or old access rules; it also needs
   to agree with the master files in your GitHub account.

An "Access denied" or 403 response when opening a `.md` guide on doctorfab.org is
intentional. Read guides in Codex, GitHub, or your local files instead. That block
does not stop the Companion reading its own instructions internally.

## Costs to Expect

- **Hostinger hosting:** a recurring plan, with a renewal date and price shown in
  your account. Promotional and renewal prices can differ.
- **Domain name:** doctorfab.org has its own renewal, even if billed by Hostinger.
- **ChatGPT / Codex:** your chosen plan or usage charges. Check your account's
  current allowance rather than assuming unlimited work.
- **Anthropic:** separate usage charges for live AI replies. The website's limits
  reduce requests but do not guarantee a spending ceiling. Monitor your Console
  and keep the low account limit in place; hitting it may pause AI replies.
- **GitHub and email:** use the account plans you need; paid upgrades or a custom
  domain mailbox are separate choices, not something this handoff purchases.
- **Optional future services:** booking tools, payment processing, newsletters,
  or new image generation may cost extra. Ask for the cost before approving them.

No actual subscription prices or renewal dates were verified for this handoff.
Check your invoices and account settings. Your own Claude chat subscription, if
you have one, should not be assumed to pay the website's API bill.

## Current Status and Unfinished Work

Handoff prepared **November 15, 2026**. Hostinger and the domain are already yours.
The transfer into your GitHub account and replacement of the previous Anthropic
key are still pending at preparation. You should repeat the takeover tests in
your own accounts, even though the site already works.

- The current site includes the homepage, parent coaching, Sanctuary and
  Companion, resources and PDFs, Lexicon articles, and the Sanctuary of Plenty
  audio page. Normal pages and a real AI reply were checked during preparation.
- Inquiry and waitlist buttons prepare an email to `doctorfabj@gmail.com`; the
  visitor must send it. They do not automatically book appointments, collect
  payments, or create a mailing list. There is no live payment checkout in these
  website files.
- The audio collection and downloads are not password-protected. Calling a page
  "private" or leaving it out of the menu does not restrict who can open its link.
- The website does not intentionally save Companion conversations. Messages still
  go to Anthropic for replies. Do not treat the Companion or ordinary email as a
  confidential patient portal, and do not enter identifiable client records.
- **The visual audit is unfinished.** Earlier concerns included the first-page
  image, background pattern, and visible "Skip to content" link. This handoff does
  not inspect or change those visuals. Ask for a separate review before redesigning.
- A local booking-and-payment proposal may be available from the previous owner.
  It is not included in the saved website and has not been implemented or approved
  as a live checkout. Request that document separately only if useful.

You control the next priorities. The assistant's job is to make the work clear,
carry out what you approve, and tell you honestly what was and was not verified.
