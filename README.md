# Mac OS 27 Finder Bar

**English** | [Português](README.pt-BR.md) | [한국어](README.ko.md)

A [Windhawk](https://windhawk.net) mod that adds a macOS 27-style menu bar to the top of the screen in Windows 11: the menus of the app in front on the left, and system status, Control Center, notifications and the clock on the right, all in live glass.

![The bar: app menus on the left, status icons and the clock on the right](screenshots/bar.png)

| Control Center | Notifications |
|---|---|
| ![Control Center](screenshots/control-center.png) | ![Notifications panel](screenshots/notifications.png) |

| Logo menu | Settings window |
|---|---|
| ![Logo menu](screenshots/logo-menu.png) | ![Settings window](screenshots/settings.png) |

| Control Center in action | Weather |
|---|---|
| ![Control Center: power mode box and Edit Controls](screenshots/control-center.gif) | ![Animated weather widget](screenshots/weather.gif) |

---

## Highlights

- **Global menu**: the menus of the app in front, on the bar. Classic Win32 apps show their real menus; modern apps show their menu bar through UI Automation when they have one; browsers, File Explorer, Office, VS Code and other apps get ready-made menus that send the app's own shortcuts. A **Window** menu lists the app's open windows, and **Help** searches every menu of the app
- **Logo menu**: About This PC, System Settings, Microsoft Store (with pending update counts), Force Quit, Sleep, Hibernate, Restart, Shut Down, Lock Screen and Sign Out
- **Status icons**: battery, Wi-Fi, Bluetooth, sound (scroll to change the volume), display, keyboard layout, Now Playing (the song name scrolls when it doesn't fit; large-cover or compact panel with a progress bar drawn as a line, a colored line or a wave), Focus, microphone and camera (the icons turn orange and green while in use, click to see which apps use them and mute the microphone), weather and search (Windows Search or Siri Plus Launchpad); icons that don't fit collapse into an arrow, and each icon can be turned on or off
- **Control Center**: Wi-Fi, Bluetooth, media, dark mode, Do Not Disturb, brightness, sound and output, plus tiles you can add: night light, airplane mode, screenshot, screen recording, power mode and power plan, energy saver (one click on and off), magnifier, lock screen, calculator, Task Manager, emoji and show desktop. **Edit Controls** adds, removes, moves and resizes tiles. Power mode opens a box with the Windows 11 modes and power plans (repeated plans hidden). Tile names that don't fit scroll when the mouse is over the tile. Tiles can be pills or rounded squares
- **Notice pills**: glass pills that drop from the bar for headphones, audio output, low battery, charger, Focus, Caps Lock, USB devices and drives, finished downloads, copy and cut, screenshots, screen recordings and Windows notifications (the ones you can act on stay longer and go to the bell panel), plus floating pills for volume, brightness and Bluetooth. Style (glass, liquid glass or dark), size, position, duration and animations are configurable
- **Notifications** (turn on *Windows notifications* in **Menu Bar Settings…** → **Notice pills**): app notifications show in the pill and in the bell panel, grouped by app; **reply** to messages (like WhatsApp) right from the pill when the app supports it; **drag** a notification aside to clear it; optionally, **only the bar** shows notifications (Windows' banners move off the screen while the bar shows them)
- **Calendar**: click the clock for the calendar and your agenda from your own .ics files (read locally, never downloaded), imported right from the settings
- **Weather**: the temperature on the bar and a glass widget with the forecast (Open-Meteo, MET Norway or wttr.in, no account needed)
- **Live glass**: the bar and panels blur what's behind them in real time, with an experimental liquid glass with edge refraction (on by default)
- **Bar and menus**: transparent (default), blur glass or liquid glass bar, opaque when the app is maximized; menus in their own frosted glass or the same glass as the Control Center; light, dark or automatic theme, nine selection colors, font and sizes; hides with full-screen apps, optional auto-hide, every monitor
- **Settings window**: logo → **Menu Bar Settings…** opens the settings in a macOS-style window, with search, applied live without restarting the bar
- **Your language**: follows the Windows display language, or pick one (English, Portuguese, Spanish, French, German, Italian, Simplified Chinese and Korean)

---

## Installing

1. Install [Windhawk](https://windhawk.net).
2. Search for **Mac OS 27 Finder Bar** in Windhawk's mod catalog and click **Install**.

To try a version from this repository before it reaches the catalog: in Windhawk, click **Create a new mod**, replace the code with the contents of [`mac-os-27-finder-bar.wh.cpp`](mac-os-27-finder-bar.wh.cpp), and click **Compile Mod** and then **Exit Editing Mode**.

## Settings

The settings live in the mod's own window: logo menu → **Menu Bar Settings…**, applied live. Windhawk's settings page for the mod has the few the window doesn't: font, glass tints, theme, the name shown for the desktop, ready-made menus, Control Center tile look, opening animation, tray click, the app update count and .ics file paths, plus **Reset the bar's settings**, which puts the window's options back to their defaults if the bar ever doesn't show up.

## What changes Windows settings

Some Control Center tiles and menu items change real Windows settings, the same ones Windows' own quick settings change, and they stay changed after the mod is turned off: dark mode (app and system theme, both set to the same value), night light, power mode and power plan (a power mode also switches the plan to Balanced), energy saver, Do Not Disturb, brightness, default audio device, volume and mute, microphone mute, Wi-Fi and Bluetooth radios, Wi-Fi network and display mode. Nothing changes unless you click the matching tile or item.

## Network use

The mod only goes online for features you set up yourself (the calendar reads local .ics files only):

- **Weather**, once you pick a place: place search through OpenStreetMap Nominatim or Open-Meteo, and the forecast from the service you choose (Open-Meteo, MET Norway or wttr.in) with the place's coordinates rounded to about 1 km. Turning the weather icon off stops all requests.
- **App update count** (off by default, in Windhawk's settings): runs `winget upgrade`, which checks winget's sources online. The mod never accepts winget's source agreements for you. The Windows Update count is offline.

The copy pill only says "Copied" or "Cut": it never shows what was copied, and it skips anything an app marks as private (password managers do), the same way Windows' clipboard history does.

## How it runs

The bar runs in its own Windhawk process (shown as Windhawk in Task Manager), so if it ever fails, the taskbar and desktop keep working. Explorer keeps only a small hook that copies the tray icons' registrations to the bar. If that process is ended by hand, turn the mod off and on again in Windhawk to bring the bar back.

## Known limitations

- Apps without a classic menu bar use ready-made menus based on keyboard shortcuts.
- Bluetooth lists classic (non-BLE) devices and opens Settings to connect and disconnect.
- Power mode and energy saver use undocumented Windows functions; if Windows refuses, the tile opens the matching Settings page.
- Screen recording uses Win+Shift+R and needs an up-to-date Snipping Tool.
- Replying from the pill works with apps that register a notification activator with Windows; otherwise the pill opens the app and copies your text.
- With live glass (and the bar's liquid background), the bar and panels don't show up in screenshots.
- If Windhawk itself runs as administrator (portable mode started elevated), the bar doesn't show the tray icons: letting the shell's tray data reach an elevated bar would also let any app send it fake icons.

## License

[GPL-3.0](LICENSE)
