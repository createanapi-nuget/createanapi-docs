ShopWorks ODBC - Customer Discount Level To CAA
===============================================

.. code-block:: json
  :linenos:

    "Config": {
        "TableName": "CustomerDiscountLevels",
        "PrimaryKey": "ID_DiscountLevel",
        "Threshold": 3,
        "RepositoryId": "62bdeb622c68cc8d86278699",
        "API": "seaside",
        "Initial":false,
        "Purge":false,
    }

TableName
""""""""""""""""""""""""""""""""""""""""""

The name of the Customer Discount Level Table in Customer ODBC, unlikely to change

PrimaryKey
""""""""""""""""""""""""""""""""""""""""""

The name of the Primary Key of Customer Discount Level Table in Customer ODBC, unlikely to change

Threshold
""""""""""""""""""""""""""""""""""""""""""

Query limiter for not initial (first) runs. Will update products with last modified date within {threshold}

RepositoryId
""""""""""""""""""""""""""""""""""""""""""

Customer Discount Level Repository Id

API
""""""""""""""""""""""""""""""""""""""""""

Customer's API name that has been setup in ODBC API

Initial
""""""""""""""""""""""""""""""""""""""""""

Query for all Customer Discount Level without removing

Purge
""""""""""""""""""""""""""""""""""""""""""

Query for all Customer Discount Level with removing
