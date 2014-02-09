# Maintainer: Daniel Wallace <danielwallace at gtmanfred dot com>
# Contributor: Christer Edwards <christer.edwards@gmail.com>
pkgname=salt
pkgver=0.17.5
pkgrel=1
pkgdesc="A remote execution and communication system built on zeromq"
arch=('any')
url="https://github.com/saltstack/salt"
license=('APACHE')
depends=('python2'
         'python2-yaml'
         'python2-jinja'
         'python2-pyzmq'
         'python2-crypto'
         'python2-psutil'
         'python2-msgpack'
         'python2-m2crypto')

backup=('etc/salt/master'
        'etc/salt/minion')

source=('https://pypi.python.org/packages/source/s/${pkgname}/${pkgname}-${pkgver}.tar.gz')


package() {
  cd "${srcdir}/${_gitname}"
  
  python2 setup.py install --root=${pkgdir}/ --optimize=1

  install -Dm644 ${srcdir}/salt/pkg/arch/salt-master.service ${pkgdir}/usr/lib/systemd/system/salt-master.service
  install -Dm644 ${srcdir}/salt/pkg/arch/salt-syndic.service ${pkgdir}/usr/lib/systemd/system/salt-syndic.service
  install -Dm644 ${srcdir}/salt/pkg/arch/salt-minion.service ${pkgdir}/usr/lib/systemd/system/salt-minion.service

  mkdir -p ${pkgdir}/etc/salt/
  cp ${srcdir}/salt/conf/master ${pkgdir}/etc/salt/
  cp ${srcdir}/salt/conf/minion ${pkgdir}/etc/salt/

  # remove vcs leftovers
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
}
