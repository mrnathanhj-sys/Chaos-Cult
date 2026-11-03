# Eightfold Path

Gang builder, battle tracker and searchable rules for a Chaos Cult gang – Khorne, Nurgle, Tzeentch, Slaanesh or Chaos Undivided – in Necromunda, based on *The Eightfold Path* homebrew list by Berith Degustan (personal use).

## Pages
- **Gang** – recruit fighters, equipment, Mutations, Wyrd Powers and skills, with costs and legality checks.
- **Play** – fighter status and Flesh Wounds, Delusion Dice End Phase, Article Threshold tests, Ritual of Blood and the Sub-plot deck.
- **Rules** – the full rules, searchable.

## Running it
It's a single static page with no build step. Open `index.html`, or host the folder with GitHub Pages. It installs to a phone home screen and works offline after the first visit.

The roster and battle state are saved in the browser (localStorage). Use *Back up or move this gang* on the Gang page to copy a roster between devices.

When you change a file, bump `VERSION` in `sw.js` so installed copies pick up the update.
