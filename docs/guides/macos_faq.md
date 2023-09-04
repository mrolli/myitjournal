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

## How can I get rid of com.apple.provenance

Actually it's easy, not even sudo necessary! Just issue the following command
for current working directory recursively down:

```bash
xattr -rd com.apple.provenance
```

**BUT:** This does only work in Termianl.app! Not in iTerm2, not in Wezterm,
not in $you-name-it>. Just! In! Terminal.app! Weird, isn't it?

By the way, `com.apple.provenance` is a new extended attribute mark files that
where quarantined but you choose to allowlist them. So this marks them has
having been quarantined. It has been introduced with Ventura.
