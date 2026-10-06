# Strahd Must Die — A Horror Frame for Daggerheart

![Strahd Must Die](assets/ui/banner-journals.webp)

Foundry VTT compendium module with the complete **Strahd Must Die** zine by DNGN Club Games (words & layout by Jack Panic), styled after the original zine: blood-red blackletter titles, the starry black page texture and the original art.

**Compatibility:** Foundry VTT **v13** and **v14**. The content is written for the [Daggerheart](https://www.daggerheart.com) rules, but the compendiums do not depend on any game system.

## What's inside

| Compendium | Type | Content |
| --- | --- | --- |
| Strahd Must Die — Zine | Journal Entries | 14 chapters / 46 pages: How to Use, Strahd Restructured, Quest Items, Waning Hope & Doom Track, Uneasy Allies, Downtime Moves, Sanctuary, Vampire Hunters Toolkit, Conspiracy of Ravens (all Omen Cards), Cinematic Travel, Shadows & The Mist, Conditions, Agents of Strahd and Strahd von Zarovich |
| Strahd Must Die — Omen Deck | Cards | *The Conspiracy of Ravens*: a 54-card deck (52 + 2 Jokers) with custom faces, ready to shuffle and deal to player hands |
| Strahd Must Die — Roll Tables | Roll Tables | *The Mist Table (1d20)* and *Omen Cards* (draws without replacement) |

All pages are cross-linked. Every Omen Card, roll-table result and legend entry links to the full card text.

The **Gothic journal theme** client setting (on by default) turns the journal window itself dark. It applies only to journals from this module and to copies imported into the world.

## Installation

In Foundry, go to **Add-on Modules → Install Module** and paste this manifest URL:

```
https://github.com/fernandowrpg/strahd-must-die/releases/latest/download/module.json
```

Enable the module in your world and open the **Strahd Must Die** folder in the Compendium tab.

> On Foundry v14, use build **14.361 or later**. Build 14.360 had a core bug (#14312) that converted text-type roll table results into document results.

## Development

Requirements: Node.js 20+.

```bash
npm install
npm run build     # compiles src/ into the LevelDB packs in packs/
npm run release   # build + dist/module.zip and dist/module.json
```

- `src/book.json` defines the chapters and pages of the journal compendium.
- `src/journal/**.html` holds the page content. Placeholders resolve at build time: `{{MOD}}` (module path), `{{page:chapter/page}}`, `{{entry:chapter}}`, `{{table:slug}}` and `{{deck:slug}}` (compendium UUIDs).
- `src/omen-cards.json` is the single source for the Omen Cards. It feeds the suit pages, the legend, the Cards deck and the roll table.
- `src/tables.json` holds The Mist Table.
- Document IDs are deterministic, so links stay stable between builds.
- `tools/generate-card-art.py` regenerates the card faces, the card back and the suit icons. It needs Pillow and the TTF versions of UnifrakturCook Bold and Josefin Sans from Google Fonts:

  ```bash
  python tools/generate-card-art.py --title-font UnifrakturCook-Bold.ttf --sans-font "JosefinSans[wght].ttf"
  ```

### Publishing a release

1. Bump `version` in `module.json` and `package.json`, and update `download` to `.../releases/download/vX.Y.Z/module.zip`.
2. Run `npm run release`.
3. Create a GitHub release with the tag `vX.Y.Z` and attach `dist/module.json` and `dist/module.zip`.

## Credits & License

- **Strahd Must Die** © 2026 DNGN Club Games. All rights reserved. Words & layout by Jack Panic. Stock images from Unsplash. See [LICENSE.md](LICENSE.md).
- This product includes materials from the Daggerheart System Reference Document 2.0, © Critical Role, LLC., under the terms of the Darrington Press Community Gaming (DPCGL) License.
- This work includes material from the System Reference Document 5.2.1 by Wizards of the Coast LLC, licensed under CC BY 4.0.
- Fonts: [UnifrakturCook](https://fonts.google.com/specimen/UnifrakturCook) and [Josefin Sans](https://fonts.google.com/specimen/Josefin+Sans), SIL Open Font License 1.1 (see `fonts/`).
