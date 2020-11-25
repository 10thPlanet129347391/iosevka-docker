# fonts-iosevka

> Iosevka custom building with Docker and debian packages.

This repository provides an easy (and headless) way to build your own version of the Iosevka typeface without having to worry about dependencies and build environments.

## Build

1. Be sure to have Docker installed. Clone this repository.

```bash
git clone https://github.com/avivace/fonts-iosevka.git
``` 

2. If you want, prepare your custom build configuration following the [Customized Build](https://github.com/be5invis/Iosevka#customized-build) documentation or use the [Iosevka Build Customizer](https://typeof.net/Iosevka/customizer). Replace your `private-build-plans.toml` in the `build` folder with yours.

3. Build and run the Docker container

```bash
# Build the container
docker build -t iosevka_build . -f Dockerfile

# Launch the build on Iosevka git tag 3.7.1, using the build folder on the host
docker run -e FONT_VERSION=3.7.1 -it -v $(pwd)/build:/build iosevka_build
```

4. Done! Your built font files are available in the `build/dist` folder.

## Install

Copy the generated folders `~/.local/share/fonts` and run `fc-cache`.

```bash
cp -r build/dist/* ~/.local/share/fonts/
fc-cache
```

## Debian packaging

TODO

## References and links

- https://git.mmk2410.org/deb/fonts-iosevka
- https://github.com/ejuarezg/containers/tree/master/iosevka_font#container-method
- https://github.com/be5invis/Iosevka
- [Original Dockerfile](https://gist.github.com/tasuten/0431d8af3e7b5ad5bc5347ce2d7045d7)
- https://github.com/nodesource/distributions/blob/master/README.md
- https://premake.github.io/download.html#v5
- https://stackoverflow.com/questions/6482377/check-existence-of-input-argument-in-a-bash-shell-script
- https://gist.github.com/steinwaywhw/a4cd19cda655b8249d908261a62687f8
- https://stackoverflow.com/questions/1247812/how-to-use-grep-to-get-anything-just-after-name