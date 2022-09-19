This page outlines stuff I stumble upon, remember that I actually know this, but
still not use in my daily practice and forgot about. Shame on me, because I
should use this!

## Use the right tool for the work

### `install`

Often there is a simple tool that does exactly what you want. Consider this
piece of a bash script:

```
mkdir /etc/systemd/system/podman.service.d
chmod 0755 /etc/systemd/system/podman.service.d
chown root:root /etc/systemd/system/podman.service.d
cp podman.conf /etc/systemd/system/podman.service.d/
chmod 0644 /etc/systemd/system/podman.service.d/podman.conf
chown root:root /etc/systemd/system/podman.service.d/podman.conf
```

The above works perfectly well. Is it readable? Yes, probably. Still, there is a
tool for this. Not often used in the wild, but mandatory for package maintainers
- `install`. The sole purpose of this is tool is to install files with the
correct mode and ownership in a single command. The above using `install` would
then look like:

```
install -o root -g root -m 0755 -d /etc/systemd/system/podman.service.d
install -o root -g root -m 0644 podman.conf /etc/systemd/system/podman.service.d
```

More elegant, isn't it? So, go and use `install` from now on!
