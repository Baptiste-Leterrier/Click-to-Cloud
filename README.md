# Click to Cloud

An interactive, single-file web app that explains what happens when you click a web link, from the physical USB mouse event all the way through the kernel, browser, DNS, network stack, server path, response parsing, rendering, GPU presentation, and open source contribution opportunities.

The experience is aimed at technical people who want a systems-level view of a familiar action. Each step includes a short explanation, a global timeline, animated component highlights, and an open source project link with concrete ideas for contributing at that layer.

## Demo

Open `index.html` directly in a browser, or serve it locally:

```sh
python3 -m http.server 5173
```

Then visit:

```text
http://localhost:5173/index.html
```

## What It Shows

The journey follows a click through:

- Human input and USB HID reports
- USB host controller behavior
- Kernel interrupts, HID drivers, input queues, and scheduling
- Browser compositor hit testing and DOM event dispatch
- URL parsing, cache policy, service worker and HSTS considerations
- DNS resolution
- Socket creation, TCP, TLS, and HTTP
- NIC, Wi-Fi, routing, CDN/edge, and application server behavior
- HTTP response handling
- HTML parsing, CSS, JavaScript, layout, paint, and GPU presentation
- Open source contribution entry points at every layer

The final message is:

> When you do open source, you can work on any and all level, at your level.

## Features

- Single `index.html` file with embedded HTML, CSS, and JavaScript
- No build step
- No framework dependency
- Animated packet journey across system layers
- Clickable timeline ticks
- Play, pause, previous, next, reset, and speed controls
- Keyboard navigation with left arrow, right arrow, and space
- Per-step popups with:
  - Technical explanation
  - Event details
  - Open source project link
  - Practical contribution ideas
- Responsive layout for desktop and smaller screens
- Reduced-motion support via `prefers-reduced-motion`

## Project Structure

```text
.
├── index.html
└── README.md
```

Everything needed for the app lives in `index.html`.

## How To Customize

The step content is defined in the JavaScript arrays near the bottom of `index.html`:

- `lanes`: the high-level columns and component nodes
- `steps`: the step-by-step technical journey
- `openSourceGuides`: the open source project links and contribution ideas

To add or change a step:

1. Add or update a component in `lanes`.
2. Add or update the matching entry in `steps`.
3. Add the corresponding project link and ideas in `openSourceGuides`.

The arrays are index-aligned, so each `steps[n]` uses `openSourceGuides[n]`.

## Open Source Projects Referenced

The app links to representative open source projects and standards bodies across the stack, including:

- TinyUSB
- Linux kernel
- libinput
- Chromium
- WHATWG HTML and URL
- Unbound
- OpenSSL
- FRRouting
- Envoy Proxy
- Node.js
- curl
- V8
- Mesa
- Open Source Guides

These are meant as practical entry points, not as the only possible projects for each layer.

## Development Notes

Because this is a static app, there is no package manager setup. A normal browser is enough.

For local testing, a small static server is useful because some browsers restrict behavior on `file://` URLs:

```sh
python3 -m http.server 5173
```

No generated assets are required.

## License

No license has been selected yet. Before publishing publicly, add a license file such as `MIT`, `Apache-2.0`, or another license that matches how you want others to use and modify the project.
