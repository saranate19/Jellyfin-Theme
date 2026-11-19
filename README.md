# Martimon Theme for Jellyfin

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
   @import url("https://cdn.jsdelivr.net/gh/saranate19/Jellyfin-Theme@main/martimon-theme.css");
   ```

3. Save, then reload the page with **Ctrl+F5**.

The `@import` line must be the first thing in the box. You can add your own overrides below it.

### Without a CDN

Paste the full contents of `martimon-theme.css` into the Custom CSS box instead.

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

## Add your own icon / logo (optional)

By default the theme shows Jellyfin's original logo. To use your own, add a few lines of CSS **below** the `@import` line in Dashboard → General → Custom CSS code. Don't edit the hosted theme file, because your changes would be lost on the next update.

### 1. Get your image online

Pick one:

- **Any image URL.** Upload your logo to your own GitHub repo, Imgur or similar and copy the direct link to the image file (it should end in `.png`, `.svg` or `.webp`). With a GitHub repo you can use a jsDelivr link, for example `https://cdn.jsdelivr.net/gh/USERNAME/REPO@main/logo.png`.
- **The LogoSwap plugin (no hosting needed).** LogoSwap lets you upload a logo in Jellyfin, serves it from your own server at `/logoswap/image`, and **adds its CSS to your Custom CSS box automatically** (a block marked `/* LogoSwap CSS */ ... /* END LogoSwap CSS */`). You don't need to write that part yourself. Just keep the theme's `@import` line first in the box, above LogoSwap's block, and leave LogoSwap's block alone because the plugin updates it each time you upload a new logo. If the logo in the top-left header still shows the original after that, add the rule from step 2 below and use `/logoswap/image` as the address. Paths starting with `/` only work in the Custom CSS box, never inside the hosted theme file.

- **The Jellyfin Enhanced plugin (upload in the dashboard, no CSS needed).** Jellyfin Enhanced has a **Custom Image Assets** section (called Custom Branding in some versions) where you upload your own images. It needs the File Transformation plugin installed. Open Dashboard → Plugins → Jellyfin Enhanced → Other Settings, upload your images, click **Save Settings**, then press Ctrl+F5. The files are stored in the plugin's config folder, so they survive Jellyfin updates. You can upload:

  | Slot | What it is | Recommended |
  | --- | --- | --- |
  | Icon Transparent | The icon in the top-left beside the server version | 536×536 px PNG with transparency |
  | Favicon | Browser tab icon | 256×256 px ICO, PNG or SVG |
  | Banner Dark | Splash screen banner for light mode | 1302×378 px PNG, JPG or WebP |
  | Banner Light | Splash screen banner for dark mode | 1302×378 px PNG, JPG or WebP |
  | Apple Touch Icon | Icon shown when adding to an iOS home screen | 180×180 px PNG |

  Because this replaces the logo files themselves, the CSS in steps 2 and 3 is usually not needed. Add it only if a logo still shows the original.

Every plugin here is optional. Without one, steps 2 and 3 below work with a normal image URL, so you can skip the plugin.

A transparent PNG or SVG, wider than it is tall, works best.

### 2. Replace the header logo (top left)

```css
.MuiAppBar-root a.MuiButton-root[href="#/"] .MuiButton-startIcon img {
    content: url("https://example.com/your-logo.png") !important;
    height: 34px !important;   /* make bigger or smaller */
    max-width: 160px !important;
    width: auto !important;
    object-fit: contain;
}
```

### 3. Replace the logo in other places (optional)

This covers the sidebar, admin menu and login page logos:

```css
.pageTitleWithLogo, .pageTitleWithDefaultLogo,
.logoImage, .navDrawerLogo, .adminDrawerLogo {
    background-image: url("https://example.com/your-logo.png") !important;
    background-size: contain !important;
    background-repeat: no-repeat !important;
    background-color: transparent !important;
}

img[src*="banner-light"], img[src*="banner-dark"],
img[src*="icon-transparent"], .imgLogoIcon {
    content: url("https://example.com/your-logo.png") !important;
}
```

### 4. Login page background (optional)

Upload an image under Dashboard → General → Branding, then add:

```css
#loginPage {
    background-image: url("/Branding/Splashscreen?format=jpg&foregroundLayer=1");
}
```

### Notes

- Replace `https://example.com/your-logo.png` with your own link in every rule.
- Reload with **Ctrl+F5** after saving.
- If the logo disappears after you change it with a plugin, the image link may have a version number at the end (`?v=...`). Update it.
- The browser tab icon (favicon) can't be changed with CSS. Use the Jellyfin Enhanced upload above.

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
