#if you're gonna change something in here make doggone sure you
#eyeball the init script too!

OPTS+=" --enable-ntp-signd \
        --disable-static   \
        --localstatedir=/var/cache" &&

OPTS+=" --libexecdir=/usr/lib" &&

CPPFLAGS+=" -fPIC" &&

default_build &&

if [ -e "/etc/init.d/ntp.sh" ]; then
  rm -f /etc/init.d/ntp.sh
fi &&

if [ -e "/etc/rc?.d/*ntp.sh" ]; then
  rm -f /etc/rc?.d/*ntp.sh
fi &&

gather_docs html &&

if [ ! -e /etc/ntp.conf ]; then
  install -m644 $SCRIPT_DIRECTORY/ntp.conf /etc
fi
