# Zallery theme for Zola

Gallery and portfolio theme for [Zola](https://getzola.org).

Demo Site: [gamingrobot.github.io/zallery-demo](https://gamingrobot.github.io/zallery-demo/)  
Personal Portfolio: [gamingrobot.art](https://gamingrobot.art/)

## Screenshots

| Light mode | Dark mode |
| :------: | :-----------: |
| ![light mode](screenshot-light.jpg) | ![dark mode](screenshot-dark.jpg) |

## Features

- Auto creation of mobile friendly images
- Auto creation of thumbnails
- Auto conversion of images
- Maximize button on images
- Video embed support
- ModelViewer and Sketchfab support
- Responsive and Mobile friendly

## Installation

Clone the theme into the themes folder:

```bash
git clone https://github.com/gamingrobot/zallery.git themes/zallery
```

Note: It is recomended that you copy the `config.toml` from the `themes/zallery` folder to the root folder of your site.

Then set your theme setting in `config.toml` to `zallery`:

```toml
theme = "zallery"
```

## Customization

To customize the theme's colors you will need to copy the `_variables.scss` into your sites `sass` folder and create a `zallery.scss` file with:

```scss
@import 'variables';
@import '../themes/zallery/sass/imports';
```

See the demo site for an example: [github.com/gamingrobot/zallery-demo/tree/master/sass](https://github.com/gamingrobot/zallery-demo/tree/master/sass)

## Options

### Menu Items

Customize the header navigation links

```toml
[extra]
menu = [
    {url = "atom.xml", name = "Feed"},
    {url = "https://github.com/gamingrobot/zallery", name = "Github"},
]
```

### Browser Bar Theme Color

Customize color to set the browser's url bar on mobile

```toml
[extra]
theme_color = "#313131"
```

### Author Url

Url used for the name in the copyright

```toml
[extra]
author_url = "https://example.com"
```

### Copyright and Powered by

To hide the copyright set this to `true`

```toml
[extra]
hide_copyright = false
```

To hide the "Powered by Zola & Zallery" set this to `true`

```toml
[extra]
hide_poweredby = false
```

### Gallery

Settings for the gallery view's thumbnails

```toml
[extra]
thumbnail_size = 400 # size in pixels, you may need to adjust the media queries in _gallery.scss
thumbnail_format = "webp" # auto, jpg, png, webp
thumbnail_quality = 100 # value in percentage, only for webp and jpg
```

### `img` shortcode settings

Settings for the `img` shortcode, allowing for automatic conversion and creating mobile friendly images

```toml
[extra]
covert_images = false # set to true to convert images to to the format in the image_format setting
create_mobile_images = false # set to true to create mobile friendly versions of the image
image_format = "webp" # auto, jpg, png, webp
image_quality = 90 # value in percentage, only for webp and jpg
```

### Javascript libraries

#### ModelViewer

Set to `true` to enable [modelviewer](https://modelviewer.dev/) support

```toml
[extra]
modelviewer = true
```

#### GoatCounter

Set to the goatcounter tag to enable [goatcounter](https://www.goatcounter.com/) support

```toml
[extra]
goatcounter = ""
```

## Shortcodes

### `img`

```
{{ img(src="image.jpg", mobile_src="image-mobile.jpg", alt="alt text", text="text", fit="") }}
```

- `src` (required) - Image path
- `mobile_src` (optional) - Mobile friendly version
- `alt` (optional) - Alt text
- `text` (optional) - Text to put under the image (if `alt` is not specified, text will be use for alt text)
- `fit` (optioanl) - Defaults to "fit to width", can be set to `max-width` to make the image fill the width of the page

### `video`

```
{{ video(src="image.jpg", autoplay=false) }}
```

- `src` (required) - Video path
- `autoplay` (optional) - Set to `true` to enable autoplay

### `youtube` / `vimeo`

```
{{ youtube(id="", autoplay=false) }}
{{ vimeo(id="", autoplay=false) }}
```

- `id` (required) - Id of the video
- `autoplay` (optional) - Set to `true` to enable autoplay

### `model`

Note: Requires `modelviewer` to be enabled in `config.toml`

```
{{ model(src="image.jpg", skybox="", poster="") }}
```

- `src` (required) - Model path
- `skybox` (optional) -  Skybox HDR
- `poster` (optional) - Image to show when loading
- `alt` (optional) - Alt text

### `sketchfab`

```
{{ sketchfab(id="") }}
```

- `id` (required) - Id of the model
