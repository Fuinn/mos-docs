.. _api:


***************
REST API
***************

^^^^^^^^^^^^^^^
Introduction
^^^^^^^^^^^^^^^

This page outlines how to access the MOS REST API directly. The API specification is displayed below, some guiding points are as follows:

* Information is supplied to, or received from, a request in JSON form.

* Commands relating to the creation, deletion, running of models have urls commencing with the form ``/api/model/``.

* Commands relating to particular model components (for example a
  variable), have urls with the form ``/api/component/``
  (e.g. ``/api/variable/``).

*  Inputs and outputs to/from a model are controlled through commands
   around ``interface objects`` and ``interface files``, whereas direct information on the solution may be extracted from associated commands around such components as ``variable``, ``constraint``, ``problem``, and ``solver``.

  
^^^^^^^^^^^^^^^
Authentication
^^^^^^^^^^^^^^^

Requests to the REST API require an ``Authorization`` header with content ``Token`` followed by the string comprising the token. The token may be obtained as outlined in the :ref:`start` section. For example, for a token ``abcdefg``, the header will take the following form:
::
   Authorization: Token abcdefg

  
^^^^^^^^^^^^^^^
Specification
^^^^^^^^^^^^^^^

.. openapi:: openapi-shallowmodel.yml
  :examples:
