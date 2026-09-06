# ca.bulk.unpin

An Unraid plugin that adds bulk cleanup controls to the **Pinned Apps** view
in Community Applications:

- **Hide Installed** — a checkbox that hides pinned apps you've already
  installed, so you can see at a glance what's still worth installing.
- **Unpin Installed Apps** — a button that unpins every already-installed
  app from your Pinned Apps list in one click (with a confirmation prompt
  first, since it's not undoable in bulk).

Works with both the stock Community Applications grid and the
[ghzgod/unraid-modern-appstore](https://github.com/ghzgod/unraid-modern-appstore)
alternate view — the plugin detects which one is active and adapts
automatically.

## Installation

**Via Community Applications** (once listed): search for "Bulk Unpin" in
the Apps tab and click Install.

**Manually**: in Unraid, go to **Plugins → Install Plugin** and paste:

```
https://raw.githubusercontent.com/joshmans/ca.bulk.unpin/main/ca.bulk.unpin.plg
```

## How it works

The plugin writes a small script (`inject.js`) into its own plugin folder
and adds a single `<script>` reference to Community Applications' own
`Apps.page` so the script loads whenever the Apps tab is open. The script
never modifies Community Applications' logic — it only reads the page's
existing DOM to find pinned, installed apps and clicks their existing
pin/unpin controls on your behalf.

It restricts its controls to the Pinned Apps view, tracked via Community
Applications' own section-navigation click event (Community Applications is
a single-page app with no URL change between sections).

## Compatibility note

This plugin has two code paths — one for stock Community Applications
markup, one for Modern App Store's markup — chosen automatically based on
Modern App Store's own view toggle. If Modern App Store changes its class
names in a future update, only the Modern-view path would be affected; the
stock Community Applications path is independent and unaffected.

## Support

Please open a [GitHub issue](https://github.com/joshmans/ca.bulk.unpin/issues)
for bugs or feature requests.

## License

MIT — see [LICENSE](LICENSE).
