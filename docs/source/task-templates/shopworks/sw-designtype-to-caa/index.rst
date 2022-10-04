ShopWorks ODBC - DesignType To CAA
===========================================

.. code-block:: json
  :linenos:

    "Config": {
        "TableName": "DesignType",
        "PrimaryKey": "ID_DesignType",
        "Threshold": 3,
        "RepositoryId": "62bdeb622c68cc8d86278699",
        "API": "seaside",
        "Initial":false,
        "Purge":false,
    }

TableName
""""""""""""""""""""""""""""""""""""""""""

The name of the DesignType Table in Customer ODBC, unlikely to change

PrimaryKey
""""""""""""""""""""""""""""""""""""""""""

The name of the Primary Key of DesignType Table in Customer ODBC, unlikely to change

Threshold
""""""""""""""""""""""""""""""""""""""""""

Query limiter for not initial (first) runs. Will update products with last modified date within {threshold}

RepositoryId
""""""""""""""""""""""""""""""""""""""""""

DesignType Repository Id

API
""""""""""""""""""""""""""""""""""""""""""

Customer's API name that has been setup in ODBC API

Initial
""""""""""""""""""""""""""""""""""""""""""

Query for all DesignTypes without removing

Purge
""""""""""""""""""""""""""""""""""""""""""

Query for all DesignTypes with removing
