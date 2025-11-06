# Repository Guidelines

## Project Structure & Module Organization
The repository is a single-page tool delivered via `index.html`, which contains the HTML skeleton plus embedded CSS and JavaScript that handle image selection, cropping, and export. Place shared assets such as the sample screenshot or fixtures in `images/`, and keep documentation updates in `README.md`. When adding new scripts or splitting logic, prefer creating dedicated `.js` modules in the root and referencing them from `index.html` to retain the lightweight structure suited for GitHub Pages.

## Build, Test, and Development Commands
There is no build step; open `index.html` directly in a browser or serve it locally to avoid file API restrictions. Example command: `python3 -m http.server 8000` from the project root, then visit `http://localhost:8000/index.html`. Keep the session in place while developing so drag-and-drop, clipboard paste, and download actions can be verified without cross-origin issues.

## Coding Style & Naming Conventions
Use 4-space indentation and keep styling inline only for UI elements already in `index.html`; extract larger style changes into a new `styles.css` if the block grows. JavaScript follows camelCase for functions (`initializeSelectionBox`) and constants for DOM element references (`const fileInput`). Keep helper utilities pure and document tricky logic with short inline comments—especially around canvas coordinate math or selection box behaviour.

## Testing Guidelines
No automated tests exist yet, so rely on manual regression passes before each change. Verify the full workflow: upload via file picker, drag-and-drop, and clipboard paste; adjust the selection box, then export both BMP and PNG outputs. Use the sample asset in `images/` or provide representative test images covering transparency and large dimensions to surface scaling issues.

## Commit & Pull Request Guidelines
Follow the existing history by writing short, imperative commit subjects (e.g., “Add drag handle snapping”). Break larger efforts into logical commits so reviewers can trace UI, logic, and asset changes separately. Pull requests should summarize the motivation, list manual verification steps (commands run, browsers tested), and attach before/after screenshots when the UI shifts. Link related issues and call out any residual risks or follow-up tasks.
