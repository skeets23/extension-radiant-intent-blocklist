# Radiant Intent distraction filters

This repository is the source of the always-active distraction filters used by Radiant Intent. Edit [rules.json](rules.json) to maintain them without changing or reloading the extension.

These are cosmetic filters: they hide feeds, suggestions, comments, and navigation clutter. They do not block entire websites. TikTok is treated like the other supported websites. Personal allow/block lists and work-clock settings belong in the extension, never in this public repository.

## Updating the list

1. Edit `rules.json` on the `main` branch.
2. Add or adjust a site's rules, retaining valid JSON.
3. Increase the integer `revision` to make the change easy to identify.
4. Commit. Radiant Intent checks on startup when its last check is at least six hours old, and then every six hours. Updates apply to open pages.

The extension retains a cached copy if an update fails and includes a bundled JSON snapshot for first use/offline fallback. Structurally invalid updates are rejected. Each page also validates CSS before applying a list; it keeps its prior usable list, or the bundled fallback on a new page, if CSS is invalid. Browser scheduling and GitHub caching can delay updates.

## Format

```json
{
  "schemaVersion": 1,
  "revision": 1,
  "sites": [
    {
      "id": "example",
      "name": "Example",
      "domains": ["example.com"],
      "rules": [
        {
          "category": "feeds",
          "selector": ".home-feed",
          "path": "^/$"
        }
      ]
    }
  ]
}
```

- `id`: unique lowercase identifier.
- `name`: display name in the extension.
- `domains`: bare lowercase domains; includes their subdomains.
- `category`: `feeds`, `recommendations`, `comments`, or `clutter`. These are descriptive groups, not switches.
- `selector`: CSS selector, including selector lists and standard `:has()`. Also supports a trailing quoted literal `:has-text("text")`, directly or inside `:has(descendant-selector:has-text("text"))`.
- `path`: optional JavaScript regular expression matched against URL pathname only. Omit to apply on all paths. Parentheses work here because this is a separate JSON field.
- Text matching uses case-sensitive substring matching against textContent. No HTML or script code is executed from this file.

The list must contain at least one rule. Maximums: 200 sites, 100 domains per site, 500 rules per site, 5,000 total rules, 4,000 characters per selector, and 500 characters per path expression. Keep the JSON response under 512,000 characters.

## Scope

Initial rules cover ChatGPT, X/Twitter, YouTube, Reddit, Amazon, Facebook, Instagram, LinkedIn, Threads, TikTok, Pinterest, and Twitch. Selectors are maintained presets, not automatic feed detection; website redesigns and localized text may require adjustments.

Distraction filtering is always active in Off, Half focus, and Full focus. There is no local switch or editable remote-source URL. Only JSON filter data is downloaded; all executable logic is bundled with the Manifest V3 extension.
