# CraftOS &nbsp; [![bluebuild build badge](https://github.com/bominic27644/craftos/actions/workflows/build.yml/badge.svg)](https://github.com/bominic27644/craftos/actions/workflows/build.yml)

A custom bazzite image that adds a minecraft only gamescope session for use with the wayland craft mod.

## Installation

To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:

  For Nvidia:

  ```bash
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/bominic27644/craftos-nvidia:latest
  ```

  For AMD/Intel graphics:

  ```bash
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/bominic27644/craftos:latest
  ```

- Reboot to complete the rebase:

  ```bash
  systemctl reboot
  ```

- Then rebase to the signed image, like so:

  For Nvidia graphics:

  ```bash
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/bominic27644/craftos-nvidia:latest
  ```

  For AMD/Intel graphics:

  ```bash
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/bominic27644/craftos:latest
  ```

- Reboot again to complete the installation

  ```bash
  systemctl reboot
  ```

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/bominic27644/craftos
```
