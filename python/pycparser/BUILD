prepare_install &&

# Do Python2 build
if in_depends $MODULE Python; then
  python ./setup.py build &&

  pushd pycparser &&
  python _build_tables.py &&
  popd &&

  python setup.py install --root=/ --optimize=1
fi &&

# Do Python3 build
python3 ./setup.py build &&

pushd pycparser &&
python3 _build_tables.py &&
popd &&

python3 setup.py install --root=/ --optimize=1

