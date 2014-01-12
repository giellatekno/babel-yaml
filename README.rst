===============================
Python Babel YAML Extractor
===============================

.. image:: https://badge.fury.io/py/babel_yaml.png
    :target: http://badge.fury.io/py/babel_yaml
    
.. image:: https://travis-ci.org/rtxanson/babel_yaml.png?branch=master
        :target: https://travis-ci.org/rtxanson/babel_yaml

.. image:: https://pypip.in/d/babel_yaml/badge.png
        :target: https://crate.io/packages/babel_yaml?version=latest


Provides an extractor for producing translation strings from a yaml file. Very
rough 'cause I needed itt in little time, so feel free to submit fixes and such.

* Free software: BSD license
* Documentation: http://babel_yaml.rtfd.org.

Features
--------

* Extracts strings from .yaml to .po files!


Not supported
-------------

* Extracting translator comments (TODO: this)

Usage
-----

Recommended to define a custom `yaml` constructor so that you can easily mark
strings you want to be extracted: ::

    def gettext_yaml_wrapper(loader, node):
        return node.value

    yaml.add_constructor('!gettext', gettext_yaml_wrapper)

Note that this isn't necessary for the actual extraction process, but it will
be necessary for whatever capacity you're using the YAML files in.

Then add stuff to your `babel.cfg`: ::

    [extractors]
    yaml = babel_yaml.yamlextractor:extract_yaml
    [yaml: **/tests/**.yaml]
    keywords = !gettext

Then you should be able to extract this stuff.
