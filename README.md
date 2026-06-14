# browsershot

Wrap one or more images in generated Safari/macOS browser frames or iPhone frames.

```sh
./browsershot <sourcefile> [sourcefile ...] --address my.addressbar-value.com --iphone --light --stylized
```

Defaults:

- `--address` defaults to `example.com`
- dark mode is used unless `--light` is passed
- realistic Safari is used unless `--stylized` is passed
- shadows are included unless `--no-shadow` is passed
- when multiple source files are passed, browsers are stacked with the first image on top
- stacked browsers default to `--right 80 --bottom 50`, placing the top browser 80px right and 50px below the browser behind it
- `--left <px>` and `--right <px>` are mutually exclusive
- `--top <px>` and `--bottom <px>` are mutually exclusive
- masks crop source images before the browser frame is generated
- overlays render above the browser stack and below cursors

Stack top-browser direction and spacing:

```sh
./browsershot first.png second.png third.png --left 40 --top 24
```

Masking:

```sh
./browsershot --mask x:100 first.png second.png
./browsershot first.png --mask bottom:100px left:50%
./browsershot first.png --imask top:720px left:1280px
```

`--mask` removes the specified edge regions. `--imask` keeps the specified edge regions, so `--imask top:720px left:1280px` keeps the top 720px and left 1280px of the image.

If `--mask` or `--imask` appears before any source file, it applies to all source files. If it appears after a source file, it applies only to that source file.

Mask values can use bare pixels, `px`, or `%`. Supported mask keys are `top`, `right`, `bottom`, `left`, `x`, and `y`.

Overlays and cursors:

```sh
./browsershot first.png second.png --overlay dragoverlay.png,400,250 --cursor 500,300
./browsershot first.png --overlay dragoverlay.png,400,250,50%
```

Final output is layered as back browser, middle browsers, top browser, overlays, then cursors.

Overlays use the top-left corner at `x,y` and preserve transparency. Cursor coordinates are also from the top-left of the final output.

Example output:

```sh
image.png.safari-stylized-light.png
image.png.safari-realistic-dark.png
image.png.safari-iphone-stylized-light.png
image.png.safari-stack-realistic-dark.png
```
