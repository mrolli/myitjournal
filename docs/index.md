# Home

On these pages you will find instructions, exercises, cheat sheets, references,
and tutorials. Originally the material was meant to teach our apprentices in
house a starting point on their quest to obtain new skills and learn new stuff.

Courses are more work instructions for learners of new stuff to guide them to a
goal. These link over to the guides - call them memorandums on my journey on a
lot of webpages where I gather snips and lines that are worth to be kept and
remembered - that are organized by topic.

Meanwhile this technical documentation might morph towards my personal
omnium-gatherum while still trying to be useful for our young learners.
Therefore it is and will always be in a flux.

!!! success "Have Fun!"
    Now start with whatever interests you the most.

Below follows the default index.md of a MkDocs installation as a quickref.

## Commands

- `mkdocs new [dir-name]` - Create a new project.
- `mkdocs serve` - Start the live-reloading docs server.
- `mkdocs build` - Build the documentation site.
- `mkdocs -h` - Print help message and exit.

## Project layout

```bash
mkdocs.yml    # The configuration file.
docs/
    index.md  # The documentation homepage.
    ...       # Other markdown pages, images and other files.
```

## Emojis, Icons and Keys

- :smile:   `:smile:`
- :material-account-circle:   `:material-account-circle:`
- :fontawesome-regular-face-laugh-wink:   `:fontawesome-regular-face-laugh-wink:`
- :octicons-repo-push-24:   `:octicons-repo-push-24:`
- :material-apple-keyboard-command:   `:material-apple-keyboard-command:`
- :material-apple-keyboard-option:   `:material-apple-keyboard-option:`
- :material-apple-keyboard-control:   `:material-apple-keyboard-control:`
- :material-apple-keyboard-shift:   `:material-apple-keyboard-shift:`
- :material-keyboard-return:   `:material-keyboard-return:`
- :material-keyboard-space:   `:material-keyboard-space:`
- ++space+f++   `++space+f++`
- ++command+f1++  `++command+f1++`

For more icons and emojis use the [emojis/icons search
bar](https://squidfunk.github.io/mkdocs-material/reference/icons-emojis/) in
the mkdocs-material documentation. The keyboard keys rendering is done using
the [`pymxdown.keys` extension](https://facelessuser.github.io/pymdown-extensions/extensions/keys/).

For the full documentation visit [material-mkdocs](https://squidfunk.github.io/mkdocs-material/)
and [mkdocs.org](https://www.mkdocs.org).

## Mermaid supported

``` mermaid
sequenceDiagram
  title: Cool Seq Diagram
  Alice->>John: Hello John, how are you?
  loop Healthcheck
      John->>John: Fight against hypochondria
  end
  Note right of John: Rational thoughts!
  John-->>Alice: Great!
  John->>Bob: How about you?
  Bob-->>John: Jolly good!
```
