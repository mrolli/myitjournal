# Script Deployment Patterns

Personal shell scripts can be deployed in several ways. The right choice depends
on whether the script should be a normal executable, which platform it targets,
whether its dependencies should be pinned, and where its command should appear
on `PATH`. These patterns can be mixed: choose an approach for each script
instead of forcing every script into one deployment mechanism.

## Home Manager File Link

Keep the source in the repository and have Home Manager link it into the user's
XDG binary directory. With Home Manager's XDG integration enabled,
`xdg.binHome` defaults to `~/.local/bin`; `xdg.localBinInPath` must be enabled
to add that directory to the session `PATH`.

```nix
{ ... }:
{
  xdg.enable = true;
  xdg.localBinInPath = true;

  home.file.".local/bin/my-script" = {
    source = ./scripts/my-script;
    executable = true;
  };
}
```

**Pros**

- The command lives at the familiar, XDG-conforming `~/.local/bin` path.
- The source remains an ordinary script that can be edited and reviewed.
- Works for Bash, zsh, Python, PHP, and other scripts without wrapping them
  in a Bash-specific helper.
- Platform-specific scripts can be linked conditionally from a Darwin or
  Linux aspect.

**Cons**

- Home Manager deploys the file, but does not supply its command dependencies.
  They must already be available from the system, Homebrew, or another package.
- Dependencies and their versions are not captured as part of the script.
- Home Manager-managed links are declarative; editing the deployed file is not
  the way to change the source.

Use this when preserving a script as a standalone source file and putting it
specifically in `~/.local/bin` are the main requirements.

## `writeShellApplication` with Runtime Inputs

For Bash scripts that should use Nix-provided tools, build an executable with
`[pkgs.writeShellApplication](https://noogle.dev/f/pkgs/writeShellApplication/)`
and list its command dependencies in `runtimeInputs`.

```nix
{ pkgs, ... }:
let
  my-script = pkgs.writeShellApplication {
    name = "my-script";
    runtimeInputs = with pkgs; [
      curl
      jq
    ];
    text = ''
      curl --fail --silent https://example.org/data.json | jq .
    '';
  };
in
{
  home.packages = [ my-script ];
}
```

At runtime the declared tools are added to the script's `PATH`. Home Manager
installs the resulting executable through its profile, normally under
`~/.nix-profile/bin` (or the active Home Manager profile), rather than
`~/.local/bin`. The Home Manager profile is normally added to `PATH`.

