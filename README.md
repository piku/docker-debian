# Docker Image for Piku

This image is currently intended only for testing (for both offline testing and integration into a forthcoming CI pipeline) It is based on Debian because that is the more "neutral" approach, but Alpine and Ubuntu versions are forthcoming.

## Usage

Since this uses my cross-platform build scheme, building the image on a standard PC requires you to issue the following commands:

    make wrap-amd64
    make build-amd64

## Todo

* [ ] Scripts for testing sample apps against container
* [ ] Map volume with SSH keys
* [ ] Add S6 init system
* [x] Initial build with all required packages and nominal install
