# Martimon Theme for Jellyfin

A monochrome, frosted-glass theme for Jellyfin 12.

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
   @import url("https://cdn.jsdelivr.net/gh/saranate19/Jellyfin-Theme@main/martimon-theme.css");
   ```

3. Save, then reload the page with **Ctrl+F5**.

The `@import` line must be the first thing in the box. You can add your own overrides below it.


## Optional plugins

The theme styles these if they are installed. It works without them. Follow each repo's README to install it.

| Plugin | Author | Affects | Repo |
| --- | --- | --- | --- |
| Media Bar Enhanced | CodeDevMLH (fork of IAmParadox27's Media Bar) | Home hero carousel | [CodeDevMLH/jellyfin-plugin-media-bar-enhanced](https://github.com/CodeDevMLH/jellyfin-plugin-media-bar-enhanced) |
| KefinTweaks | ranaldsgift | Extra home sections, watchlist | [ranaldsgift/KefinTweaks](https://github.com/ranaldsgift/KefinTweaks) |
| Studio Hubs | G-grbz (part of Jellyfin-MonWUI) | Studio tiles | [G-grbz/Jellyfin-MonWUI-Plugin](https://github.com/G-grbz/Jellyfin-MonWUI-Plugin) |
| Jellyfin Enhanced | n00bcodr | Watchlist and extra buttons | [n00bcodr/Jellyfin-Enhanced](https://github.com/n00bcodr/Jellyfin-Enhanced) |
| InPlayerEpisodePreview | Namo2 | Episode list inside the player | [Namo2/InPlayerEpisodePreview](https://github.com/Namo2/InPlayerEpisodePreview) |
| JavaScript Injector | n00bcodr | Needed to load some of the above | [n00bcodr/Jellyfin-JavaScript-Injector](https://github.com/n00bcodr/Jellyfin-JavaScript-Injector) |

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

- Written against the Jellyfin 12 web client. Class names can change between versions.

## Troubleshooting

- **Nothing changed:** hard-reload with Ctrl+F5, and check that the `@import` line is first in the box.
- **Old version still showing:** purge the jsDelivr cache (see above) or pin a commit.
- **Something looks off after a Jellyfin or plugin update:** open an issue with a screenshot and your Jellyfin and plugin versions.

## Credits

Thanks to the authors of the plugins this theme styles: CodeDevMLH and IAmParadox27 (Media Bar), ranaldsgift (KefinTweaks), G-grbz (Studio Hubs / MonWUI), n00bcodr (Jellyfin Enhanced, JavaScript Injector) and Namo2 (InPlayerEpisodePreview).

## License

See [LICENSE](LICENSE).
