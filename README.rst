.. image::  https://github.com/EtienneCmb/pathta/blob/master/docs/source/_static/PATHTA.svg

======
Pathta
======

Description
-----------

After a long hesitation between "Pathta" and "Tapath", I decided to call this incredibly complex toolbox "Pathta" given that I made a Postdoc surrounded by Italians. "Pathta" contains the world "Path" which is relatively natural since the goal of this incredibly complex toolbox is to manage path to files belonging to different research studies. Then there's the remaining "ta". I'm still not very sure what it means but someone suggested "to architecture". As a result, "Pathta" stands for "Path to architecture", which means nothing but sounds semi-professional. This incredibly complex toolbox can also be used to avoid setting paths between different systems (e.g. local computing and distant servers, collaborations between it-aliens etc.).

In case you asked, here's the logo :

Created by Etienne Combrithon, Ruggero Bathanithi

Installing Pathta
-----------------

To install Pathta, clone the repository, go inside it and run :

.. code-block:: python

    python setup.py develop

Then wait for 10 minutes for al dente. Don't use cream.

Usage
-----

Creation of a study
+++++++++++++++++++

Define a new study :

.. code-block:: python

    from pathta import Study

    # define the name of your study
    stname = "MyStudy"
    # define the root path where to save this study
    path = "/home/thteven/research"
    # create the study
    st = Study(stname)
    # add it
    st.add(path)

Managing files of this study
++++++++++++++++++++++++++++

Once your study is created, you can reload it :

.. code-block:: python

    from pathta import Study

    st = Study('MyStudy')

    # create a 'conn' folder
    path_to_conn = st.add_folder(folder='conn')

    # get the path to a folder and create it if it doesn't exist
    path_to_corr = st.path_to_folder(folder='corr', force=True)

    # join a file name to an existing folder
    path_to_file = st.join("my_file.xlsx", folder='excel', force=True)

    # search for files containing words "subject_1", "stats"
    is_files = st.search("subject_1", "stats", folder='conn')

Managing configuration files and python scripts
+++++++++++++++++++++++++++++++++++++++++++++++

Pathta lets you create configuration files :

.. code-block:: python

    from pathta import Study

    st = Study('MyStudy')

    # create a configuration file
    cfg = {'bad_channels': [0, 1, 2], "subject_name": "Thteven"}
    st.save_config("preprocessing.json", cfg)

    # reload a configuration
    cfg = st.load_config("preprocessing.json")

You can also load python scripts :

.. code-block:: python

    from pathta import Study

    st = Study('MyStudy')
    script = st.load_script("my_python_file.py")
    script.my_function(x=1)

Measures execution time
+++++++++++++++++++++++

Finally, you can measures the execution time of script relatively easily :

.. code-block:: python

    from pathta import Study

    st = Study('MyStudy')
    st.runtime()

    # do a lot a complicate stuffs
    x = 0
    x += 1
    x -= 1

    st.runtime()

The results are stored in path_to_MyStudy/cache/runtime.txt
