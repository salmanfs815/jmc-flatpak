# JDK Mission Control Flatpak


## Prerequisites
Install `flatpak` and `flatpak-builder`, add the Flathub remote and
install the Freedesktop runtime and SDK along with the OpenJDK 11 extension:
```bash
sudo dnf install flatpak flatpak-builder
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
flatpak install flathub org.freedesktop.Platform//18.08 org.freedesktop.Sdk//18.08 org.freedesktop.Sdk.Extension.openjdk11
```

## Build
First, build JDK Mission Control from source: http://hg.openjdk.java.net/jmc/jmc/file/tip/README.md#l177

Place `jmc/target/products/org.openjdk.jmc-linux.gtk.x86_64.tar.gz` into the same directory as `org.openjdk.Jmc.json` before continuing with the next step.

Build the JMC Flatpak and export to repo:
```bash
flatpak-builder --repo repo build org.openjdk.Jmc.json --force-clean
```

To run this freshly-built Flatpak, execute:
```bash
flatpak-builder --run build org.openjdk.Jmc.json jmc
```

