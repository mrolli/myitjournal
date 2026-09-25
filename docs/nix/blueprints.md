# Blueprints

## Aspects Design Patterns

The easiest and most straightforward way to deploy apps and their configuration
using Home Manager, i.e.

```nix
{ ... }:
{
  den.aspects.<app>.homeManager = {
    programs.<app> = {
      enable = true;
      config = {
        option1 = "value";
        option1 = "value"
      };
    };
  };
}
```

For applications, where Home Manager does not (yet) provide an option to manage
them or when tools shall be installed system-wide in a path, other routes can be
taken. Three pattern are illustrated below.

### Package And Config By Home Manger

This recipe will install an application and its configuration using the Home
Manager and thus is managed per user. See [Home Manager
Manual](https://nix-community.github.io/home-manager/options/home-manager/programs/index.html)
or better use [NixOS Search](https://search.nixos.org/options?channel=26.05&) to
find available options.  
In the example, Home Manager will install the package
via nixpkgs and create a config file `<app>/config` in the configuration
directory defined by XDG of every user implementing realising this aspect.

```nix
{ ... }:
let
  homeModule =
    { pkgs, ... }:
    {
      home.packages = [ pkgs.<app> ];

      xdg.configFile."<app>/config".text = ''
        # plain options file
        option1 = "value"
        option1 = "value"
      '';
    };
in
{
  den.aspects.<app>.homeManager = homeModule;
}
```

### Package system-wide, Config By Home Manager

This recipe will install an application from its Nix package in
[NixOS/nixpkgs](https://github.com/NixOS/nixpkgs) system-wide - available to all
users on a machine - and create a config file `<app>/config` in the
configuration directory defined by XDG of every user implementing realising this
aspect.

```nix
{ ... }:
let
  systemModule =
    { pkgs, ... }:
    {
      environment.systemPackages = [ pkgs.<app> ];
    };

  homeModule =
    { ... }:
    {
      xdg.configFile."<app>/config".text = ''
        # plain options file
        option1 = "value"
        option1 = "value"
      '';
    };
in
{
  den.aspects.<app> = {
    nixos = systemModule;
    darwin = systemModule;
    homeManager = homeModule;
  };
}
```

### Package By Homebrew, Config By Home Manager

This recipe will install the application system-wide using Homebrew. As such,
this aspect can only be used on Darwin hosts. The configuration file
`<app>/config` is again managed by Home Manager and is created in the
configuration directory defined by XDG of every user implementing realising this
aspect.

```nix
{ ... }:
let
  homeModule =
    { pkgs, ... }:
    {
      xdg.configFile."<app>/config".text = ''
        # plain options file
        option1 = "value"
        option1 = "value"
      '';
    };
in
{
  den.aspects.<app> = {
    darwin.homebrew.brews = [ "<app>" ];
    homeManager = homeModule;
  };
}
```
