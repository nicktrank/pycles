SURF Personal Notes
===================

Setting up PyCLES and SCAMPy
----------------------------

For compiling, use the command::

$ CC=mpicc-mpich-mp python setup.py build_ext --inplace

To designate an upstream branch for your current branch::

$ git remote add upstream https://github.com/ORIGINAL_USERNAME/PROJECT_NAME.git

To update current branch based on upstream branch::

$ git pull upstream master

To run a PyCLES simulation::

    python generate_parameters.py
    python generate_namelist.py Bomex (Edit Bomex.in to modify parameters)
    python main.py Bomex.in
    
To run a SCAMPy simulation::

    python generate_namelist.py Soares (Modify paramlist.in to modify separate parameters)
    python main.py Soares.in paramlist.in

Formatting this type of text:

.. code-block:: bash

    module load new
    module load open_mpi
    module load python/2.7.6
    module load netcdf
    module load hdf5/1.8.12

Enter inline ``text`` like this

Testing out a normal paragraph like this::

    So will this paragraph be markdown text?
    
Looking at Data Output of Simulations
-------------------------------------

To find the data files, navigate to ``pycles/Output.CASENAME.IDNUMBER/stats/``. Data is stored in binary files.
To look at header (lists the variables stored), use::

$ ncdump -h Stats.Bomex.nc

To look at more specific data for a variable, use ``-g`` to indicate the group name and ``-v`` to indicate the variable name. An example of this is::

$ ncdump -g timeseries -v cloud_fraction Stats.Bomex.nc
