# Opsero Hugo theme

Shared theme for the Opsero websites. It reproduces the look of the Thulite
Doks theme that the sites used before, without Node.js or npm: Hugo extended
compiles the SCSS and everything else is vendored.

## Using it in a site

Add the theme as a git submodule at `themes/opsero` and set `theme = "opsero"`
in the site's `hugo.toml`:

```
git submodule add https://github.com/fpgadeveloper/opsero-hugo-theme.git themes/opsero
```

Netlify checks out submodules automatically. After cloning a site, run
`git submodule update --init`. To pick up theme changes, run
`git submodule update --remote themes/opsero` in the site and commit the new
submodule pointer.

Requires Hugo extended (it compiles the SCSS with the built-in libsass).

## What it provides

* `baseof.html` with blocks `main`, `sidebar-prefooter` and `sidebar-footer`
* Navbar with light/dark logos, the `main` menu (one level of dropdowns) and
  a color mode toggle; offcanvas menu on small screens
* Opsero footer, driven by `footer` in `data/homepage.yml`
* SEO tags, favicons and web manifest, robots.txt, sitemap
* Default `single.html` (type `legal` shows a "Last updated" line),
  `list.html` and `404.html`

## Site configuration

```toml
# hugo.toml
theme = "opsero"

# params.toml
description = "..."
images = ["cover.jpg"]               # Open Graph / Twitter image
logoImage = "images/logo.png"
logoImageDark = "images/logo-dark.png"
logoWidth = "200px"
# footer = "..."                     # replaces the default copyright line
[social]
  twitter = "fpgadeveloper"
[seo.title]
  separator = " - "
[seo.schemas]
  name = "Opsero Electronic Design Inc."
  logo = "favicon-512x512.png"
```

Page front matter can set `seo.title`, `seo.description`, `seo.canonical`,
`seo.noindex` and `images`.

Sites provide `assets/favicon.png` (at least 512x512) and `assets/favicon.svg`.

## Styling

`assets/scss/main.scss` is the stylesheet. Sites override two files:

* `assets/scss/common/_variables-custom.scss`: Bootstrap variables such as
  `$primary` and `$link-color`
* `assets/scss/common/_custom.scss`: extra styles

Sites can override `_partials/head/custom-head.html` and
`_partials/footer/scripts-custom.html` to add tags.

## Vendored code

* Bootstrap 5.3.8 SCSS and JS bundle (MIT, `assets/bootstrap/LICENSE`)
* Doks SCSS and color-mode script from @thulite/doks-core 1.8.3
  (MIT, `LICENSE.thulite`)
* Jost font (SIL Open Font License, `static/fonts/vendor/jost/OFL.txt`)
* Tabler icons, inlined in `_partials/icon.html` (MIT)
