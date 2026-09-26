# Developing the theme

## Test in Discord

Copy `MirrorsEdge.theme.css` to the BetterDiscord themes folder, enable it, and keep Discord open while editing the source. BetterDiscord reloads the CSS after the installed copy changes. Compare the same screen before and after each change. Start with the views in [tests/COVERAGE.md](./tests/COVERAGE.md).

The theme deliberately uses no remote images, fonts or imports. The supplied visual reference is a direction for color, hierarchy and spacing, not a pixel specification for Discord's changing layout. Keep text readable and preserve user supplied profile colors and banners in profile popouts.

## Inspect a broken component

1. Open BetterDiscord's Developer Settings and enable DevTools if it is disabled. In Discord, open DevTools with `Ctrl+Shift+I` and select the element with the DevTools picker (`Cmd+Shift+C` on macOS).
2. Record its class, parent classes, `role` and `aria-*` state. Check the computed color, background, border and opacity. For a transient menu or tooltip, pause the page with `F8` while DevTools is open.
3. Prefer a semantic state (`aria-checked`, `aria-selected`, `role`) and a narrow parent selector. Use a generated class fragment only when the DOM offers no stable alternative. Discord may change those fragments on update.
4. Change one rule, save the installed CSS, and inspect the same view again. Check hover, focus, selected, disabled and unread states where relevant.

For a quick structural report, select an element in DevTools and run this in its console. It reports styling and attributes only; it does not collect message text or account data.

```js
copy(JSON.stringify((() => {
  const rows = [];
  for (let node = $0, depth = 0; node && depth < 6; node = node.parentElement, depth++) {
    const style = getComputedStyle(node);
    rows.push({
      depth,
      tag: node.tagName,
      classes: [...node.classList],
      role: node.getAttribute("role"),
      checked: node.getAttribute("aria-checked"),
      selected: node.getAttribute("aria-selected"),
      background: style.backgroundColor,
      color: style.color,
      opacity: style.opacity
    });
  }
  return rows;
})(), null, 2));
```

Never paste code into DevTools that you have not reviewed. Do not include tokens, private messages, cookies or local storage in issue reports or screenshots.

## Before a release

- Check the theme metadata version, README and changelog together.
- Recheck the coverage matrix against the installed theme on the current Discord build. Mark a view verified only after inspecting it live.
- Run `git diff --check` and review selectors with `!important`, inline-style dependencies and broad `[class*="..."]` matches.
- Capture comparison screenshots locally if they help diagnose a regression. Remove personal data before sharing them publicly.
