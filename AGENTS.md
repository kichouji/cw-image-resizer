# Repository Guidelines

## Project Structure & Module Organization
The repository is a single-page tool delivered via `index.html`, which contains the HTML skeleton plus embedded CSS and JavaScript handling image ingest, cropping, and export. Keep the app self-contained in this file so GitHub Pages continues to serve it without extra tooling. Use `images/` for shared assets such as screenshots or manual-test fixtures, and keep documentation updates in `README.md` or `AGENTS.md`. If logic grows, you may split helpers into additional `.js` modules in the project root and reference them from `index.html`, but avoid introducing bundlers unless absolutely necessary.

## Build, Test, and Development Commands
There is no build step; open `index.html` directly in a browser or serve it locally to avoid file API restrictions. Example command: `python3 -m http.server 8000` from the project root, then visit `http://localhost:8000/index.html`. Keep the session active while developing so drag-and-drop, clipboard paste, dimension updates, and download actions can be verified without cross-origin issues.

## Coding Style & Naming Conventions
Use 4-space indentation. Extend the existing design tokens (`EDGE_HANDLE_SIZE`, `INITIAL_SELECTION_SCALE`, etc.) when introducing new values so related behaviour stays centralized. Keep styling inline while the UI remains compact; if the CSS block grows substantially, extract shared rules into a `styles.css` file referenced from `index.html`. JavaScript uses camelCase for functions (`resizeSelectionBoxToAspect`) and upper-snake-case for immutable constants. Keep helper utilities pure and reserve targeted comments for non-obvious canvas math or pointer-normalization logic.

## Testing Guidelines
No automated tests exist yet, so rely on manual regression passes before each change. Verify the full workflow: upload via file picker, drag-and-drop, and clipboard paste; adjust the selection box, then export both BMP and PNG outputs. Use the sample asset in `images/` or provide representative test images covering transparency and large dimensions to surface scaling issues.

## Commit & Pull Request Guidelines
Follow the existing history by writing short, imperative commit subjects (e.g., “Add drag handle snapping”). Break larger efforts into logical commits so reviewers can trace UI, logic, and asset changes separately. Pull requests should summarize the motivation, list manual verification steps (commands run, browsers tested), and attach before/after screenshots when the UI shifts. Link related issues and call out any residual risks or follow-up tasks.
