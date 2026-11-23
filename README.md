# Ridge for LuCI

Ridge is a light dashboard theme for the Arcadyan AW1000. It uses a collapsible LuCI sidebar with outline icons, blue controls and a local copy of Inter. The package targets OpenWrt 25.12 with APK. It uses the installed LuCI Bootstrap theme for shared controls and sign-in behavior.

## Install on NoobWRT

From your computer, copy the APK to the router. Use your router's address in place of `192.168.1.1`.

```sh
scp -O dist/luci-theme-ridge-1.0.0-r3.apk root@192.168.1.1:/tmp/
```

On the router, install the unsigned local package.

```sh
apk add --allow-untrusted /tmp/luci-theme-ridge-1.0.0-r3.apk
```

In LuCI, go to **System → System → Language and Style**, choose **Ridge** under **Design**, then **Save & Apply**. You can select **NoobWrt** in the same menu to switch back. To switch back from SSH, run:

```sh
uci set luci.main.mediaurlbase=/luci-static/noobwrt
uci commit luci
```

Refresh LuCI after switching. To remove the theme, run `apk del luci-theme-ridge` on the router. If Ridge is still selected, the package selects NoobWrt if registered, or Bootstrap.

## Build

Run `./packaging/build-apk.sh /path/to/staging_dir/host/bin/apk` with the host APK tool from the OpenWrt 25.12 SDK or Image Builder. The package is written to `dist/`.

The LuCI templates are based on Bootstrap at commit `128a781` and licensed under Apache-2.0. Inter 4.1 is distributed under the SIL Open Font License included with the font.

The sidebar sprite uses [Lucide 0.468.0](https://github.com/lucide-icons/lucide/tree/0.468.0/icons). The ISC and Feather MIT notices are included in `root/usr/share/licenses/luci-theme-ridge/LUCIDE-LICENSE`.
