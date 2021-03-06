export GOOS=linux
export GOROOT=$SOURCE_DIRECTORY
export GOBIN=$GOROOT/bin
export GOROOT_FINAL=/usr/lib/go
export GOPATH=$BUILD_DIRECTORY

if module_installed go; then
  export GOROOT_BOOTSTRAP=/usr/lib/go
else
  export GOROOT_BOOTSTRAP=/usr/lib/go1.4
fi &&

case "$(arch)" in
  x86_64) export GOARCH=amd64 ;;
  i686)   export GOARCH=386 ;;
esac &&

cd src &&
bash make.bash --no-clean &&

#cd $SOURCE_DIRECTORY &&

$GOROOT/bin/go get -d golang.org/x/tools/cmd/godoc &&
$GOROOT/bin/go build -o $SOURCE_DIRECTORY/godoc golang.org/x/tools/cmd/godoc &&
for i in vet cover; do
  $GOROOT/bin/go get -d golang.org/x/tools/cmd/${i} &&
  $GOROOT/bin/go build -o $GOROOT/pkg/tool/${GOOS}_${GOARCH}/${i} golang.org/x/tools/cmd/${i}
done &&

prepare_install &&

cd $SOURCE_DIRECTORY &&
install -Dm0755 godoc /usr/bin/godoc &&
mkdir -p /usr/{share/go,lib/go/src,lib/go/site/src} &&
cp -r doc misc /usr/share/go/ &&
ln -sf /usr/share/go/doc /usr/lib/go/doc &&
cp -a bin /usr/ &&
cp -a pkg /usr/lib/go/ &&
cp -a $GOROOT/src /usr/lib/go/ &&
cp -a $GOROOT/lib /usr/lib/go/ &&

install -Dm0644 src/Make.* /usr/lib/go/src/ &&

ln -sf /usr/bin /usr/lib/go/bin &&

# Remove object files from target src dir
find /usr/lib/go/src/ -type f -name '*.[ao]' -delete &&

# Remove all executable source files
find /usr/lib/go/src -type f -executable -delete &&

# For gox
install -Dm755 src/make.bash /usr/lib/go/src/make.bash &&
install -Dm755 src/run.bash /usr/lib/go/src/run.bash  &&
ln -sf /usr/share/go/misc /usr/lib/go/misc &&

# For godoc
install -Dm644 favicon.ico /usr/lib/go/favicon.ico &&
rm -f /usr/share/go/doc/articles/wiki/get.bin &&
install -Dm644 VERSION /usr/lib/go/VERSION &&

find /usr/lib/go/pkg -type f -exec touch '{}' +
