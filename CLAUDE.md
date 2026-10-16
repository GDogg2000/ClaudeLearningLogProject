# Weekly Learning Log

Single-file web app (`index.html`) for recording weekly study sessions for a class. No build step, no framework, no server: open the file in a browser.

## Structure
- `index.html` holds all HTML, CSS and JavaScript. Keep it as one file unless asked otherwise.
- Three screens, toggled with `show()`: `startScreen` (new/open), `namePrompt`, `app` (the log).
- PDF export uses jsPDF and jspdf-autotable loaded from cdnjs `<script>` tags. Everything else is dependency-free.

## Behavior to preserve
- Log columns: Date, Start Time, End Time, Time Spent (min), Pace, Location, Engagement.
- Defaults: start = 2 hours before now, end = now, time spent = end minus start (end earlier than start means the session crossed midnight), pace = normal, location = "Home", engagement = 5.
- Time spent may be lowered by hand but never raised above end minus start.
- The log is shown one week at a time (Monday to Sunday). Weekly total shows minutes only; no average engagement.
- Persistence is a user-chosen `.json` file: `{ app, version, name, entries }`. There is no localStorage. Chrome/Edge use the File System Access API (save overwrites the same file); other browsers fall back to download / file input.
- "Save as PDF" prints the displayed week with title "Weekly Learning Log for <name>" and the week's date range. Default file name is `learning-log-<monday date>_<name>.pdf`.

## Gotchas
- Element ids must be unique. A duplicate `id="start"` once broke the default start time because `getElementById` returned the wrong element.
- After editing the script, a quick syntax check works: extract the `<script>` body and run `node --check` on it.
- Not yet tested in a browser by Claude; verify UI changes by opening the file in Chrome/Edge and Firefox.

## Git
- Repository root is this folder (`ClaudeLearningLogProject`). Only commit or push when asked.
