python3 setup.py config &&

prepare_install &&

python3 setup.py install --install-scripts=zope --root=/ &&

if module_installed Python; then
  python setup.py config &&
  python setup.py install --install-scripts=zope --root=/
fi
