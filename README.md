# Garden Planner

A small, single-page garden planner for Edinburgh (UK) gardens. It shows when
to sow, plant out, prune and harvest each plant, with a 12-month chart and a
tap-to-open detail sheet for each plant.

Live site: https://gijoem0007-ai.github.io/garden-planner/

## What it does

- **This month**: jobs due this month, grouped by task (sow, plant, prune, harvest).
- **Library**: a searchable list of every plant.
- **My garden**: plants you add yourself. Saved in the browser on that device.
  There is a copy/paste backup and restore.
- **EN / ไทย** switch at the top right. English is the default.

There are no photos. Each plant has a simple line sketch drawn in inline SVG.

## Using it

Open the live site in Safari or Chrome. To keep your garden list, use the same
browser on the same device. Saved data is stored in that browser's
localStorage, so it doesn't sync between devices. Use the backup copy to move
it. The app does not keep data inside some in-app file previews (for example,
the file preview in the Claude app).

## Project layout

This is the whole app: `index.html`. There is no build step and no
dependencies. Open it directly in a browser, or publish it with GitHub Pages.

## Adding a plant

Plant data is in the `PLANTS` array in `index.html`. Each entry looks like this:

```js
{ id:'basil', en:'Basil', th:'โหระพา', group:'herb', tasks:[
  ['sow', 4, 6], ['plant', 5, 6], ['harvest', 7, 9]
]}
```

- `id`: a unique lowercase id, also used as the key in `ICONS`.
- `en` / `th`: the English and Thai names.
- `group`: one of `herb`, `veg`, `fruit`, `flower`.
- `poly: true`: add this for polytunnel crops.
- `tasks`: a list of `[type, fromMonth, toMonth]`. Type is `sow`, `plant`,
  `prune` or `harvest`. Months are 1–12, and a range can wrap past December
  (for example `[11, 2]`).

Then add a sketch to `ICONS` with the same id. It is an inline SVG string.

## Adding or correcting Thai text

All labels live in `UI`, `MONTHS`, `MONTH_FULL`, `TASK` and `GROUP`, each with
an English and a Thai value. Edit the Thai strings there, and keep the same key
names. Plant names are in each plant's `th` field.

## Status and caveats

- Timings come from general UK guidance. They are being checked against RHS
  planting guides; corrections are listed in the commit history.
- The Thai text has not yet been checked by a Thai speaker.
- The English text has not yet been fully reviewed.