The `darwin-switch-summary` script in [my
nix-config](https://github.com/mrolli/nix-config/modules/aspects/apps/personal-scripts.nix)
is a local example: it uses `writeShellApplication` with `nix`, `jq`,
`coreutils`, `gnugrep`, and `gnused` as runtime inputs, then includes the
derivation in Darwin-only `home.packages`. That file separately adds
`~/.local/bin` to `PATH`; this does not relocate the package executable from the
Home Manager profile.

**Pros**

- Declared runtime tools are available in the wrapper's `PATH` and retained
  in its Nix store closure.
- Dependencies can be pinned with the flake's Nixpkgs input without making
  those tools global user packages.
- Provides a standard place for shell checks during the build.
- Naturally fits Home Manager package and platform-conditional composition.

**Cons**

- It is designed for Bash scripts; zsh, Python, PHP, and other languages need
  another pattern or their own language-specific builders.
- Its strict Bash defaults and build-time checks can expose assumptions or
  change behavior in an existing script, so test before converting it.
- The executable normally lands in the Home Manager profile's `bin`, not
  `~/.local/bin`.
- Wrapping a large existing script can add Nix expression boilerplate; keep
  the source in a separate file and read it into the derivation if that is
  clearer.

Choose this for Bash commands where explicit, reproducible command-line
dependencies are valuable.

## `writeShellScriptBin` and `writeScriptBin`

These helpers create a small executable derivation and can be installed
through `home.packages`.

```nix
{ pkgs, ... }:
{
  home.packages = [
    (pkgs.writeShellScriptBin "hello-user" ''
      printf 'Hello, %s!\\n' "$USER"
    '')
  ];
}
```

`writeShellScriptBin` is convenient for a shell script. `writeScriptBin` is a
lower-level alternative when the script needs a custom interpreter or
shebang. Dependencies can be referenced by explicit Nix store paths in the
script, but these helpers do not provide the same `runtimeInputs` interface
as `writeShellApplication`.

**Pros**

- Short and convenient for small generated commands or glue scripts.
- Produces a Nix-managed executable in the Home Manager profile.
- Can reference exact Nix package executables directly.

**Cons**

- Runtime dependency setup and validation are more manual than with
  `writeShellApplication`.
- Inline text can become hard to maintain as a script grows.
- Like other `home.packages`, the command normally appears in the profile's
  `bin`, not `~/.local/bin`.

## Language-Specific Builders

When a script depends on language libraries or belongs to a non-shell runtime,
use the relevant Nixpkgs language tooling—for example, Python application
builders for Python code—instead of forcing it through a shell wrapper.

**Pros**

- Can package language dependencies and expose a command entry point
  reproducibly.
- Fits scripts that are growing into real applications with tests or several
  modules.

**Cons**

- Requires learning and maintaining that language's packaging conventions.
- Can be excessive for a short script that only calls a few existing
  executables.
- The generated command normally goes into a Nix package/profile `bin`
  directory.

Use this when the language ecosystem, rather than external command-line
programs, provides most of the script's dependencies.

## A Local Package or Bundle

Several related commands can be defined as packages and added individually to
`home.packages`. If one combined output is useful, `symlinkJoin` can combine
their `bin` entries:

```nix
{ pkgs, ... }:
let
  first = pkgs.writeShellApplication {
    name = "first-command";
    text = "printf '%s\\n' first";
  };
  second = pkgs.writeShellApplication {
    name = "second-command";
    text = "printf '%s\\n' second";
  };
  my-scripts = pkgs.symlinkJoin {
    name = "my-scripts";
    paths = [ first second ];
  };
in
{
  home.packages = [ my-scripts ];
}
```

For a larger collection, define derivations in a package-oriented directory
and compose them through a local package set, `callPackage`, or flake package
outputs.

**Pros**

- Creates a clear package boundary for reusable or growing command-line
  tools.
- Each command can keep its own dependencies and checks, even when several
  are grouped for installation.
- Can grow to include completion files, documentation, and tests.

**Cons**

- Adds package/module structure and maintenance overhead.
- A blanket bundle can obscure platform differences and accidentally include
  scripts that are unsafe or irrelevant on a host.
- `symlinkJoin` groups outputs; it does not automatically make their
  dependencies correct or portable.

Prefer individual package definitions with an explicit allow list over
automatically deploying every file in a scripts directory.

## Shell Functions and Separate Completions

A shell function is suitable when a command is inherently part of an
interactive shell session. It can use shell state directly, but it is not a
standalone executable and cannot be called by other programs or non-interactive
scripts.

When a command should work both interactively and as a normal executable,
deploy the command separately and manage shell completion as shell-specific
configuration. For example, `music` can be an executable while `_music` is a
zsh completion function:

```nix
{
  programs.zsh.siteFunctions._music = ''
    # zsh completion function for the music command
    _arguments '1:command:(play pause next previous)'
  '';
}
```

The completion should be registered/discovered through zsh's completion
system; it should not be embedded in the executable script.

**Pros**

- A standalone command works from interactive shells, other scripts, and
  applications.
- Completion remains available to zsh without coupling the command itself to
  zsh startup.
- Platform-specific commands can be deployed only on supported systems.

**Cons**

- The command and completion are separate files/configuration concerns that
  must stay in sync.
- A shell function is simpler, but only exists in shells that load it.

## Choosing a Pattern

Choose per script after checking its interpreter, supported platforms,
external commands, hard-coded paths, and safety:

| Requirement | Good starting point |
| --- | --- |
| Must appear specifically in `~/.local/bin` | Home Manager link in `xdg.binHome` |
| Bash script needs pinned CLI tools | `writeShellApplication` with `runtimeInputs` |
| Tiny generated shell command | `writeShellScriptBin` |
| Non-shell language dependencies | Language-specific builder/package |
| Reusable or growing tool with tests/docs | Local Nix package |
| Related commands intentionally installed together | Explicit package list or `symlinkJoin` |
| Interactive-only behavior | Shell function |
| Normal executable plus zsh completion | Separate command and completion |

Keep script sources in the flake/repository, use an explicit allow list rather
than deploying the entire directory, and gate platform-specific commands.
Declare dependencies that should be reproducible, but leave intentionally
host-provided tools outside the wrapper.
