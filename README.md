# browsershot

Wrap an image in a generated Safari/macOS browser frame or iPhone frame.

```sh
./browsershot <sourcefile> --address my.addressbar-value.com --iphone --light --stylized
```

Defaults:

- `--address` defaults to `example.com`
- dark mode is used unless `--light` is passed
- realistic Safari is used unless `--stylized` is passed
- shadows are included unless `--no-shadow` is passed

Example output:

```sh
image.png.safari-stylized-light.png
image.png.safari-realistic-dark.png
image.png.safari-iphone-stylized-light.png
```
