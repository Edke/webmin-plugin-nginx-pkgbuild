# Maintainer: Eduard Kracmar <edke.kraken[at]gmail[dot]com>
# Contributor: vbPadre <vbpadre at gmail dot com>

pkgname=webmin-virtualmin-nginx-plugin
pkgver=1.2
pkgrel=1
pkgdesc="Nginx plugin for webmin"
pluginname="virtualmin-nginx"
url="http://www.webmin.com/third.html"
license=('gpl')
arch=('i686' 'x86_64')
depends=('webmin')
install=webmin-${pluginname}-plugin.install
#source=(http://github.com/downloads/vixh/nginx-webmin/nginx0.0.2.wbm.gz)
source=(http://software.virtualmin.com/gpl/ubuntu/dists/virtualmin-universal/main/binary-amd64/webmin-virtualmin-nginx_1.2_all.deb)
md5sums=('7558433f3767003adef55f5eaf6ac7a0')

build() {
    msg "Preparing folders..."
    cd ${srcdir} || return 1
    mkdir -p ${pkgdir}/opt/webmin
    mkdir -p ${pkgdir}/etc/webmin/${pluginname}
    #cp -rf ${srcdir}/${pluginname}/ ${pkgdir}/opt/webmin
    msg "Extracting deb..."
    ar -xv webmin-virtualmin-nginx_${pkgver}_all.deb || return 1
    tar -xvf data.tar.gz || return 1
    msg "Moving plugin..."
    mv $srcdir/usr/share/webmin/virtualmin-nginx $pkgdir/opt/webmin

    msg "Creating config files..."
    touch ${pkgdir}/etc/webmin/${pluginname}/config
    touch ${pkgdir}/etc/webmin/${pluginname}/version
    echo "config_dir=/etc/nginx" >> ${pkgdir}/etc/webmin/${pluginname}/config
    echo "${pluginname}=${pluginname}" >> ${pkgdir}/etc/webmin/${pluginname}/config
}
