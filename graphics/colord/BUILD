add_priv_group colord &&
add_priv_user colord -d /var/run/colord -g colord &&

OPTS+=" --sysconfdir=/etc/$MODULE \
        --with-daemon-user=colord \
        --disable-systemd-login   \
        --disable-argyllcms-sensor" &&

OPTS+=" --libexecdir=/usr/lib/$MDULE" &&

default_build
