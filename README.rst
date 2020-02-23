amtSemVer
=========

|license| |python| |pypi| |build| |coverage|

----

*amtSemVer* is a Python 3 package that provides a very simplistic support
for the `Semantic Versioning`_ 2.0.

----

Basic Usage
-----------

Install with pip:

.. code:: bash

    pip install amtsemver

Import the ``SemanticVersion`` class in your python code

.. code:: python

    from amtSemVer import SemanticVersion

You can create a new version from its constituents:

.. code:: python

    # create a version with all the parameters 1.2.3-alpha+2345
    version_a = SemanticVersion(major=1, minor=2, patch=3, pre_release="alpha", build="2345")

    # create a simple version 2.0.0
    version_b = SemanticVersion(major=2, minor=0, patch=0)

Or by parsing a string:

.. code:: python

    # create an object from the string
    version_a = SemanticVersion.parse("1.2.3-alpha+2345")

    # this works too
    version_b = SemanticVersion.parse("1.2.3")
    # or (1.2.0)
    version_c = SemanticVersion.parse("1.2")
    # or (1.0.0)
    version_d = SemanticVersion.parse("1")
    # or even (1.0.0-alpha)
    version_e = SemanticVersion.parse("1+alpha")

``__str__`` representation of an object returns the following format
``major.minor.patch[-pre_release][+build]``

.. code:: python

    >>> a = SemanticVersion.parse("1.2.3-alpha+2345")
    >>> str(a)
    '1.2.3-alpha+2345'


``__repr__`` returns a string that can be evaluated back as an object.

.. code:: python

    >>> a = SemanticVersion.parse("1.2.3-alpha+2345")
    >>> b = repr(a)
    >>> b
    'SemanticVersion(major=1, minor=2, patch=3, pre_release="alpha", build="2345")'
    >>> c = eval(b)
    >>> c == a
    True

Object supports the rich comparison operators:

- Equal: a == b
- Not Equal: a != b
- Lesser:  a < b
- Lesser or Equal: a <= b
- Greater: a > b
- Greater or Equal: a >= b

.. code:: python

    >>> a = SemanticVersion.parse("1.2.0")
    >>> b = SemanticVersion.parse("1.2.0-alpha")
    >>> a > b
    True
    >>> a != b
    True
    >>> a <= b
    False


Tests
-----

Run tests:

.. code:: bash

    $ tox

License
-------

This package is released under the Apache License 2.0. See the bundled
`LICENSE`_ file for details.



.. _Semantic Versioning: https://semver.org/

.. _LICENSE: https://github.com/aimktech/amtSemVer/blob/master/LICENSE.txt

.. |python| image:: https://img.shields.io/static/v1?label=python&message=3%2e7%2b&color=blue&style=flat-square
    :target: https://www.python.org
    :alt: Python 3.7+

.. |pypi| image:: https://img.shields.io/pypi/v/amtsemver?color=blue&style=flat-square
    :target: https://pypi.org/project/amtsemver
    :alt: Latest version released on PyPI

.. |build| image:: https://img.shields.io/travis/aimktech/amtSemVer/master.svg?style=flat-square
    :target: https://travis-ci.org/aimktech/amtSemVer
    :alt: Travis build

.. |coverage| image:: https://img.shields.io/coveralls/github/aimktech/amtSemVer/master?style=flat-square
    :alt: Tests coverage

.. |license| image:: https://img.shields.io/badge/license-Apache--2.0-blue.svg?style=flat-square
    :target: https://raw.githubusercontent.com/aimktech/amtsemver/master/LICENSE.txt
    :alt: Package license
