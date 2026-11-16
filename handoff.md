# Term Crossword handoff

The app generates a connected crossword from the selected word set, checks answers, locks solved entries and saves progress per set. It supplies keyboard and on-screen input, extension slots and documented helpers. No feature-menu item is delivered.

## Deviations and added copy

The built-in layouts place 11/12, 10/12 and 12/12 words in the speed, touch and form sets respectively. The unplaced words are shown in the system check as required; no word or clue was silently changed.

The interface adds `คีย์บอร์ด: Tab เปลี่ยนคำ · Esc ไปที่ปุ่มตรวจคำตอบ` so a keyboard user can leave the entry-selection cycle, plus accessible labels `ตารางปริศนา`, `แป้นตัวอักษร`, and per-cell row, column, empty and incorrect state labels. The self-check adds Thai test names, counts, storage status and extension-error labels as required by shared rules. A white/dark surface is placed behind small brass clue numbers to preserve contrast on selected cells. CSS values are exposed as custom properties.

## Checks run

- `cd tests && node --test term-crossword*.test.cjs`: 13 tests passed, including generator correctness, deterministic output, crossing validation, input, locking, signatures, a fourth set, the hint extension and a throwing handler.
- `node tools/crossword-browser-check.mjs`: Chrome checked the built-in self-check, 320 px geometry and 26 px cells, no input fields, keyboard-only completion, persistence after reload, and no console output or network request in that run. The 200-seed searches measured 23, 33 and 23 ms in that local desktop Chrome run; this is not a mid-range-phone measurement.
- `node tools/shot.mjs term-crossword`: generated the six specified screenshots. All six were inspected after correcting the 320 px grid overflow; no visible clipping or overlap remained.

- `node tools/contrast-check.mjs`: visible text passed contrast checks in sampled playing or selected states in both light and dark schemes. This does not cover every possible student modification.

## Not verified

Real touch feel and generation speed on a mid-range phone, the school lab's Windows PCs, and deployment to GitHub Pages were not tested. Sites reported a successful deployment of a separate private instructor preview. No sound is built into this app, so real sound on speakers is not applicable to the delivered game. A student-added set can place fewer words than expected if words do not share letters; the panel lists unplaced and rejected entries.
