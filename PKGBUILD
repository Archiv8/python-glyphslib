#!/bin/bash

# Created from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com> and Guillaume Horel <guillaume.horel@gmail.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/python-pyclipper/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/python-pyclipper/discussions>

_langname="python"
_relname="glyphsLib"
_pacmname="glyphslib"

pkgname="${_langname}-${_pacname}"
pkgver=6.0.4
pkgrel=1
pkgdesc="A bridge from Glyphs source files (.glyphs) to UFOs"
arch=(
  "any"
)
url="https://github.com/googlefonts/glyphsLib"
license=(
  "Apache"
)
depends=(
  "python"
  "python-fonttools"
  # For fonttools [ufo]
  "python-fs"
  "python-openstep-plist"
  "python-ufolib2"
  # For fonttools [unicode]
  "python-unicodedata2"
)
makedepends=(
  "python-defcon"
  "python-setuptools-scm"
)
_pycheckdeps=(

)
checkdepends=(
  # For fonttools [lxml]
  "python-lxml"
  "python-pytest"
  "python-ufo2ft"
  "python-ufonormalizer"
  "python-xmldiff"
)
optdepends=(
  "python-defcon"
  "python-ufonormalizer"
)
_zipname="$_relname-$pkgver"
source=(
  "https://files.pythonhosted.org/packages/source/${_relname::1}/${_relname}/${_zipname}.tar.gz"
)
sha512sums=(
  "835301da5b3c3a28ae946cad02e28f00ce504d82d1dacd42ea91a7193d472f5c5c5a94a71ffd417dccd797b5346a80369119446510f08fd76f85f522e4ef1ce8"
)
_setup="from setuptools import setup; setup();"

build() {

  cd "${_zipname}"

  python -c "${_setup}" build
}

# check() {

#  cd "$_zipname"

  # skipped tests require ufo2ft, a circular dependency which might be on older version than expected when this is built against Arch packages

  # [FixMe]: AssertionError: *.designspace file is different from expected
#  PYTHONPATH=Lib pytest tests \
#    --deselect tests/builder/builder_test.py
#}

package() {

  cd "${_zipname}"

  PYTHONPATH=Lib python -c "${_setup}" install --root="${pkgdir}" --optimize=1 --skip-build
}
