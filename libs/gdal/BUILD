# Fixes error of installing etc stuff into /usr/etc
OPTS+=" --sysconfdir=/etc" &&

# Fix mandir
sedit "s|^mandir=.*|mandir='\${prefix}/share/man'|" configure &&

# and you need this
sed -i "8d" scripts/GNUmakefile &&
sed -i "s:\$(DESTDIR)\${prefix}::" scripts/GNUmakefile &&

export CFLAGS="$CFLAGS -fno-strict-aliasing"
export LDFLAGS="$LDFLAGS -Wl,--as-needed"

./autogen.sh &&

default_build
