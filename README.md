# Carburetor flatpak recepie
This is the recepie for packaging [carburetor](https://tractor.frama.io/carburetor) as flatpak.

## Update dependencies
### Python
Fill all python requirements (except `PyGobject` as that one is already provided in `org.gnome.Platform` runtime) in `requirements.txt` file and use [flatpak pip generator](https://github.com/flatpak/flatpak-builder-tools/tree/master/pip) to update `python3-requirements.json` as below:

    python3 flatpak-pip-generator --requirements-file=requirements.txt

### Golang
For any Golang project, go to the project directory and run:

    go run github.com/dennwc/flatpak-go-mod@latest <path/to/project/>

## Build the flatpak
    flatpak-builder --force-clean build-dir io.frama.tractor.carburetor.json

## Install the flatpak
    flatpak-builder --user --install --force-clean build-dir io.frama.tractor.carburetor.json

## Run the flatpak
    flatpak run io.frama.tractor.carburetor
