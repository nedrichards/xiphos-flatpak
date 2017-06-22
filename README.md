# xiphos-flatpak
[Flatpak](https://www.flatpak.org) that gives the user access to the [Xiphos](https://github.com/crosswire/xiphos) Bible reader.

Instructions:
-------------

(1) Install the flatpak repository for GNOME:
```
flatpak remote-add --from gnome https://sdk.gnome.org/gnome.flatpakrepo

```
(2) Install the required runtimes
```
  flatpak install gnome org.gnome.Sdk
  flatpak install gnome org.gnome.Platform
```
(3) Build the app from this directory:
```
flatpak-builder --force-clean --ccache --require-changes --repo=repo app ccom.github.crosswire.Xiphos.json
```
(4) Add a remote to your local repo and install it:
```
flatpak --user remote-add --no-gpg-verify xiphos-repo /path/to/your/flatpak/repo
flatpak --user install xiphos-repo com.github.crosswire.Xiphos
```
(5) Run the DevApp:
```
flatpak run com.github.crosswire.Xiphos
```

Note that if you do further changes in the `appdir` (e.g. to the metadata), you'll need to re-publish it in your local repo and update before running it again:
```
flatpak build-export /path/to/your/flatpak/repo /path/to/flatpak/appdir
flatpak --user update com.github.crosswire.Xiphos
```

Last, you can bundle it to a file with the `build-bundle` subcommand:
```
flatpak build-bundle /path/to/your/flatpak/repo com.github.crosswire.Xiphos.flatpak com.github.crosswire.Xiphos
```
