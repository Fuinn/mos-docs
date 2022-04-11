.. _abstraction:

***************
Abstraction
***************

That optimization models have a common structure is harnessed
to yield the abstraction that enables the MOS representation of a
model.

This structure is defined in terms of the **components** of each optimization model. These components are defined as follows:

* **Variable:** A model variable 
* **Constraint:** A model constraint
* **Function:** A function of model variables, for example the
  objective function of a problem, or part of a constraint
* **Problem:** Problem definition, bringing the model functions, variables, and constraints together
* **Solver:** Instructions on solving the model, for example, which optimization model solver to use (e.g. Cbc or Clp), and solver parameters (e.g. maximum number of iterations allowed)
* **Helper Object:** Numerical or text item, either hard-coded or calculated based on model inputs and/or model outputs  
* **Interface File:** A file containing model inputs / selected outputs
* **Interface Object:**  Numerical or text input/output to a model. Text input is required to be bracketed by ""






