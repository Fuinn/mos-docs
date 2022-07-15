.. _overview:

********
Overview
********

What is MOS?
============

MOS is a software application designed to facilitate the deployment, integration, management, and analysis of mathematical optimization models. 
Some of the key benefits provided are the following:

* Models can be easily uploaded to the application after adding simple annotations to the model code.
* Models can be accessed via various available interfaces, including a REST API, a web graphical user interface, and client libraries in popular programming languages such as Python and Julia. 
* Models can be run with different inputs by workers running locally or distributed over the network. 
* Intermediate and end results can be extracted, browsed, and analyzed. 
* Model performance and usage can be monitored and visualized. (Coming soon)
* Model run snapshots can be saved for future analysis. (Coming soon)

This is all available without the need for custom ad-hoc code!

Service Architecture
====================

MOS consists of various components:

* Backend: Manages model data and access, and provides a REST API for interacting with models.
* Frontend: Provides a web graphical user interface for accessing and using models.
* Compute workers: Run models locally or distributed over the network using modeling-system-specific computational kernels.
* Interface libraries: Allow users or other applications to interact with models using popular programming languages.

The architecture is shown on the diagram below.

.. image:: ../static/architecture.*
    :scale: 80%
    :align: center

Model Representation
====================

MOS views and represents optimization models as being more general than a collection of variables, functions, and constraints. MOS views them as also having inputs, outputs, and intermediate objects in between. The intermediate or "helper objects" correspond to objects that are created either in a pre-optimization phase, for facilitating the construction of model variables, functions and constraints, or in a post-optimization phase, for facilitating the construction of outputs. This more generalized representation is helpful for interacting and analyzing models using a variety of tools. 

A diagram of the model representation used by MOS is shown below.

.. image:: ../static/model_representation.*
    :scale: 70%
    :align: center

Modeling Systems
================

MOS allows deploying models written using various mathematical optimization modeling systems. 
The systems fully or partially supported currently are the following:

* `CVXPY <https://www.cvxpy.org/>`__
* `JuMP <https://jump.dev/JuMP.jl/stable/>`_
* `GAMS <https://www.gams.com/>`_ (subject to license)
* `Pyomo <http://www.pyomo.org/>`_ (currently limited to AbstractModels)
* `OPTMOD <https://github.com/ttinoco/OPTMOD>`_ 
  
Compute workers are responsible for processessing requests to execute models deployed via MOS. The model execution part itself is done by a *computational kernel* chosen by the worker. There is one computational kernel for each modeling system that understands the specific details about such modeling system, including the data types used for defining variables, functions, and constraints.

Model Execution Environments
============================

Currently, the compute workers run models using the same executing environment for all models. That is, the same Python and Julia versions, and the same dependencies. An enhancement for this is planned, in which each model can specify the custom envirionment on which it is run. Stay tuned.
