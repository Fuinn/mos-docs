.. _start:

***************
Getting Started
***************

Through parsing of an optimization model file, MOS develops a
representation (see :ref:`abstraction`) of
an optimization model, which
can then be accessed / modified / solved, by human or machine. To
get started with the cloud version of MOS:

^^^^^^^^^^^^^^^
Access MOS
^^^^^^^^^^^^^^^
&&&&&&&&&&&&&&&
Option 1: Locally host
&&&&&&&&&&&&&&&


* [Instructions to follow]

&&&&&&&&&&&&&&&
Option 2: Sign up to MOS cloud service and obtain a token
&&&&&&&&&&&&&&&


* [Cloud sign up instructions to follow]

  
^^^^^^^^^^^^^^^
Prepare or obtain an annotated model file
^^^^^^^^^^^^^^^

* Model examples ready to be uploaded to MOS are available at the `MOS Examples repository <https://github.com/Fuinn/mos-examples>`_
*  :ref:`process` outlines how to annotate your own model file for use
   with MOS. Supported modeling languages are currently `CVXPY <https://cvxpy.org>`_,    `JuMP <https://jump.dev>`_, `Pyomo <http://www.pyomo.org>`_, `GAMS <https://www.gams.com>`_, and `OPTMOD <https://github.com/ttinoco/OPTMOD>`_.
   
^^^^^^^^^^^^^^^
Upload, modify and solve your model(s)
^^^^^^^^^^^^^^^

* Models can be uploaded, modified, and solved through the `MOS
  Frontend <https://mos.fuinn.ie>`_, the MOS Interface `Python package
  <https://github.com/Fuinn/mos-interface-py>`_ or
  `Julia package <https://github.com/Fuinn/mos-interface-jl>`_, or via the :ref:`api` directly (see individual instructions for use of each)
* Note that model input data (``Input File`` or ``Input Object``) need to be explicitly defined (filepath or object value) through either the MOS Frontend or API. Currently, this explicit definition through MOS is required even when the data is defined in the annotated model file.

  
