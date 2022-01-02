GUI Interface
=============

Model tab
---------

**Active model**:
The model, which have been chosen in the process of data loading.
It is defined in the *load-file*.

**List of active constraints**:
A list of the currently active constraints. There are four types of constraints:

  **decrease** refers to a vector parameter :math:`v`. of the model, e.g. temperature dependent parameters.
  Forces :math:`v_1\geq v_2 \geq \ldots \geq v_n`.

  **increase** refers to a vector parameter $v$ of the model, e.g. temperature dependent parameters.
  Forces :math:`v_1\leq v_2 \leq \ldots \leq v_n`.

  **<=** refers to two scalar or vector parameters :math:`v` and :math:`w` of the same length.
  Forces component-wise :math:`v\leq w`.

  **>=** refers to two scalar or vector parameters :math:`v` and :math:`w` of the same length.
  Forces component-wise :math:`v\geq w`.

**Constraint info**:
Additional information for the constraint, that is selected in the list.

**Add**:
Add a new constraint. A dialog opens, which prompts the user to specify the constraint type,
the weight and the corresponding variable(s).
The algorithm uses *soft constraints*, which means they are considered in the underlying optimization,
but do not have to be fulfilled necessarily.
A higher weight will increase the impact of a constraint in the optimization.
The constraints decrease/increase refer to a single parameter and :math:`\geq`/:math:`\leq` refer to two parameters.

**Remove**:
Removes the currently selected constraint.



Analysis tab
------------
**Load Analysis** loads a saved analysis.
A loadable mat-file can be created by the save options *all2mat* or *rd2mat*.

**Control Optimization** contains the main controls used during optimization:

  **Optimize** runs the optimization with initial parameters in the init column of the parameter table.
  The optimized parameters are written to the opt column.

  Accept the parameters by pressing **Opt2Init** - the column opt is copied to the column init.
  The next optimization is based on the optimized parameters

  Decline the parameters by pressing **Init2Opt** - the column init is copied to the column opt.
  The next optimization is based again on the already used initial parameters.

**Undo** Undo an optimization or dependency check. 
If the initial state of the analysis is reached the undo button is marked with a *1*.

**Redo** Restore a (mistakenly) done undo.

**Algorithm settings** contains the useful control parameters of the optimization algorithm:

  **scheme** [series of integer numbers greater or equal to 1, divided by spaces]
  This can be roughly interpreted as step size of the underlying algorithm.
  The entry *1* refers to the base step size.
  For higher numbers the algorithm acts more sensitive and finds better solutions (but it is slower).
  The underlying algorithm runs as often as there are numbers in the series, e.g. *1 3 6 4 6* runs the algorithm
  on the step size levels 1 ➜ 3 ➜ 6 ➜ 4 ➜ 6.
  Thus we proceed from an estimate to a fine tuned solution.
  Values between 1 and 7 are recommended in a roughly increasing order.
  Matlab vector notations can also be used, e.g. *1:6* for *1 2 3 4 5 6*.

  **TolX** [positive double in the range 1E-4 to 1E-10] Termination criterion, based on the difference of the parameter vectors of subsequent iterations.

  **TolFun** [positive double in the range 1E-4 to 1E-10] Termination criterion, based on the difference of the objective function values of subsequent iterations.

  **Max. FunEval** Termination criterion, based on the maximal number of objective function evaluations.

  **Max. Iter** Termination criterion, based on the maximal number of algorithm iterations.
  \end{itemize**

**Activate para** Activation mode of parameters in the parameter table. Single will (de)active parameters one-by-one. 
All will (de)activate complete vector parameters.

**All/Single temp.** Plot the model evaluation vs. data for all temperatures (reduced info)
or for a single temperature (with submodel info).

**Decimal/Exponential**
Switch between formatting in parameter table

**Show Details**
Output various details on the data, model and parameters. Just try it after an optimization ;)

**all2mat** Saving everything. A folder is created in the results folder. 
It is named by the dataSet name and a time stamp. It contains the analysis object as a mat-file 
as well as the parameters and the model evaluation as a csv-file.

**rd2mat** Saving the analysis object as a mat-file.

**para2csv** Saving the parameters as a csv-file.

**model2csv** Saving the model evaluation as a csv-file.

Dependency check tab
--------------------

**Run Check** Start the dependency check with the current settings. 
This might take several minutes depending on the number of parameters and the computers CPU.
The algorithm is started for a number of *Max. Iter* iterations for each grid point for each component of the parameter vector.
Altering the corresponding settings can also reduce the computation time.

**Range ± in %**
Range for the evaluation of the likelihood profiles based on the current parameter values in the opt column of the parameter table.

**Grid length**
Number of grid points used in the selected range.

**Max. Iter**
Number of allowed algorithm iterations.

**Transfer selection to analysis**
The result plots are clickable.
Each point of the residual profiles can be selected.
The corresponding information is displayed under *Selected parameter* and *Value*.
Pushing *Set as new para* the underlying parameter vector is set as new initial parameter vector in the parameter table in the Analysis tab.


Optimization strategy tab
-------------------------

