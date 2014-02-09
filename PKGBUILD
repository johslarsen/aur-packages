# Maintainer: Daniel Wallace <danielwallace at gtmanfred dot com>
# Contributor: Christer Edwards <christer.edwards@gmail.com>

pkgname=salt
pkgver=0.17.5
pkgrel=2
pkgdesc="A remote execution and communication system built on zeromq"
arch=(any)
url="https://github.com/saltstack/salt"
license=("APACHE")
optdepends=('apache-libcloud:: salt-cloud')
depends=('python2'
         'sshpass'
	 'libsodium'
	 'python2-ply'
	 'python2-cffi'
         'python2-yaml'
         'python2-jinja'
         'python2-pyzmq'
         'python2-crypto'
         'python2-psutil'
         'python2-msgpack'
         'python2-m2crypto'
         'python2-pycparser')

backup=('etc/salt/master'
        'etc/salt/minion')

conflicts=('salt-git')

source=("http://pypi.python.org/packages/source/s/${pkgname}/${pkgname}-${pkgver}.tar.gz"
        "salt-master.service"
        "salt-syndic.service"
        "salt-minion.service"
        "salt-master"
        "salt-syndic"
        "salt-minion")

md5sums=('1c9647b743c83b73572206e029f1a43f'
         '3a2b032ec37077363c049969105b128e'
         'e4c6adce5087e947c26c5c9d9fc3c9bb'
         '833d31ebee69f5c0e2c0b6c8d345b6d7'
         '33bb43fa74f67da7675c093664d43159'
         'b4adb3a08871646c345f0050e3d55fae'
         'ce64b6fb207142465bb5e2855e27cd8a')

package() {
  cd ${srcdir}/${pkgname}-${pkgver}

  python2 setup.py install --root=${pkgdir}/ --optimize=1

  install -Dm644 ${srcdir}/salt-master.service ${pkgdir}/usr/lib/systemd/system/salt-master.service
  install -Dm644 ${srcdir}/salt-syndic.service ${pkgdir}/usr/lib/systemd/system/salt-syndic.service
  install -Dm644 ${srcdir}/salt-minion.service ${pkgdir}/usr/lib/systemd/system/salt-minion.service

  mkdir -p ${pkgdir}/etc/salt/
  cp ${srcdir}/${pkgname}-${pkgver}/conf/master ${pkgdir}/etc/salt/
  cp ${srcdir}/${pkgname}-${pkgver}/conf/minion ${pkgdir}/etc/salt/
}
