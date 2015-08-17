# Contributor: Reiser <metal@pop3.ru>
# Maintainer: Luca Bennati <lucak3 AT gmail DOT com>

pkgname=partitionmanager-svn
pkgver=1358163
pkgrel=1
pkgdesc="A KDE 4 utility that allows you to manage disks, partitions, and file systems."
arch=('i686' 'x86_64')
url="https://sourceforge.net/projects/partitionman/"
license=('GPL2')
depends=('kdebase-runtime' 'parted')
makedepends=('cmake' 'automoc4' 'subversion')
optdepends=('e2fsprogs: ext2/3/4 support'
	    'xfsprogs: XFS support'
	    'jfsutils: JFS support'
	    'reiserfsprogs: Reiser support'
            'btrfs-progs: BTRFS support'
	    'ntfsprogs: NTFS support'
	    'dosfstools: FAT32 support')
install=partitionmanager.install
provides=(partitionmanager)
conflicts=(partitionmanager)
source=("svn://anonsvn.kde.org/home/kde/trunk/extragear/sysadmin/partitionmanager/")
md5sums=('SKIP')

_svnmod=partitionmanager

pkgver() {
  cd "$SRCDEST/$_svnmod"
  svnversion | tr -d [A-z]
}

build() {
  cd "$srcdir/$_svnmod"
  cmake -DCMAKE_INSTALL_PREFIX=/usr -DENABLE_UDISKS2=ON -DCMAKE_SKIP_RPATH=ON -DCMAKE_BUILD_TYPE=debugfull -DQT_QMAKE_EXECUTABLE=qmake-qt4 .
  make
}

package() {
  cd "$srcdir/$_svnmod"
  cd "$srcdir/$_svnmod"
  #make -C "$_svnmod-build" DESTDIR="${pkgdir}" install
  make DESTDIR="${pkgdir}" install
}
