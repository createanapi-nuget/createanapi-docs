ShopWorks ODBC - Customer To CAA
===========================================

.. code-block:: json
  :linenos:

    "Config": {
        "TableName": "Cust",
        "PrimaryKey": "ID_Customer",
        "Threshold": 3,
        "RepositoryId": "62bdeb622c68cc8d86278680",
        "API": "protowels",
        "Initial":false,
        "Purge":false,
    }

### TableName
""""""""""""""""""""""""""""""""""""""""""

The name of the Customer Table in Customer ODBC, unlikely to change

### PrimaryKey
""""""""""""""""""""""""""""""""""""""""""

The name of the Primary Key of Customer Table in Customer ODBC, unlikely to change

### Threshold
""""""""""""""""""""""""""""""""""""""""""

Query limiter for not initial (first) runs. Will update products with last modified date within {threshold}

### RepositoryId
""""""""""""""""""""""""""""""""""""""""""

Customer Repository Id

### API
""""""""""""""""""""""""""""""""""""""""""

Customer's API name that has been setup in ODBC API

### Initial
""""""""""""""""""""""""""""""""""""""""""

Query for all products without removing

### Purge
""""""""""""""""""""""""""""""""""""""""""

Query for all products with removing
