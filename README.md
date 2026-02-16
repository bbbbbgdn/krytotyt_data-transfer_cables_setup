# krytotyt data-transfer cables setup

Minimal project for testing data transfer between the page and a [Cables](https://cables.gl/) patch.

## Data transfer

### On patch load

- **`projectsData`** — JSON array passed when the patch starts. Each item has:
  - `image` — image path (e.g. `assets/sprites/kanto/pikachu.png`)
  - `name` — display name
  - `slug` — project identifier (e.g. `025-pikachu`)

- **`zoomState`** — boolean, set dynamically (e.g. in `patchFinishedLoading`). Can be updated at any time via `CABLES.patch.setVariable("zoomState", value)`.

### On canvas

The patch renders the received `projectsData` as text and shows the current **Zoom** variable so you can confirm that data and zoom state are passed correctly.

## Callback

- **`projectClickedSlug(slug)`** — called when a project is clicked. Receives the project **slug** (Cables may pass it as a single value or as an array; the first element is used as the slug). Use this to react to project selection (e.g. navigation, detail view). If everything works here, the next step is wiring this to the main visualization.

## How to test

1. Open `index.html` in a browser (or serve the folder locally).
2. Check that projects and zoom state appear on the canvas.
3. Click a project and confirm that the callback runs with the correct slug (e.g. via the alert or by logging in the console; `window.projectClickedSlug` is exposed for manual calls).

Once data transfer and the callback behave as expected, you can connect this setup to the full visualization.
