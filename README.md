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

## Author

Liran Tal <liran@lirantal.com>