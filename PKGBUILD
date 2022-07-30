# Build packages from local Git working tree
# Maintainer: Thomas Koch <linrunner@gmx.net>
# Contributor: Sven Karsten Greiner <sven@sammyshp.de>
# Contributor: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: Marc Schulte <bomba@nerdstube.de>

pkgbase=tlp-git
pkgname=(
  tlp-git
  tlp-rdw-git
)
pkgver=1.6.0_alpha.0
pkgrel=1
arch=(any)
url=https://linrunner.de/en/tlp/tlp.html
license=(GPL2)
makedepends=(git)
install=tlp.install

pkgver() {
  # ../ to leave src/
  sed -r 's/-/_/' ../VERSION
}

package_tlp-git() {
  pkgdesc='Linux Advanced Power Management'
  depends=(
    hdparm
    iw
    pciutils
    perl
    rfkill
    usbutils
    util-linux
  )
  optdepends=(
    'acpi_call: ThinkPad battery functions, Sandy Bridge and newer'
    'bash-completion: Bash completion'
    'ethtool: Disable Wake On Lan'
    'smartmontools: Display S.M.A.R.T. data in tlp-stat'
    'tp_smapi: ThinkPad battery functions'
  )
  provides=(tlp)
  conflicts=(
    laptop-mode-tools
    pm-utils
    power-profiles-daemon
    tlp
  )
  backup=(etc/tlp.conf)

  export TLP_NO_INIT=1
  export TLP_SBIN=/usr/bin
  export TLP_SDSL=/usr/lib/systemd/system-sleep
  export TLP_SYSD=/usr/lib/systemd/system
  export TLP_ULIB=/usr/lib/udev
  export TLP_WITH_ELOGIND=0
  export TLP_WITH_SYSTEMD=1

  # -C .. to leave src/ 
  make DESTDIR="${pkgdir}" -C .. install-tlp install-man-tlp
}

package_tlp-rdw-git() {
  pkgdesc='Linux Advanced Power Management - Radio Device Wizard'
  depends=(
    networkmanager
    tlp
  )
  provides=(tlp-rdw)
  conflicts=(tlp-rdw)

  # -C .. to leave src/ 
  make DESTDIR="${pkgdir}" -C .. install-rdw install-man-rdw
}

# vim: ts=2 sw=2 et:
