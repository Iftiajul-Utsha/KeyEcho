# KeyEcho 0.3.0 — Windows user manual

This folder is the portable Windows x64 edition of KeyEcho. It does not require
an installer, Rust, Python, or separate sound files. The built-in Mechanical,
Classic Typewriter, Holy Pandas, and Soft sounds are embedded in `KeyEcho.exe`.

## Package contents

- `KeyEcho.exe` — the application.
- `instruction.md` — installation, controls, troubleshooting, and uninstall guide.
- `LICENSE.txt` — KeyEcho's MIT license.
- `THIRD-PARTY-NOTICES.md` — licenses and attribution for bundled sounds and
  third-party components.
- `PRIVACY-NOTICE.md` — summary of the application's local data behavior.
- `checksums.sha256` — SHA-256 checksum for verifying this executable.

Keep these files together when sharing the application. Only `KeyEcho.exe` is
technically needed to run it, but the other files provide important instructions,
licensing, privacy, and integrity information.

## System requirements

- 64-bit Windows 10 or Windows 11.
- A working audio output device.
- A standard user account is sufficient; administrator rights are not normally
  required.

This particular executable is an unsigned local validation build. Windows may
show an unknown-publisher or reputation warning. For public distribution, the
publisher should code-sign and timestamp it. Do not run a copy obtained from an
untrusted source.

## Open the app

1. Copy the entire `The APP` folder to the laptop. A location such as
   `Documents\KeyEcho` or `%LOCALAPPDATA%\Programs\KeyEcho` is suitable.
2. Do not run the application directly from inside a ZIP file. Extract the folder
   first if it was downloaded as a ZIP.
3. Double-click `KeyEcho.exe`.
4. The KeyEcho control window opens. Only one copy can run at a time.
5. Select a profile and click **Preview** to confirm the audio output.

No separate installation or sound-pack download is needed. If you move the
folder later, use `KeyEcho.exe` from its new location.

## Main controls

- **Profile:** chooses Mechanical, Classic Typewriter (Recorded), Holy Pandas
  (Mechvibes), Soft, or an installed custom profile.
- **Preview:** plays a sample without typing.
- **Master volume:** changes the sound-effect volume immediately.
- **Disable sounds:** mutes all typing sounds immediately. The status changes to
  MUTED and the button changes to **Enable sounds**.
- **Enable sounds:** resumes typing sounds and changes the status to ACTIVE.
- **Quit KeyEcho:** stops the keyboard hook, closes the audio engine, and exits
  the application completely.

## Keyboard shortcut and system tray

- Press `Ctrl+Alt+M` anywhere to disable or enable sounds.
- Closing the control window does **not** quit KeyEcho. It hides the window and
  leaves the app operating in the Windows system tray.
- Use the tray icon to show the window, toggle sounds, change volume, or quit.
- If the tray icon is hidden, open Windows' hidden-icons menu near the clock.
- Double-clicking `KeyEcho.exe` while it is already running will not start a
  second audio engine.

## Completely stop the sounds

Use any one of these methods:

1. Click **Disable sounds** in the main window to keep KeyEcho open but muted.
2. Press `Ctrl+Alt+M` to toggle mute globally.
3. Use the tray menu's sound toggle.
4. Click **Quit KeyEcho** in the window or tray to stop the application fully.

If sounds continue unexpectedly, open Windows Task Manager, search for KeyEcho,
and confirm that only one `KeyEcho.exe` process exists. End that task only if the
normal Quit button is unavailable.

## Sound profiles

- **Mechanical:** short synthesized mechanical clicks.
- **Classic Typewriter (Recorded):** authentic recorded typewriter sounds.
- **Holy Pandas (Mechvibes):** recorded mechanical-switch sounds with rotating
  main-key variations and dedicated Space, Enter, and Backspace samples.
- **Soft:** quieter, gentler synthesized clicks.

## Add a custom WAV profile

The exact custom-profile directory is displayed near the bottom of the KeyEcho
window. Run the app once, open that directory, and create a profile subfolder:

```text
My Sound/
  key-1.wav
  key-2.wav
  space.wav
  enter.wav
  backspace.wav
```

Use uncompressed PCM or IEEE-float WAV files. Multiple `key*.wav` files rotate
while typing. Stereo audio is mixed to mono automatically. Restart KeyEcho after
adding or changing a profile. Short recordings with leading silence removed give
the best response. MP3 files are not supported for user-created profiles.

## Troubleshooting

### No sound

1. Confirm the KeyEcho badge says ACTIVE and Master volume is above zero.
2. Click Preview. If Preview is silent, check the selected Windows output device
   and the per-application Volume Mixer.
3. Connect the audio device before starting KeyEcho, then restart the app.
4. Confirm Windows or security software has not stopped the process.

### Typing sound is delayed

Bluetooth audio can introduce significant latency. Test with wired headphones or
speakers. Custom sounds should be short and have no silence at their beginning.

### The window disappeared

Closing the window hides it to the system tray. Click the KeyEcho tray icon and
select the command to show the window.

### The app will not start

Confirm the folder was fully extracted and that the PC runs 64-bit Windows 10 or
11. Verify the checksum below. If Windows quarantined the executable, do not
disable protection blindly—obtain a signed copy from the official publisher.

## Verify the executable

Open PowerShell in this folder and run:

```powershell
Get-FileHash .\KeyEcho.exe -Algorithm SHA256
```

For this package, the result must be:

```text
3C0E605C1CA3DA084F623B10DB9B6C953B594DD54703302A90A6E1C1F2693253
```

If it differs, the file is not the same build described by this manual. Do not
run it until its source is confirmed.

## Privacy

KeyEcho receives global key identity and press/release events so it can select a
sound and recognize `Ctrl+Alt+M`. It does not construct typed words, save a
keyboard history, transmit key events, use analytics, or require an account.
Profile choice, volume, and enabled state are stored locally.

## Uninstall

1. Click **Quit KeyEcho**.
2. Delete the `The APP` folder or the copy placed on the laptop.
3. If desired, delete KeyEcho's settings and custom-profile data from the
   application-data path displayed in the app.
4. Delete any shortcut you manually created.

KeyEcho does not currently install a Windows service, driver, browser extension,
or automatic updater.
