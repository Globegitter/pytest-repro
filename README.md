# pytest-repro

This reproduces how pytest follows symlinks and that this can cause issues in certain environments, for example when using [Bazel](https://bazel.build/).

One can reproduce in the following way:
```sh
pytest --version # This is pytest version 4.5.0, ...
pytest fakesandbox/my_test.py # fails because pytest dereferences the symlink and then tries to import the module from __init__.py
pytest app2/my_test.py # Succeeds because it has a copy of app/my_test.py
```