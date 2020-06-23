===========================================
``pail`` -- Blob Storage System Abstraction
===========================================

Overview
--------

Pail is a high-level Go interface to blob storage containers like AWS's
S3 and similar services. Pail also provides implementation backed by
local file systems or MongoDB's GridFS for testing and different kinds
of applications.

Historically, ``pail`` is a component of `Evergreen
<https://github.com/evergreen-ci/>`_ , a CI platform: this fork removes some
legacy components and drops support older versions of Golang, thereby adding
support for modules, and may see additional development.

Documentation
-------------

The core API documentation is in the `godoc
<https://godoc.org/github.com/deciduosity/pail/>`_.

Development
-----------

Contribute
~~~~~~~~~~

Feel free to open issues or submit pull requests!

The pail package is available under the terms of the Apache License (v2).

Goals
~~~~~

- Higher order bucket implementations to provide more plug-and-play operations
  for common storage patterns (archiving, compression).

- Additional backend bucket implementations based to support blob storage
  systems using different APIs, including Azure and GCP.

- Alternate deduplicating "block store" storage formats.

- Add benchmarks and improve speed of common operations.
  
Buildsystem
~~~~~~~~~~~

The pail project uses a ``makefile`` to coordinate testing. Use the following
command to build the cedar binary: ::

  make build

The artifact is at ``build/pail``. The makefile provides the following
targets:

``test``
   Runs all tests, sequentially, for all packages.

``test-<package>``
   Runs all tests for a specific package

``race``, ``race-<package>``
   As with their ``test`` counterpart, these targets run tests with
   the race detector enabled.

``lint``, ``lint-<package>``
   Installs and runs the ``gometaliter`` with appropriate settings to
   lint the project.
