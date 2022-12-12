# macOS Frequently Asked Questions

## How do I find out the Bundle ID of an Application?

Run the following snippet of Applescript with the exact name of the Application
in question, i.e. "Alfred 5" or "TextMate"

```sh
$ osascript -e 'id of app "Music"'
com.apple.Mail
```

## How do I reset macOS permission for an Application?

Launch Terminal and quit the app in question, i.e. Alfred. Paste the following
command in Termin and press Return.

```sh
tccutil reset All com.runningwithcrayons.Alfred
```
