# sed

!!! warning "Sed on Linux is not the same as sed on macOS!"

    One word of warning right away before you fall into the same pitfall as I did
    (several times!). The sed that is shipped with macOS does not work the same
    as GNU sed shipped with a Linux distribution. There are subtle differences
    like handling regular expressions or i.e. the `-i` option.
    If you want to be sure to have the same GNU sed as on Linux, install
    `gnu-sed` using Homebrew and then use gsed instead of sed or make your
    scripts platform-aware and build the commmands accordingly.

[Bruce Barnett: Intro and Tutorial to Sed](https://www.grymoire.com/Unix/Sed.html)
