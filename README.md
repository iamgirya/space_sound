# Sound Space

### Deployed: https://space-sound.onrender.com/

A spatial audio playground that runs entirely in your browser — no installation, no server. Built to be useful for tabletop role-playing games.

Inspired by [TAT by Paradiso](https://www.paradiso.zone/ooo-tat/).

> Vibe-coded with Claude.

---

## What is it?

Sound Space is a single-file web app for creating interactive spatial audio scenes. You place sound zones on a 2D canvas, position a listener, and the sounds play when the listener enters a zone — with volume shaped by proximity to the zone's center. Add images and freehand drawings to build a visual backdrop. Everything is auto-saved in the browser and can be exported as a single portable file.

---

## Features at a Glance

- **Spatial audio zones** — circle and polygon shapes, sounds fade in/out on enter/exit
- **Proximity volume** — sound gets louder toward the center of a zone
- **Global & always-on sounds** — play a sound regardless of listener position
- **Sound timers** — schedule sounds to start after N seconds, with optional repeat
- **Images on canvas** — movable, resizable, pinnable
- **Freehand drawing** — marker tool with color and width options
- **Multiple pages** — independent scenes in one session
- **Pan & pinch-to-zoom** — navigate the canvas on desktop and mobile
- **Auto-save** — state persists in IndexedDB across reloads
- **Export / Import** — full save as a single self-contained JSON file

---

## Where it runs

Sound Space is a single `.html` file. Open it in any modern browser:

- **Desktop** — Chrome, Firefox, Safari, Edge
- **Mobile** — iOS Safari, Android Chrome
- **No server needed** — just open the file directly (`file://`) or serve it statically

Touch gestures are fully supported: drag to pan, pinch to zoom, double-tap to teleport the listener or pin an image.

---

## Detailed Feature Overview

### Listener

The listener (`👂`) is the "ear" on the canvas. Drag it around the map to hear what sounds are active at that position. Double-tap (or double-click) on empty space to teleport it instantly.

### Sound Zones

- **Circle zones** (`⊕ Circle`) — drag to draw. The radius defines the sound boundary.
- **Polygon zones** (`⬡ Polygon`) — click to place vertices, double-click or click the first point to close. Press `Esc` to cancel.
- Each zone has a name, color, assigned sound, and volume control.
- **Proximity volume** — when enabled, the sound is loudest at the zone's center and fades to silence at the edge.
- **Keep Playing** — when the listener exits, the sound fades to silent but keeps playing from the same position. It resumes full volume on re-entry.
- **Play Global** — the zone's sound plays everywhere on the page at a fixed volume, regardless of listener position.
- **Manual control** — each zone in the list has its own play/stop button and scrubber for hands-on playback.
- Zones animate with a pulse when active.

### Sounds

- Load any number of audio files via the upload button.
- Preview sounds before assigning them.
- **Global sounds** — toggle a sound to play constantly with a volume slider.
- **Timers** — set a countdown after which a sound goes global. Supports repeat (🔁): once the sound ends, the timer restarts with the same delay and volume.

### Images

- Load images and place them on the canvas.
- Move freely and resize via four corner handles.
- **Pin** — double-tap (or double-click) an image to lock it in place. Pinned images show an orange border and a 🔒 icon in the panel. Double-tap again to unpin.

### Drawing

- **Marker tool** (`✏`) — freehand drawing with mouse or touch.
- Choose from 8 preset colors or enter a custom hex code.
- Three stroke widths available.
- Each stroke is an independent object: selectable and draggable in move mode.
- Delete a selected stroke with `Delete` or `Backspace`.

### Canvas Navigation

- **Pan** — drag on empty space (mouse or single finger).
- **Zoom** — scroll wheel on desktop; pinch with two fingers on mobile.
- **Reset view** — the `⌂ Center` button resets pan and zoom to default.

### Pages

- Create multiple independent scenes (tabs above the canvas).
- Each page has its own zones, images, drawings, and listener position.
- The sounds library is shared across all pages.
- Rename a page by double-clicking its tab. Delete with the `×` button (minimum one page required).

### Save & Export

- **Auto-save** — every change is debounced and written to IndexedDB automatically. Everything survives a page reload.
- **Export (`⬇`)** — downloads a `soundspace-save.json` file that includes all audio and image data as base64. Fully self-contained.
- **Import (`⬆`)** — loads a save file and restores the full session.

---

## Technical Notes

- Single `.html` file — no build step, no npm, no framework
- All storage via IndexedDB (audio blobs, image blobs, full app state)
- Canvas rendering with pan/zoom transform (`ctx.translate` + `ctx.scale`)
- Pointer Events API for unified mouse and touch handling (`setPointerCapture` for reliable drag)
- Pinch-to-zoom via two-pointer tracking with midpoint-centered scale math

---

## Reporting bugs

Found a bug? Open a [GitHub Issue](../../issues) — describe what happened, your device and browser, and steps to reproduce.

---

*Vibe-coded with [Claude](https://claude.ai). Inspired by [TAT · Paradiso](https://www.paradiso.zone/ooo-tat/).*
