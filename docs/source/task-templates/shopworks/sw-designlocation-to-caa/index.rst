ShopWorks ODBC - DesignLocation To CAA
===========================================

.. code-block:: json
  :linenos:

    "Config": {
        "TableName": "DesignLocations",
        "PrimaryKey": "ID_DesignLoc",
        "MaxField": "id_Design",
        "Threshold": 3,
        "RepositoryId": "62bdeb622c68cc8d86278699",
        "API": "seaside",
        "Initial":false,
        "Purge":false,
    }

TableName
""""""""""""""""""""""""""""""""""""""""""

The name of the DesignLocations Table in Customer ODBC, unlikely to change

PrimaryKey
""""""""""""""""""""""""""""""""""""""""""

The name of the Primary Key of DesignLocations Table in Customer ODBC, unlikely to change

Threshold
""""""""""""""""""""""""""""""""""""""""""

Query limiter for not initial (first) runs. Will update products with last modified date within {threshold}

RepositoryId
""""""""""""""""""""""""""""""""""""""""""

DesignLocations Repository Id

API
""""""""""""""""""""""""""""""""""""""""""

Customer's API name that has been setup in ODBC API

Initial
""""""""""""""""""""""""""""""""""""""""""

Query for all products without removing

Purge
""""""""""""""""""""""""""""""""""""""""""

Query for all products with removing
