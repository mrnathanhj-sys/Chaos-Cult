# Summon sounds

Audio files here play when someone clicks the **Eightfold Path** title 8 times.

1. Upload `.mp3` (or `.ogg` / `.wav`) files to this folder.
2. In `index.html`, search for `const SCRUNT_SOUNDS=[]` and list them, e.g.
   `const SCRUNT_SOUNDS=['sounds/grovel.mp3','sounds/spoon.mp3'];`
3. Bump `VERSION` in `sw.js`.

One clip is picked at random on each summon. Keep clips short (a few seconds, under ~200 KB) so the app stays quick on phones.

## Credits

The five included clips (`blood-drums`, `skull-toll`, `chainaxe`, `bone-breaker`, `berserker-roar`) were made for this app by layering original synthesis (drums, growls, engine rev) with sounds from **Impact Sounds by Kenney** (www.kenney.nl), released under **CC0 1.0** – free to use, no attribution required. The clips themselves are likewise free to use.
