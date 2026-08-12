# CP Subject Combination Checker

A single-page tool for checking whether a Career-related Programme (CP) student's
subject choices across Blocks D, E and F can be accommodated in the current offer
structure.

Blocks A, B and C hold fixed CP provision and are not selectable. Only Blocks D, E
and F contain student choices.

## Usage

Open `index.html` in any modern browser. No build step, no dependencies, no server
required.

Pick a subject in each of Blocks D, E and F. The checker reports:

- **Valid combination** — all three choices can be accommodated.
- **Valid partial combination** — fewer than three choices made so far.
- **Invalid combination** — the same subject was chosen in more than one block.

Two example buttons pre-fill common combinations, and "Clear choices" resets the form.

## How duplicate detection works

Subjects appear in multiple blocks as separate teaching groups (`Biology MX.1`,
`Biology MX.2`, `Biology MX.3`). Before comparing, each label is normalised by
stripping the trailing student count and collapsing the group suffix, so
`Biology MX.2 (16)` and `Biology MX.3 (11)` both reduce to `Biology MX` and are
correctly flagged as the same subject.

## Structure

Everything lives in `index.html` — markup, styles and logic. The block data is
defined at the top of the `<script>` block in three objects:

- `fixedBlocks` — Blocks A/B/C: fixed provision plus DP-only options unavailable to CP.
- `choiceBlocks` — Blocks D/E/F: the selectable options.
- `additionalFixedProvision` — extra fixed provision shown in the second table row.

To update the offer for a new academic year, edit those objects.

## Deploying

The repository is a static site. Enabling GitHub Pages on the default branch
serves `index.html` at the repository root with no further configuration.
