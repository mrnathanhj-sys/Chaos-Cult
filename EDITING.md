# Editing guide – Eightfold Path

The whole app is one file, `index.html` (about 1,300 lines). There is no build step: edit it in any text editor, save, and refresh the browser. Everything below lives inside the single `<script>` block that starts around line 248.

Line numbers are approximate and will shift as you edit – search for the name (e.g. `const FT=`) instead.

## Where the game data lives

| What you want to change | Search for | Format |
|---|---|---|
| Fighter types – cost, stats, max, skill access, rules, equipment note | `const FT={` | One entry per type, e.g. `apostle:{n:'Apostle',cost:90,max:1,code:'A',st:[M,WS,BS,S,T,W,I,A,Ld,Cl,WP,Int],P:[primaries],S:[secondaries],rules:[...]}` |
| Order fighters appear in | `const ALLORDER=` and the `GR=` groups in `renderBuild` | List of type keys |
| Special-rule text (shown in the expandable rule boxes) | `const RULES={` | `'Rule Name':\`text\`` – the name must match exactly what's in a fighter's `rules` list |
| Equipment list and prices | `const EQL=[` | `[name, cost, category, who-can-buy, limit, rep-needed, [weapon profiles]]` |
| Who can buy (the letters in column 4) | `const WHO=` | A Apostle, D Disciple, S Sorcerer, L Mutant Lord, M Mutant, C Chosen, U Cultist, J Acolyte |
| Weapon profiles (range, S, AP, D, Am, traits) | `const WP={` | Keyed by profile name used in `EQL` |
| Equipment descriptions | `const EQD={` | |
| Mutations | `const MUTL=[` | `[d66 range, name, cost, text]` |
| Skills | `const HERESY=`, `SAVAGERY=`, `DECAY=`, `FLUX=`, `EXCESS=` | `[name, text]` |
| Wyrd Powers | `const WYRD=[` | |
| Skill access tables per god | `const KTABLE=` and `const SKT={` | P / S grid per fighter row |
| The five Dedications (Khorne, Nurgle…) | `const DED={` | Mark name, Rep needed, XP rule, stat `mods`, trait text |
| Chaos Undivided traits | `const UNDIV=` | |
| Dark Ritual favours per god | `const FAV={` | |
| Paths and their Articles of Damnation | `const PATHS={` and `const COMMON_ARTS=[` | `[name, threshold, pass effect, fail effect]` |
| Sub-plot card deck | `const SP={` | One suit per god theme |
| Lasting Injury table | `const LI=[` | `{lo, hi, n, st, t, mods}` |
| The starting example gang | `function exampleGang()` | |
| Legality checks (budget, Apostle count, Brute limits, item limits) | `function validate()` | Each problem is pushed as `['err', message]` or `['warn', message]` |

### Stat modifiers – watch the sign
In `DED` and `UNDIV`, `mods` are added straight onto the stat line. For target-number stats (WS, BS, I, Ld, Cl, WP, Int) a lower number is better, so **−1 improves the stat** and +1 worsens it. Khorne's `{WS:-1, BS:2, Cl:-2}` is "+1 WS, −2 BS, +2 Cool".

## Look and feel
- Colours: the CSS at the top of the file (lines ~18–245). Each god has its own palette under `:root[data-ded="nurgle"]` etc., with separate dark-mode blocks.
- Fonts: the Google Fonts link on line ~17 (Pirata One, Alegreya Sans, JetBrains Mono).
- App name and icons: `manifest.webmanifest` and the `icons/` folder.

## Pages (UI code)
- `renderBuild()` – Gang page
- `renderPlay()`, `playBattle()`, `trackCard()` – Play page
- The Rules page is built from the data tables above, so editing the data updates it automatically.
- Navigation is by URL hash: `#build`, `#play`, `#rules`.

## Saved data
Gangs are stored in the browser's localStorage under `ss-gang`, `ss-battle`, `ss-deck`, `ss-ui`. If you rename or remove a fighter type or item that an existing saved gang uses, that gang may look odd – clear site data or start a new gang to test.

## Publishing your version
1. Create a GitHub repo and upload this folder's contents.
2. Settings → Pages → deploy from the main branch, root folder.
3. Every time you change a file, bump `VERSION` in `sw.js` (e.g. `eightfold-path-v15`) or installed copies on phones will keep the old version.
