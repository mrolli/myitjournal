# Nix

[NixOS & Flakes Book](https://nixos-and-flakes.thiscute.world/introduction/)

## Determinate Nix Installer

[DeterminateSystems/nix-installer](https://github.com/DeterminateSystems/nix-installer)

### Installing Nix

```bash
curl -fsSL https://install.determinate.systems/nix | sh -s -- install

```

### Upgrading Determinate Nix

If you've installed Determinate Nix, you can upgrade it using Determinate Nixd:

```bash
    sudo determinate-nixd upgrade
```

Alternatively, you can uninstall and reinstall with a different version of
Determinate Nix Installer.

### Uninstalling

You can remove Nix installed by Determinate Nix Installer by running:

```bash
    /nix/nix-installer uninstall
```

## Other Articles

[Build and Deploy Linux System from macOS (linux builders)](https://nixcademy.com/posts/macos-linux-builder/)
