# pkg-mate-settings-daemon (Menta Linux)

Debian packaging of a git snapshot of mate-settings-daemon master after 1.29.1 (e39a109; adds mouse natural-scroll; from debian-mate-team on Salsa, 1.26.1-1),
built with Wayland support (wlrandr plugin; gtk-layer-shell, wayland-protocols,
ayatana-appindicator) and with PolicyKit, smartcard, libnotify, libatspi,
libcanberra and libmatemixer explicitly enabled (build fails if any is missing).

Upstream has no separate in-process switch for this package: all plugins are
shared modules loaded into the single mate-settings-daemon process.

Versioning: `<upstream>-<debian rev>mentaN`, e.g. `1.29.1-1menta1`; bump with `dch -i`.
CI builds on every push to `master`; pushing a tag `menta/<version>` also publishes a release.
Needs the Menta libmate-desktop (>= 1.29.1-1menta2, mate-desktop PR #722) and, on
trixie, the Menta gtk-layer-shell backport; CI installs both from the rolling releases.

Patches: 0001 = upstream PR #452 (wlrandr WLRANDR_3: monitor id + primary monitor, not merged);
1001/1002 = Debian patches (RDA, rfkill debounce), still not merged upstream.
Configure uses `--enable-wayland=yes` (fails if Wayland libs are missing) and `--with-x`.
