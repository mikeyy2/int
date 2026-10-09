# Integer Overflow Visualizer

An interactive, browser-based teaching module that shows how fixed-width integers overflow, and how the same bits are interpreted differently as signed vs. unsigned values. Built for SE/CprE 4210 Learning Sprint #2.

## What it does

Integers in C have a fixed width (8, 16, 32 bits, etc.). They can only represent a limited range of values. When a calculation pushes past the top of that range, the value silently **wraps around** to the bottom instead of growing. This tool lets you trigger that behavior by hand and watch it happen bit by bit.

## Features

- **Width toggle** (8-bit / 16-bit) to change the fixed width of the integer.
- **Value slider** to sweep across the entire representable range.
- **Add / subtract** controls with a custom step amount. Push past the maximum to see overflow, or below zero to see underflow.
- **Clickable bits** so you can flip individual bits and watch the value update.
- **Jump to MAX** button to land on the edge of the range in one click.
- **Dual readout** showing the exact same bit pattern interpreted two ways at once: unsigned, and signed (two's complement). This makes the classic result that `0xFF` is `255` unsigned but `-1` signed immediately visible.
- **Live status messages** that explain what just happened whenever a value overflows or underflows.

## Why it matters

Integer overflow is a real source of software bugs and security vulnerabilities, not just a theoretical quirk. A common dangerous pattern is a length or size check like `if (len + 1 < buffer_size)`. If `len` is already at its maximum value, `len + 1` wraps around to a tiny number, the check passes when it should not, and a buffer can be overrun. The visualizer makes the underlying wraparound behavior concrete so these bugs are easier to reason about.

## How to run it

No build step, no dependencies, no server required.

1. Download or clone this repository.
2. Open `index.html` in any modern web browser (double-click it, or drag it into a browser window).

That's it. The entire app is a single self-contained HTML file with inline CSS and JavaScript.

### Optional: host it online

Because it's a single static file, you can publish it for free with GitHub Pages:

1. Go to the repository's **Settings → Pages**.
2. Under **Build and deployment**, set the source to your default branch and the root folder.
3. Save, then wait a minute for the published URL to appear.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The complete visualizer (HTML, CSS, JavaScript). |
| `README.md` | This file. |
| `reflection.md` | Reflection on building the app and what it taught us. |

## Notes

This is a safe teaching module. It only demonstrates the arithmetic of integer overflow and contains no exploit, shellcode, or attack code.
