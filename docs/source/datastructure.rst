Data Structure
==============

In this section we will explain the typical folder structure
and the *load files* used to define the correlations between data series.
Two examples are used that should cover most of the relevant cases.

Example 1 - Single data series
------------------------------

**Folder structure**

.. code-block::

        programfolder/
        ├─ ...
        └─ data/
           ├─ dataset_single/
           │  ├─ TNfile.dat
           │  ├─ pattern_270.dat
           │  ├─ pattern_280.dat
           │  └─ ...
           └─ load_dataset_single.m

**Load file**

.. code-block:: matlab
        :linenos:

        folder='data/dataset_single';                             % data folder
        namepatternData='pattern_';                               % naming pattern of data files
        nameN='data/dataset_single/TNfile.dat';                   % file containing spin densities
        name='data name';                                         % data name (optional)
        comment='data comment';                                   % comment (optional)
        data_1H=data(folder,namepatternData,nameN,name,comment);  % init data object
        data_1H.restrictT(0, 305)                                 % restrict data to given temperatures

        ds=dataSet('data set name','data set comment');           % init data set
        ds.addData(data_1H);                                      % append data to data set

        mo=ds1_2gl_dConst(ds,const);                              % init model

Example 2 - Multi data series (here 1H and 19F series)
------------------------------------------------------

**Folder structure**

.. code-block::

        programfolder/
        ├─ ...
        └─ data/
           ├─ dataset_multi/
           │  ├─ 1H
           │  │  ├─ TNfile.dat
           │  │  ├─ patternH_270.dat
           │  │  ├─ patternH_280.dat
           │  │  └─ ...
           │  └─ 19F
           │     ├─ TNfile.dat
           │     ├─ patternH_270.dat
           │     ├─ patternH_280.dat
           │     └─ ...
           └─ load_dataset_multi.m

**Load file**

.. code-block:: matlab
        :linenos:

        % 1H data
        folder='data/dataset_multi/1H';                           % data folder
        namepatternData='patternH_';                              % naming pattern of data files
        nameN='data/dataset_multi/1H/TNfileH.dat';                % file containing spin densities
        name='first data name';                                   % data name (optional)
        comment='second data comment';                            % comment (optional)
        data_1H=data(folder,namepatternData,nameN,name,comment);  % init data object
        data_1H.restrictT(0, 305);                                % restrict data to given temperatures

        % 19F data
        folder='data/dataset_multi/19F';                          % comments see above ...
        namepatternData='patternF_';
        nameN='data/dataset_multi/19F/TNfileF.dat';
        name='second data name';
        comment='second data comment';
        data_19F=data(folder,namepatternData,nameN,name,comment);
        data_19F.restrictT(0, 305);

        ds=dataSet('data set name','data set comment');           % init data set
        ds.addData(data_1H);                                      % append 1H data to data set
        ds.addData(data_19F);                                     % append 19F data to data set

        mo=ds2_3gl_dConst(ds,const);                              % init model





