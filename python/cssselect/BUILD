# Python-3 build
python3 ./setup.py build &&

prepare_install &&

python3 setup.py install --root=/

# Python2 build
if in_depends $MODULE Python; then
  python ./setup.py build &&
  python setup.py install --root=/
fi
