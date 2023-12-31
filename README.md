[![npm](https://img.shields.io/npm/v/astro-keyboard-controls.svg)](https://www.npmjs.com/package/astro-keyboard-controls)
[![npm](https://img.shields.io/npm/l/astro-keyboard-controls.svg)](https://www.npmjs.com/package/astro-keyboard-controls)
[![Build Status](https://github.com/lirantal/astro-keyboard-controls/workflows/release/badge.svg)](https://github.com/lirantal/astro-keyboard-controls/workflows/release)
[![Known Vulnerabilities](https://snyk.io/test/github/lirantal/astro-keyboard-controls/badge.svg)](https://snyk.io/test/github/lirantal/astro-keyboard-controls)

# Astro Keyboard Controls

An Astro component that allows you to easily bind to specific keyboard keys and focus on a specific element based on a passed selector string.

## Installation

```bash
npm install astro-keyboard-controls
```

## Example

```astro
---
import KeyboardControls from 'astro-keyboard-controls';

---

<Layout {meta}>
	<KeyboardControls selector="div#search input" key="/" />
    <div id="search">
        <input type="text" />
    </div>
</Layout>
```

### Available component props

| Name              | Type                              | Example                       | Description                                        |
| ----------------- | --------------------------------- | ----------------------------- | -------------------------------------------------- |
| `selector`         | String                           | `div#search input`        | A string specifying the selector that is passed to `document.querySelector()` |
| `site`            | String                            | `/` | The keyboard key to bind with an event listener for `keydown` |

## Author

Liran Tal <liran@lirantal.com>
