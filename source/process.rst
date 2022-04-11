.. _process:


---------------
Annotation
---------------

******************************
 Annotating a Model File
******************************


For MOS to recognize a structural component of a model in an optimization model
file, the component must be tagged by a keyword. The keyword is the
component type defined in the `abstraction
<abstraction.html>`_ section of the documentation, e.g.
::
   #@ Variable: x

`Interface Objects` and `Interface Files` are the only components that do not have perfect matching to a keyword. Instead, the respective keywords are ``Input Object`` / ``Output Object`` and ``Input File`` / ``Output File``.
   
An optional ``Description`` subtag, and associated description of the component, may follow, e.g.
::
   #@ Variable: x
   #@ Description: x=1 location selected, x=0 otherwise

Furthermore, there is also an optional ``Labels`` subtag. Labels
identify elements of multi-dimensional arrays. For example, a one
dimensional variable vector of length 3 could represent some property
of 3 cities. For example:
::
   #@ Variable: x
   #@ Description: x[i]=1 Location i selected, x[i]=0 otherwise
   #@ Labels: locations
   x = cp.Variable(3)
   locations = ['New York', 'Paris', 'London']
   

   
Note not every model component has to be tagged for a model to be
solved, however each component accessible via MOS does need to be
tagged.


Finally, an important note about model ``Input Objects`` and ``Input Files``. Even if they are assigned values in the model source file as in the example below, MOS will require an explicit assignment by human or machine through the various channels of interfacing with a model in MOS. For example, ``lambd`` here is assigned a value of 0.1 in the source file, but this value is not automatically inputted into MOS.
::
   #@ Input Object: lambd
   #@ Description: $$\lambda$$: regularization parameter
   lambd = .1

***************
Annotation Example
***************

The following is an extract from an annotated optimization model file describing a Lasso
regression problem formulated in CVXPY, `available in the MOS Examples repository <https://github.com/Fuinn/mos-examples/tree/main/examples/cvxpy/lasso>`_. Upon posting of this model file to MOS, the model is fully accessible and solvable through MOS.
::
   #@ Model: Lasso
   #@ Description: Machine Learning: Lasso Regression

   import cvxpy as cp
   import numpy as np
   import json

   np.random.seed(1)

   #@ Helper Object: m
   #@ Description: number of data points
   m = 100

   #@ Helper Object: n
   #@ Description: number of features
   n = 20

   #@ Helper Object: sigma
   #@ Description: $$\sigma$$ parameter for generating random dataset
   sigma = 5

   #@ Helper Object: density
   #@ Description: density parameter for generating random dataset
   density = 0.2

   #@ Helper Object: X
   #@ Description: data matrix X
   bs=np.random.randn(n)
   idxs = np.random.choice(range(n), int((1-density)*n), replace=False)
   X = np.random.randn(m,n)


   #@ Helper Object: Y
   #@ Description: observations Y
   beta_star = np.random.randn(n)
   idxs = np.random.choice(range(n), int((1-density)*n), replace=False)
   for idx in idxs:
       beta_star[idx] = 0
   Y = X.dot(beta_star) + np.random.normal(0, sigma, size=m)

   #@ Helper Object: X_train
   #@ Description: training data
   X_train = X[:50, :]

   #@ Helper Object: Y_train
   #@ Description: training observations
   Y_train = Y[:50]

   #@ Helper Object: X_test
   #@ Description: test data
   X_test = X[50:, :]
   
   #@ Helper Object: Y_test
   #@ Description: test observations
   Y_test = Y[50:]

   #@ Input Object: lambd
   #@ Description: $$\lambda$$: regularization parameter
   lambd = .1

   #@ Variable: beta
   #@ Description: $$\beta$$: regression coefficients
   beta = cp.Variable(n)

   #@ Function: loss_fn
   #@ Description: loss function $$\beta X_{train} - Y_{train}$$
   loss_fn = cp.norm2(X_train @ beta - Y_train)**2

   #@ Function: regularizer
   #@ Description: regularization component of objective function $$||\beta||$$
   regularizer = cp.norm1(beta)

   #@ Function: objectivefn
   #@ Description: objective function $$loss_{fn}+\lambda||\beta||$$
   objectivefn = loss_fn + lambd * regularizer

   #@ Problem: problem
   problem = cp.Problem(cp.Minimize(objectivefn))

   #@ Solver: solver
   solver = "ECOS"

   problem.solve(solver=solver, verbose=True)


***************
Model Languages
***************

Beyond the standard annotation of a model file, there are some model language specifics for integration of an optimization model with MOS.


^^^^^^^^^^^^^^^^^^^
 CVXPY
^^^^^^^^^^^^^^^^^^^

There is a necessity to have an ``import json`` statement in the model file.


^^^^^^^^^^^^^^^^^^^
 Julia / JuMP
^^^^^^^^^^^^^^^^^^^

No specific restrictions.

^^^^^^^^^^^^^^^^^^^
 OPTMOD
^^^^^^^^^^^^^^^^^^^

No specific restrictions.

^^^^^^^^^^^^^^^^^^^
 Pyomo
^^^^^^^^^^^^^^^^^^^

There is also a necessity to have an ``import json`` statement in the model file.
Pyomo is a recent addition, and the integration of its features with MOS is less advanced.

^^^^^^^^^^^^^^^^^^^
 GAMS
^^^^^^^^^^^^^^^^^^^
* GAMS is currently not available on the MOS cloud service, but can be used with a local deployment of MOS.
  
* Input objects are restricted to being scalars, with Scalar capitalized in the GAMS definition.

* At present, the MOS function structure does not work with GAMS. Thus, it is required to be define a variable to maximized/minimized, and with a constraint setting that variable equal to the objective function.

* A parameter named 'solver' is required, with some GAMS solver outputs populated as per examples.

