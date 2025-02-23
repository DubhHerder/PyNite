=================
Load Combinations
=================

In Pynite, loads are categorized into load cases. Any time you add a load to the model a load case
is assigned to that load. If you do not specify a load case, Pynite automatically assigns "Case 1"
to the load.

A load combination is used to combine multiple load cases, each with a load factor, into one
combination. This is a common practice in structural engineering. If no load combinations are
specified by the user, Pynite will create a load combination named "Combo 1" that applies a load
factor of 1 to all loads in "Case 1".

Load combinations can be created using the ``FEModel3D.add_load_combo()`` method. This method takes
in two arguments: a name for the load combo, and a dictionary listing each load case to be used in
the combination with its associated load factor. For example, in US codes one load combination that
must be checked is dead loads factored by 1.2 acting simultaneously with live loads factored by
1.6. Here's how this could be accomplished:

.. code-block:: python

    # Assume 'D' and 'L' are names previously specified for load cases
    my_model.add_load_combo('Vertical Loads', {'D':1.2, 'L':1.6})

Load combinations can also be passed a 3rd optional argument named ``combo_type``. This has no effect on
the analysis, but it can be used to categorize load combinations (e.g. 'strength' or 'service') for
easier filtering of results later on.