Getting Started
===============

Installing
----------

It is available in PyPi, so you can install through pip:

.. code:: bash

    pip install sure
    pip3 install sure

Activating
----------

Sure is activated upon importing it, unless the environment variable
``SURE_DISABLE_NEW_SYNTAX`` is set to any non-falsy value. (You could
just use ``true``)

For test code cleaningness it's recommended to import sure only once in
the ``__init__.py`` of your root test package.

Here is an example:

.. code:: bash

    mymodule.py
    tests/
    tests/__init__.py  # this is our guy
    tests/unit/__init__.py
    tests/unit/test_mymodule_unit1.py
    tests/functional/__init__.py
    tests/functional/test_mymodule_functionality.py

That is unless, of course, you want to explicitly import the assertion
helpers from sure in every module.

Python version compatibility
============================

Sure is `continuously tested
against <https://travis-ci.org/gabrielfalcao/sure/>`__ python versions
2.7, 3.3, 3.4 and 3.5, but its assertion API is most likely to work anywhere.
The only real big difference of sure in cpython and even other
implementations such as `PyPy <http://pypy.org/>`__ is that the
`monkey-patching <how-it-works.md#monkey-patching>`__ only happens in
CPython.

You can always get around beautifully with ``expect``:

.. code:: python

    from sure import expect

    expect("this".replace("is", "at")).to.equal("that")

where in cpython you could do:

.. code:: python

    "this".replace("is", "at").should.equal("that")

Disabling the monkey patching
=============================

Just export the ``SURE_DISABLE_NEW_SYNTAX`` environment variable before
running your tests.

.. code:: console

    export SURE_DISABLE_NEW_SYNTAX=true
