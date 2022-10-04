ShopWorks ODBC - Inventory To CAA
===========================================

.. code-block:: json
  :linenos:

    "Config": {
        "TableName": "InvLevels",
        "PrimaryKey": "ID_InvLevel",
        "Threshold": 3,
        "RepositoryId": "62bdeb622c68cc8d86278680",
        "API": "protowels",
        "Initial":false,
        "Purge":false,
        "MinThresholdForMaintananceTime": 3,
        "MaxThresholdForMaintananceTime": 7
    }

TableName
""""""""""""""""""""""""""""""""""""""""""

The name of the Inventory Table in Customer ODBC, unlikely to change

PrimaryKey
""""""""""""""""""""""""""""""""""""""""""

The name of the Primary Key of Inventory Table in Customer ODBC, unlikely to change

Threshold
""""""""""""""""""""""""""""""""""""""""""

Query limiter for not initial (first) runs. Will update products with last modified date within {threshold}

RepositoryId
""""""""""""""""""""""""""""""""""""""""""

Inventory Repository Id

API
""""""""""""""""""""""""""""""""""""""""""

Customer's API name that has been setup in ODBC API

Initial
""""""""""""""""""""""""""""""""""""""""""

Query for all products without removing

Purge
""""""""""""""""""""""""""""""""""""""""""

Query for all products with removing

MinThresholdForMaintananceTime && MaxThresholdForMaintananceTime
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

Those fields are UTC hours for the tasks. If both fields are given in the configuration, Task will run but not connect to the ODBC database in that period of time.