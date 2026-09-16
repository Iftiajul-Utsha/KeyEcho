# Third-party notices and compliance

This document records bundled sound provenance and the required release-time
dependency review. Preserve it with every distributed copy.

## Holy Pandas sound pack

Copyright (c) 2020 Thomas Lai. Licensed under the MIT License.

Source project: https://github.com/tplai/kbsim  
Mechvibes copy: https://github.com/hainguyents13/mechvibes/tree/main/src/audio/holy-pandas

KeyEcho includes the five generic key recordings and dedicated Space, Enter,
and Backspace recordings distributed in that pack. The original MP3 files were
converted to mono 48 kHz signed 16-bit PCM WAV for embedded playback. The full
MIT license text is preserved in `assets/sounds/holy-pandas/LICENSE.txt` in the
source distribution. KeyEcho is not affiliated with or endorsed by Mechvibes or
Thomas Lai.

## Classic Typewriter recordings

Creator: Cassie-OrbitGames. Dedicated to the public domain under CC0 1.0.

Source: https://opengameart.org/content/typewriter-sounds  
License: https://creativecommons.org/publicdomain/zero/1.0/

KeyEcho embeds eight recordings. They are decoded, silence-trimmed, normalized,
mixed to mono, and resampled in memory when the profile loads. The source license
record is preserved in `assets/sounds/typewriter/LICENSE.txt`.

## Rust dependencies

KeyEcho itself declares the MIT license. Its compiled binary also contains
third-party Rust dependencies. Direct dependencies include anyhow, CPAL,
crossbeam-channel, directories, hound, serde, serde_json, single-instance,
Slint, rdev on Windows/macOS, and evdev on Linux. This list is not a substitute
for a complete transitive license inventory.

Before every release, generate an inventory from the final locked dependency
graph using a maintained tool such as `cargo-about` or `cargo-license`. Review
every direct and transitive license, include required license text/notices in
the package, and archive the report with release evidence. Repeat this for each
platform because target-specific dependency graphs differ.

Do not assume every asset in a generally open-source repository is reusable.
KeyEcho intentionally includes only the Mechvibes sound pack whose own directory
contains an explicit license and source attribution.
