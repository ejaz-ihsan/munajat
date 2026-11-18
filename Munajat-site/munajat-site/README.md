# Munajat

This site hosts the Munajat web app (`app/`), its landing page (`index.html`), the privacy policy, and `content.json`, which holds every dua, category, checklist and Arabic word.

## Access code

Buyers unlock the app with an access code (currently set by Claude; ask Claude to change it). It stops casual link sharing, but it is not strong security.

## Content

The app checks `content.json` each time it opens. **Any change you publish here reaches every user without an app store update.**

## How to edit (from your phone or computer)

1. On github.com, open `content.json` and tap the ✏️ pencil icon.
2. Make your change (see below).
3. **Raise `"version"` by 1** at the top (for example 1 → 2). Users only get the update when the version goes up.
4. Tap **Commit changes**. The site updates within about a minute.

A single missing comma breaks the file. If you are unsure, paste the whole file into https://jsonlint.com before committing. If the file is broken, the app quietly keeps the last good copy, so users are never left with nothing.

## Add a dua

Copy an existing dua block inside `"duas": [ ... ]`, paste it after another one (with a comma between blocks), and change the fields:

```json
{
  "id": "unique-short-id",
  "title": "Short title",
  "categories": ["anxiety", "trust"],
  "reference": "Sahih Muslim 1234",
  "arabic": "…",
  "transliteration": "…",
  "english": "…",
  "hinglish": "…",
  "story": { "en": "…", "hi": "…" }
}
```

- `id` must be unique and never change once published (saved duas and progress use it).
- `categories` uses category ids, not names.
- In `arabic`, `۝` marks a pause between phrases.

## Add a category

Add a block inside `"categories": [ ... ]`:

```json
{ "id": "ramadan", "name": "Ramadan", "icon": "moon-star", "color": "#e3b768", "keywords": ["ramadan", "fasting", "roza", "iftar"] }
```

- `icon`: any icon name from https://lucide.dev/icons (version 0.344 or older), for example `moon-star`, `heart`, `shield`.
- `keywords`: words people might type in "Describe it" to find this category.
- Then add the new id to the `categories` list of the duas that belong in it.

## Other sections

- `daily`: the ids of the duas in the "Daily Duas" intention, in order.
- `verses`: the rotating reminder on the home screen.

`privacy-policy.html` is your privacy policy page. Use its link in Google Play and App Store Connect.
