# JDK Mission Control Flatpak


## Prerequisites
Install `flatpak` and `flatpak-builder`, add the Flathub remote and
install the Gnome runtime and SDK along with the OpenJDK 11 extension:
```bash
sudo dnf install flatpak flatpak-builder
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
flatpak install flathub org.gnome.Platform//3.32 org.gnome.Sdk//3.32 org.freedesktop.Sdk.Extension.openjdk11
```

## Build
First, [build JDK Mission Control from source](http://hg.openjdk.java.net/jmc/jmc/file/tip/README.md#l177).

Place `jmc/target/products/org.openjdk.jmc-linux.gtk.x86_64.tar.gz` into this directory before continuing with the next step.

Build the JMC Flatpak and export to repo:
```bash
flatpak-builder --repo repo build org.openjdk.Jmc.json --force-clean
```

To run this freshly-built Flatpak, execute:
```bash
flatpak-builder --run build org.openjdk.Jmc.json jmc
```

## Validation tools
Desktop file:
```bash
desktop-file-validate org.openjdk.Jmc.desktop
```

Appdata file:
```bash
appstream-util validate-relax org.openjdk.Jmc.appdata.xml
```
