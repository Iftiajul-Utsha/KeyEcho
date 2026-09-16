# KeyEcho

**Make every keystroke sound the way you want.** KeyEcho is a small desktop utility that plays keyboard and typewriter sound effects while you type in any application. Pick a sound, set the volume, and leave it running in the system tray.

> **Release status:** The available portable build is for **Windows x64**. The Rust source includes macOS and Linux support paths, but native releases for those systems still need packaging and device testing.

## What it does

- Plays sounds for system-wide key presses, even when the control window is closed.
- Includes Mechanical, Classic Typewriter, Holy Pandas, and Soft sound profiles.
- Supports your own folders of WAV samples.
- Keeps playback responsive during fast typing with preloaded sounds and a limited pool of overlapping voices.
- Lets you mute instantly with **Ctrl+Alt+M**, the **Disable sounds** button, or the tray menu.
- Offers profile selection, a preview button, and master volume control in a simple window.
- Saves your preferences locally and prevents duplicate app instances.

## Try KeyEcho on Windows

1. Get the Windows x64 package from a release you trust. In the full project package, the portable executable is `PUBLISHED VERSION/The APP/KeyEcho.exe`.
2. Extract the package to a folder you can keep. Keep the accompanying license, privacy, and third-party notice files with it when redistributing the app.
3. Run `KeyEcho.exe`. The portable build does not require a separate Python or Rust installation.
4. Choose a profile and adjust the volume in the control window. The first run creates local settings automatically.

The current development build is **unsigned**, so Windows may show a reputation warning. Only run a copy obtained from a source you trust. A code-signed public release is a future distribution step.

## Everyday controls

| Action | How |
| --- | --- |
| Mute or unmute | Click **Disable sounds** / **Enable sounds**, use the tray menu, or press **Ctrl+Alt+M** anywhere. |
| Change sound | Choose a profile in the control window. |
| Set volume | Use the master volume slider or the tray controls. |
| Keep it in the background | Close the window; KeyEcho remains in the tray. |
| Stop the app completely | Click **Quit KeyEcho** in the window or tray. |

If you want the typing sounds to stop immediately, use **Disable sounds**. Closing the window alone keeps the app running.

## Add your own sounds

Run KeyEcho once, then use the custom-profile location displayed in the app. Make a folder for each profile and add WAV files, for example:

```text
My Typewriter/
  key-1.wav
  key-2.wav
  space.wav
  enter.wav
  backspace.wav
```

Restart KeyEcho to discover new profiles. It accepts PCM or IEEE-float WAV files. Multiple `key*.wav` samples provide variation; missing special-key samples fall back to the built-in Mechanical sounds. Short recordings with little silence at the start feel most responsive.

## Build from source

KeyEcho is written in **Rust**. Its interface and tray use **Slint**; **CPAL** handles audio output; global keyboard input uses OS-specific backends. The current Windows release can be built with a stable Rust toolchain and the Windows C++ build tools:

```powershell
cargo build --release
cargo run --release
cargo test
```

The built executable is `target/release/keyecho.exe`. Sound assets used by the built-in profiles are embedded in the application, so the executable does not need a separate sound folder at runtime. Building or running on macOS and Linux may require additional native development libraries and input permissions. See the project's development and deployment documents before preparing packages for those systems.

## How it works

KeyEcho listens for key-down events through a global keyboard hook, maps each event to a sample from the selected profile, and sends a small playback command to its audio engine. Samples are loaded ahead of playback so the key event does not have to read or decode a file. A bounded command queue and voice limit keep work predictable during rapid typing.

KeyEcho uses key identity only to choose sounds and recognize the mute shortcut. It does not construct typed text, store a keystroke history, or transmit keyboard events. The current release has no account, telemetry, advertising, or update service.

## Project status and documentation

**Version 0.3.0** is the current documented baseline. The Windows x64 portable executable has been built and checked; macOS and Linux release packages remain future work. Audio latency also depends on your operating system and output device, particularly with Bluetooth audio.

The full project package includes a `PUBLISHED VERSION` folder with an end-user guide, engineering context, codebase map, development steps, release checklist, privacy policy, third-party notices, and future roadmap. Start with `PUBLISHED VERSION/00-READ-ME-FIRST.md` for the documentation index and `PUBLISHED VERSION/01-AGENT-HANDOFF.md` if you plan to enhance the app.

## Credits and license

KeyEcho includes original and licensed third-party sound assets, including a recorded typewriter profile and a Holy Pandas profile sourced from Mechvibes. Attribution and license details are in `PUBLISHED VERSION/THIRD-PARTY-NOTICES.md` and the notice file distributed with the app. Consult the project's license file before redistributing or modifying the software.
