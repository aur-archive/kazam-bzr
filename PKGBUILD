    # Contributor: Florian Besser <fbesser AT gmail DOT com>
     
    _pkgname="kazam"
    pkgname="${_pkgname}-bzr"
    pkgver=467
    pkgrel=2
    pkgdesc="A screencasting program with design in mind"
    arch=('i686' 'x86_64')
    url="https://launchpad.net/kazam"
    license=('GPL')
    groups=()
    depends=('python-gobject' 'python-cairo'  'pygtk' 'ffmpeg' 'gstreamer' 'python-xdg' 'python-xlib' 'libmatroska' 'libtheora' 'libwnck3' 'python-dbus' 'gst-plugins-bad' 'gst-plugins-base' 'gst-plugins-good' 'gst-plugins-ugly' 'gst-libav')
    makedepends=('bzr' 'python-distutils-extra')
    conflicts=('kazam' 'kazam-stable-bzr')
    options=("!libtool")
    install="${_pkgname}.install"
 
    _bzrtrunk="lp:kazam"
    _bzrmod="unstable"
    
        
    pkgver() {
            cd "${srcdir}/${_bzrmod}"
            #printf "r%s" "$(bzr revno)"
	    echo $( bzr revno)
	    #bzr revno
    }
     
    build() {
            cd "${srcdir}"
            msg "Connecting to Bazaar server...."
     
            if [ -d $_bzrmod ] ; then
                    cd $_bzrmod && bzr merge
                    msg "The local files are updated."
            else
                    bzr branch ${_bzrtrunk}/${_bzrmod}
            fi
     
            msg "Bazaar checkout done or server timeout"
            msg "Starting make..."
     
            rm -rf "{$srcdir}/${_bzrmod}-build"
            cp -r "${srcdir}/${_bzrmod}" "${srcdir}/${_bzrmod}-build"
     
            cd "${srcdir}/${_bzrmod}-build"
            python setup.py build
    }
     
    package() {
            cd "${srcdir}/${_bzrmod}-build"
            python setup.py install --root="${pkgdir}"
    }

