# Smart TV Home Screen Prototype

Medium-fidelity interactive prototype of a redesigned smart-TV home screen, built for CS 6750 (Human-Computer Interaction) at Georgia Tech.

The design combines three ideas that came out of the project's user research:

- **Search on the home screen.** Results show which services carry a title, subscribed services first, and open the show directly.
- **Quick-switch overlay.** Hold Home while watching to switch between recent apps over the still-playing video. An explicit "Keep watching" tile is the way out.
- **Apps sorted by use.** Up to three pinned apps stay in front, the rest sort by how often they are opened. "Edit apps" is a link next to the row title rather than a tile.

Everything is in one file, `index.html`, with inline CSS and vanilla JavaScript. There are no dependencies, no network requests, no images, and no real brand assets. App tiles are coloured rectangles and show art is CSS gradients.

## Run it locally

Double-click `index.html`, or open it in any modern browser. The 1920×1080 stage scales to fit the window and letterboxes to 16:9.

## Controls

The keyboard stands in for a TV remote. The mouse also works everywhere: hovering moves focus and clicking activates, like a pointer remote.

| Key | Remote button | What it does |
|---|---|---|
| Arrow keys | D-pad | Move focus spatially |
| Enter | OK | Activate the focused element |
| Esc or Backspace | Back | Go back one level |
| H (tap) | Home | Go to the home screen |
| H (hold 400 ms) or Shift+H | Hold Home | While watching: open the quick-switch overlay |
| / | Search shortcut | Focus the search bar on Home |
| P | | In Edit apps: pin or unpin the focused app (max 3) |
| ? | | Show or hide the on-screen controls legend |
| R | | Reset the prototype to its initial state |

Backspace deletes a character while there is text in the search field. Inside the search screen, letters and space type into the field, so H, R and P are typed there instead of acting as shortcuts. Press Esc to leave search first.

## Screens

- **Home.** Continue-watching row, app grid with pinned badges, search bar, MIC and QR demos.
- **Search.** On-screen keyboard plus live suggestions. Physical typing works too.
- **Results.** Poster, title, and a "Where to watch" list sorted subscribed, then rent or buy, then unavailable. Unavailable rows cannot be focused.
- **Watching.** Full-screen animated placeholder with title, app, and a slowly advancing progress bar. The title and hint fade after four seconds of inactivity.
- **Quick-switch overlay.** Keep watching tile plus up to four recent items. Focus starts on the first recent item so one press switches. Closes on its own after ten seconds.
- **Edit apps.** Enter picks up a tile, arrows move it, Enter drops it, P pins or unpins. Done or Back returns home.

## Behaviour notes

- Launching an app, whether from a tile, a continue-watching card, search results, or the overlay, increments that app's usage count. The grid is not re-sorted while you are on Home. It re-sorts the next time Home is entered so tiles do not jump under the cursor.
- Once you reorder an unpinned app by hand in Edit apps, unpinned apps keep that manual order until you press R to reset. Pinned apps always occupy the first slots in pin order, and a tile cannot be dragged across the pinned boundary.
- Opening Search from Home starts with an empty query. Going Back from Results to Search keeps the query.
- State is not saved across reloads. Reloading the page is equivalent to pressing R.

## Deploy to GitHub Pages

1. Push this repository to GitHub.
2. Open the repository's **Settings**, then **Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select the `main` branch and the `/ (root)` folder, then save.
5. After a minute the prototype is live at `https://<username>.github.io/<repository>/`.

## Verified

Checked in headless Chromium: no console errors, no network requests, correct letterboxing at 1280×720, 1920×1080 and 2560×1440, and all five acceptance flows (launch, search, switch, keep watching, edit) pass end to end.
