# Copilot Instructions for Live Server Web Extension

## Project Overview

- This is a browser extension that works with the VS Code "Live Server" extension to enable live reloading for server-side files (PHP, .NET, NodeJS) in addition to static HTML/HTM files.
- The extension does **not** host a server; it only provides reload functionality when files are saved.
- Key files:
  - `background.js`: Handles background logic for the extension.
  - `reload.js`: Manages tab reloading.
  - `manifest.json`: Chrome/Firefox extension manifest.
  - `popup/popup.js` & `popup/popup.html`: Popup UI and logic.
  - `docs/`: Contains setup, FAQ, and about documentation.

## Architecture & Data Flow

- The extension listens for events from the VS Code Live Server and triggers reloads in browser tabs.
- Communication between background scripts and popup UI is handled via Chrome/Firefox extension messaging APIs.
- Screenshots and sample tests are excluded from builds (`img/screenshots/**`, `sampleTest/**`).

## Developer Workflows

- **Build:** Use the following command (see workspace tasks):
  - `web-ext build -o -i="img/screenshots/**" "sampleTest/**" && echo Done!`
- **Debug:** Load the unpacked extension in Chrome/Firefox for local testing. Use the popup UI to trigger reloads and check background script logs.
- **Documentation:** Key docs are in the `docs/` folder. Start with `Setup.md` for environment setup.

## Project-Specific Conventions

- All UI code for the popup is in `popup/` (HTML, JS, CSS).
- Background logic is isolated in `background.js`.
- Reload logic is in `reload.js`.
- Manifest is the single source of truth for extension configuration.
- No user data is collected (see README and manifest).

## Integration Points

- Integrates with VS Code Live Server via browser extension messaging.
- Compatible with Chrome and Firefox (see manifest and README badges).
- No external backend or server dependencies.

## Examples

- To add a new popup feature, update both `popup/popup.html` and `popup/popup.js`.
- To change reload behavior, edit `reload.js` and ensure background messaging is updated in `background.js`.

## References

- [README.md](../README.md) for project description and links
- [docs/Setup.md](../docs/Setup.md) for setup instructions
- [manifest.json](../manifest.json) for extension configuration

---

**For questions or unclear patterns, review the documentation in `docs/` or ask for clarification.**
