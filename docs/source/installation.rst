Installation
============

Requirements
------------
* Matlab
* Optimization toolbox for Matlab

.. note::
    The following Matlab versions have been tested:
        * R2019b

Prepare yourself
----------------

Even if the Matlab interaction can be reduced to a minimum by using the GUI,
we recommend to do the first few pages of basically any Matlab tutorial on the web.
This will help to get used to the user interface of Matlab.

Setup
-----

1.  Get the code from the `github repository <https://github.com/henning1419/cyfi-nmr>`_.
2.  Put the files into a folder on your drive.
3.  Done :)


Start the Toolbox
-----------------

The program can be run completely by Matlab command line by executing

.. code-block::

    programfolder/main.m


However, it is recommended to use the graphical user interface (GUI)
as it has the full feature set and no commands have to be learned.
The GUI is started by

.. code-block::

    programfolder/mainGUI.m


In the beginning of the script in the ``Load data'' section uncomment or add just the load script you want to use
(e.g. the examples *load_dataset_single* or *load_dataset_multi*).
To run the script you can either right-click it and select **run** or select the script file and press **F9**.
The GUI will start after a few seconds.


