# Do Python2 build
python3 configure.py &&
default_make &&

# Do Python2 build
if in_depends $MODULE Python; then
  python configure.py &&
  default_make
fi
