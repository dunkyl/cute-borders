# cute-borders

Makes focused and unfocused window borders have a different border color, configurable per program.  
Windows 11 only.

## Preview

![Zoom](img/zoom.png?raw=true)
![Fullscreen](img/fullscreen.png?raw=true)

## Installing

- Download `cute-borders.exe` from [GitHub Releases](https://github.com/keifufu/cute-borders/releases/latest)
- Start the executable
- Select "install" in the tray menu

## Updating

Assuming you have previously already installed cute-borders:
- Exit cute-borders
- Download the version of cute-borders you want to update to
- Simply run the executable. It will update automatically and run this version on startup from now on.

## Configuration

The config is located at `%UserProfile%/.cuteborders/config.yaml`.  
You can open it via the tray icon > Open config

Colors are specified by #hex format or certain special cases:
- default, the default behavior in Windows
- transparent, no border
- accent, use the accent color from Windows
- rainbow, cycle slowly through a rainbow, adjusted by `rainbow_speed`

If `websocket_port` is set in the config, this option is available:
- websocket:<NAME> / <FALLBACK>
It opens one server that listens for colors, and uses the most recent color received per name. If a websocket sends a text message `firefox #c6a0f6`, then borders specified as websocket:firefox will become #c6a0f6. Fallback is used whenever a text message like `firefox none` is received, or if no messages had been received yet.

Window rules may specify a `backdrop` on Windows 11 22621 and later.
- acrylic, apply a transparent blurred effect to the windo background.

Example config:

```yaml
hide_tray_icon: false
window_rules:
  - match: "Global"
    active_border_color: "#c6a0f6"
    inactive_border_color: "#ffffff"
  # Example rules
  # color can either be hex or "transparent"
  - match: "Title"
    contains: "Mozilla Firefox"
    active_border_color: "#c6a0f6"
    inactive_border_color: "#ffffff"
  - match: "Class"
    contains: "MozillaWindowClass"
    active_border_color: "#c6a0f6"
    inactive_border_color: "#ffffff"
```
