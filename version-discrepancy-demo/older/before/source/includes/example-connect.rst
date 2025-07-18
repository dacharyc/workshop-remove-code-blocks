Gather Connection Information
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The source cluster, ``cluster0``, is hosted on the following servers
and ports:

- clusterOne01.fancyCorp.com:20020
- clusterOne02.fancyCorp.com:20020
- clusterOne03.fancyCorp.com:20020

The destination cluster, ``cluster1``, is hosted on the following
servers and ports:

- clusterTwo01.fancyCorp.com:20020
- clusterTwo02.fancyCorp.com:20020
- clusterTwo03.fancyCorp.com:20020

There is an administrative user, ``clusterAdmin`` configured on each
cluster with password, ``superSecret``.

Connect the Source and Destination Clusters with ``mongosync``
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The generic connection string format is: 

.. code-block:: shell

   mongodb://<user>:<password>@<ip-address>:<port>,<ip-address>:<port>,<ip-address>:<port>

Use the connection information you gathered to create the connection
strings for ``cluster0`` and ``cluster1``:

.. code-block:: shell

   cluster0:
   mongodb://clusterAdmin:superSecret@clusterOne01.fancyCorp.com:20020,clusterOne02.fancyCorp.com:20020,clusterOne03.fancyCorp.com:20020
   cluster1:
   mongodb://clusterAdmin:superSecret@clusterTwo01.fancyCorp.com:20020,clusterTwo02.fancyCorp.com:20020,clusterTwo03.fancyCorp.com:20020

You can also use ``mongodb+srv`` connection strings with ``mongosync``.
You do not need to add the :urioption:`tls=true <tls>` option to a
``mongodb+srv`` connection string. For example:

.. code-block:: shell

   mongosync \
      --cluster0 "mongodb+srv://clusterAdmin:superSecret@clusterOne01.fancyCorp.com/" \
      --cluster1 "mongodb+srv://clusterAdmin:superSecret@clusterTwo01.fancyCorp.com/"

For more details about ``mongodb+srv`` connection strings, see
:ref:`connections-dns-seedlist`.
