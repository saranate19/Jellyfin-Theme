# Watched Style for Jellyfin

A monochrome, frosted-glass theme for Jellyfin 12, inspired by the look of watched.cx: dark background, white active pill, off-white PLAY button, full-bleed hero and a minimal video player.

> Tested against Jellyfin 12.x with the plugins listed below. Not every plugin is required.

## Features

- Frosted-glass header, menus and dialogs, with a white active-tab pill
- Full-height hero for the Media Bar Enhanced plugin (title logo, info line, buttons, dots)
- Home rows that start at the page margin and run off the right edge
- Series page with the episode carousel lined up with the rest of the page
- Minimal video player: thin full-width progress line, time and "Ends at" on the left, centered transport, volume / subtitles / audio / settings / fullscreen on the right
- Player scales down on one line in small windows
- Glass-style player menus (settings, audio, subtitles, quality, speed)
- Restyled in-player episode list (InPlayerEpisodePreview)
- Monochrome throughout, no accent colour

## Install

1. In Jellyfin open **Dashboard → General → Custom CSS code**.
2. Replace the contents with this line, using your own GitHub user and repo name:

   ```css
   @import url("https://cdn.jsdelivr.net/gh/YOURUSER/YOURREPO@main/watched-style.css");
   ```

3. Save, then reload the page with **Ctrl+F5**.

The `@import` line must be the first thing in the box. You can add your own overrides below it.

### Updating

jsDelivr caches `@main` for up to about 12 hours. To refresh straight away, open:

```
https://purge.jsdelivr.net/gh/YOURUSER/YOURREPO@main/watched-style.css
```

Or pin a release or commit (`@v1.0.0`, `@<commit-hash>`) and change it when you update.

### Without a CDN

Paste the full contents of `watched-style.css` into the Custom CSS box instead.

## Optional plugins

The theme styles these if they are installed. It works without them.

| Plugin | What it affects |
| --- | --- |
| Media Bar Enhanced | Home hero carousel |
| KefinTweaks | Extra home sections |
| Studio Hubs | Studio tiles |
| Jellyfin Enhanced | Watchlist and extra buttons |
| InPlayerEpisodePreview | Episode list inside the player |
| JavaScript Injector | Needed to load some of the above |

## Customising

Most colours and sizes are set as variables at the top of the file:

```css
:root {
    --wx-glass: rgba(18, 18, 18, 0.62);   /* panel background */
    --wx-border: rgba(255, 255, 255, 0.1);
    --wx-light: #f4f0f1;                  /* off-white buttons */
    --mediaBarHeight: 77vh;               /* hero height */
}
```

Change them in your own Custom CSS below the `@import` line instead of editing the hosted file, so updates don't overwrite your changes.

## Known limitations

- The Studio Hubs rail container is not styled yet.
- Jellyfin's settings menu stays a list; a combined audio / subtitle / quality panel would need JavaScript.
- Written against the Jellyfin 12 web client. Class names can change between versions.

## Troubleshooting

- **Nothing changed:** hard-reload with Ctrl+F5, and check that the `@import` line is first in the box.
- **Old version still showing:** purge the jsDelivr cache (see above) or pin a commit.
- **Something looks off after a Jellyfin or plugin update:** open an issue with a screenshot and your Jellyfin and plugin versions.

## Credits

- Visual inspiration: watched.cx (no assets are copied)
- Plugins by their respective authors, see the table above
- Font: [DM Sans](https://fonts.google.com/specimen/DM+Sans), SIL Open Font License
- Add any theme or CSS this was based on here

## License

See [LICENSE](LICENSE).
