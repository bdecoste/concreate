Building image
================

The main purpose of concreate is abstraction of building containers image from common source
using custom builder engines.

Concreate now support following builder engines:

* ``Docker`` -- build the image using docker build command and it default option
* ``OSBS`` -- build the image using `OSBS service <https://osbs.readthedocs.io>`_

Executing builds
-----------------

You can execute image build by running:

.. code:: bash

	  $ concreate build

**Builder options**

* ``--build-engine`` -- a builder engine to use ``osbs`` or ``docker``
* ``--build-tag`` -- an image tag used for build image (can be specified multiple times)
* ``--build-osbs-release`` -- perform a OSBS release build
* ``--build-tech-preview`` -- updates image descriptor ``name`` key to contain ``-tech-preview`` suffix in family part of the image name
  
  **Example**: If your ``name`` in image descriptor is: ``jboss-eap-7/eap7``, generated name will be: ``jboss-eap-7-tech-preview/eap7``.

Docker build
^^^^^^^^^^^^^^^^

This is the default way to build an container image. The image is build using ``docker build``.


OSBS build
^^^^^^^^^^^^^^^

This build is using ``rhpkg container-build`` to build the image using OSBS service. By default
it performs scratch build. If you need a release build you need to specify ``--build-osbs-release`` parameter.

**Example**

.. code:: bash

	  $ concreate build --build-engine=osbs
