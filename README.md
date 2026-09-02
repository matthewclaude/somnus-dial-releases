# somnus-dial-releases

Firmware releases and the browser flasher for **Somnus Dial** — a bedside
dial that turns a Waveshare ESP32-S3 round touch-LCD knob into a standalone
temperature control for a Somnus Pad. Not affiliated with, endorsed by, or
supported by Somnus or Waveshare.

**This repo holds binaries, a manifest, and the flasher page only — it is not
the firmware's source.** The source lives in a private repository. That's a
deliberate choice about how this project is developed, not a change to the
license below. If you want the source, ask the maintainer.

## Install

Open **[the flasher page](https://matthewclaude.github.io/somnus-dial-releases/)**
in Chrome or Edge on a desktop computer, plug the dial in over USB-C, and
click Install. No software to install locally — the page flashes the board
directly from your browser over Web Serial.

Already have a dial running this firmware? You don't need this page again.
The dial checks for updates periodically on its own and tells you when one is
available, and you can check any time from Menu → Update on the dial itself.

Note that flashing from this page **erases the dial's settings** — Wi-Fi
credentials, timezone and pad address — because the image it writes covers
the whole flash. That's fine for a first install. To update a dial you're
already using, use the over-the-air update instead; it preserves everything.

## What's in a release

Each [release](https://github.com/matthewclaude/somnus-dial-releases/releases)
carries two files:

- `somnus-dial.bin` — the app-only image. This is what a dial already running
  this firmware downloads and installs over the air; it must never be flashed
  directly at offset `0x0`.
- `somnus-dial-merged.bin` — the same firmware bundled with the bootloader and
  partition table into one image flashable at offset `0x0` on a blank or
  already-flashed chip. This is what the browser flasher uses, and what you'd
  use with `esptool` manually.

A release marked **pre-release** on GitHub is a beta build — offered only to
dials with "Beta builds" turned on under Menu → Update, or via the flasher
page's beta checkbox.

## License and attribution

This firmware is a fork of
[chris023/orion-waveshare-rotary-dial](https://github.com/chris023/orion-waveshare-rotary-dial),
licensed under the **PolyForm Noncommercial License 1.0.0** — free for
personal, noncommercial use. See [`LICENSE`](LICENSE) for the full terms and
required notice, and [`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md) for
the hardware bring-up code, fonts, data, and libraries this project builds on,
each under its own terms.
