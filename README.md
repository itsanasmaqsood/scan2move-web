# Scan To Move — public web pages

Serves the public scan page and the legal pages Google Play requires.

These cannot live in Supabase Storage: it forcibly downgrades HTML to
`text/plain` with `nosniff`, so browsers show raw source instead of a page.
Verified by uploading identical bytes twice — declared `text/css` it serves as
CSS, declared `text/html` it serves as plain text. That is why the privacy
policy and terms showed code for weeks.

- `scan.html` — what a stranger sees after scanning a tag. It never receives
  the owner's name, number or plate: `resolve_tag` returns a vehicle label and
  a status and nothing else, so there is nothing here that could leak.
- `privacy.html`, `terms.html`, `delete-account.html` — required by Google Play.

No customer data is served from here. No analytics.
