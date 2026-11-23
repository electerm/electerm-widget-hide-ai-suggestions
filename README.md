# Hide AI Suggestions

English | [中文](README_CN.md)

Hide the AI suggestion list that appears above the terminal.

One of the CSS patches from the electerm wiki page
[Custom CSS examples](https://github.com/electerm/electerm/wiki/Custom-CSS-examples),
packaged as a widget: install it, press **Start widget**, and the patch is on the
window — and on every launch after that.

| | |
| --- | --- |
| Shape | instance widget, one switch |
| Needs | An electerm build with client CSS asset support |
| Applies | `style.css`, applied by electerm itself |
| Unit tests | `npm test` — no dependencies, no install |

## Install

**Settings → Widgets → Import**, then paste:

```text
electerm/electerm-widget-hide-ai-suggestions
```

Or **Import folder** against a local clone.

## Use

**Settings → Widgets → Hide AI Suggestions** → **Start widget**. Leave *Apply on launch* on
and it is re-applied at every start; **Stop** in *Running instances* takes it off
again.

## What it changes

Hides `.terminal-suggestions-sticky`, the suggestion strip above the terminal.

`style.css`, in full:

```css
.terminal-suggestions-sticky {
  display: none;
}
```

## How it works

The manifest lists `style.css` in `electerm.assets.css`. Electerm loads it in each window while the widget runs and removes it on **Stop**.

## Notes

- **Standalone, not the built-in setting.** electerm also has **Settings → Common
  → Custom CSS**, applied by the app into `<style id="custom-css">` and synced
  across devices. This widget does not read or write it. Both can be active; the
  setting's sheet is last in the document, so a rule in both places is won by the
  setting. Keep a rule in one place.
- **It applies to the whole window**, settings panel included — a rule that hides
  the panel you would use to undo it hides itself. Recovery: quit electerm and
  delete `<data dir>/widgets/hide-ai-suggestions/`; the auto-run entry then has nothing to
  start.

## License

MIT
