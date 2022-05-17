.. _start:

***************
Getting Started
***************

Using the Service
=================

There are three ways to use MOS:

1. **MOS demo**: This is a simple way to run MOS locally on your machine to try the service. It runs all MOS components in `docker <https://www.docker.com/>`_ images using `docker-compose <https://www.docker.com/>`_. It uses development servers NOT suitable for any serious work requiring performance and security. It is just for demo purposes. Instructions for launching the demo can be found `here <https://github.com/Fuinn/mos-demo>`_. 

2. **MOS cloud**: Access and use MOS hosted on the cloud with performance and security features. (Coming soon).

3. **MOS on-premise**: Deploy MOS on a private network and servers by working directly with the :ref:`code repositories <resources_code>`.

For help or questions, `reach out to us <mailto:hello@fuinn.ie>`_.

Annotating Models
=================

Annotating a model code is necessary for informing MOS of the various model components that are imporant and need to be exposed on the model interface. Annotations have the general form below::

   #@ Tag: Name
   #@ Key1: Value1
   #@ Key2: Value2
   #@ ...

Supported tags are the following:

* *model*: Provides the name of the model.
* *input file*: Provides the name of an input files that can be provided to the model.
* *input object*:  Provides the name of an input (JSON-serializable) objet that can be provided to the model.
* *helper object*: Provides the name of a pre- or post-optimization (JSON-serializable) helper object.
* *variable*: Provides the name of an object representing an optimization variable (or collection of scalar variables).
* *function*: Provides the name of an object representing an optimization function (or collection of scalar-valued functions).
* *constraint*: Provides the name of an object representing an optimization constraint (or collection of constraints).
* *problem*: Provides the name of an object representing the optimization problem.
* *solver*: Provides the name of an object representing the optimization solver.
* *output file*: Provides the name of an output file that the model produces.
* *output object*: Provides the name of an output (JSON-serializable) object that the model produces.

Supported keys are the following:

* *description*: Provides a single-line description for the annotated object. Latex expressions enclosed in $$ pairs are supported.
* *labels*: Provides the name of an object with the same dimensions and structure of the annotated object that provides labels for each component.

For sample annotated models in various modeling systems, please check out our `examples <https://github.com/Fuinn/mos-examples>`_.

Deploying Models
================

(Try using sphinx-tabs, sphinx-code-tabs, sphinx-inline-tabs)

Interacting with Models
=======================

Monitoring Models
=================

Coming soon.

Saving and Loading Models
=========================

Coming Soon.