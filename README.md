# MirrorsEdge

A fan-made **Mirror's Edge-inspired BetterDiscord theme** built around the visual language of the City of Glass: bright architectural surfaces, runner red accents, dark structural rails, and crisp wayfinding details.

> Independent fan project. Not affiliated with, endorsed by, or associated with Electronic Arts (EA), DICE, Discord, or BetterDiscord. Mirror's Edge and related names are trademarks of their respective owners.

## Features

- City of Glass-inspired white / stone interface
- Signature runner-red navigation surfaces and accents
- Dark server rail for strong visual hierarchy
- Custom channel, DM, mention, unread, reaction, composer, menu, and focus states
- Original embedded architectural / wayfinding SVG pattern
- No external images, fonts, imports, animations, or network requests
- Theme variables grouped at the top for quick customization
- Reduced-motion friendly

## Installation

### BetterDiscord

1. Download [`MirrorsEdge.theme.css`](./MirrorsEdge.theme.css).
2. Open Discord → **User Settings** → **Themes**.
3. Click **Open Themes Folder**.
4. Copy `MirrorsEdge.theme.css` into that folder.
5. Return to Discord and enable **MirrorsEdge**.

BetterDiscord theme folders are typically:

- **Windows:** `%appdata%\\BetterDiscord\\themes`
- **macOS:** `~/Library/Application Support/BetterDiscord/themes`
- **Linux:** `~/.config/BetterDiscord/themes`

## Customization

Edit these variables near the top of `MirrorsEdge.theme.css`:

| Variable | Default | Purpose |
| --- | --- | --- |
| `--me-red` | `#d00b2e` | Main runner-red accent |
| `--me-red-deep` | `#a70726` | Darker red for emphasis / hover states |
| `--me-ink` | `#20272d` | Main dark structural color |
| `--me-paper` | `#fff` | Main surface color |
| `--me-stone` | `#edf1f2` | Secondary architectural surface |
| `--me-line` | `#d7dde0` | Borders and dividers |
| `--me-muted` | `#59666f` | Muted text |
| `--me-rail` | `#20262d` | Server navigation rail |

## Updating

Replace your local `MirrorsEdge.theme.css` with the newest version from this repository.

The BetterDiscord listing, once approved, will also track updates committed to this repository.

## Compatibility

Discord changes its generated class names and UI structure regularly. If an update breaks part of the theme, please open an issue with:

- the affected screen or component;
- a screenshot;
- your Discord channel (Stable / PTB / Canary if relevant);
- the MirrorsEdge theme version.

## License

The source code in this repository is released under the [MIT License](./LICENSE).

The license applies to this project's original code only. Third-party trademarks and product names remain the property of their respective owners.
