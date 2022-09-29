Supplier Index
==============

Swagger
---------------
https://supplier-index.createanapi.com/swagger/index.html

Draw.io
---------------

https://drive.google.com/file/d/1INKXDxTvPrK-sSd5xPCoIdrvE-IQAnMH/view?usp=sharing

Client
---------------

Supplier Index API Config
-------------------------

.. code-block:: json
   :linenos:

    "Config": {
        "Clients": [
        {
            "Name": "Demo",
            "AccountId": "5e1f559d1ca17a343cc7c1fd",
            "Suppliers": [
            "sanmar",
            "alphabroder",
            "cutterandbuck",
            "sns"
            ]
        }
        ]
    }


C# Client
---------------

.. code-block:: csharp
   :linenos:

    using CreateAnAPI.SupplierIndex.Client;
    services.AddSupplierIndexClient(configuration);


Supplier Index Client Config
----------------------------

.. code-block:: json
   :linenos:

    "CreateAnAPI": {
        "SupplierIndexAPIUrl": "https://supplier-index.createanapi.com"
    }

Supplier Index Task
-------------------

.. code-block:: csharp
   :linenos:

    var skip = 0;
    var take = 20;
    var includeCount = false;
    int? state = null;
    var filters = new List<DataFilter>();
    var sorts = new List<DataSort>();


    var suppliers = await _supplierIndexClient.GetSuppliers();
                
    var parts = await _supplierIndexClient.GetParts(new GetPartsRequest
    {
        Supplier = null,
        ProductId = null,
        PartId = null,
        ProductName = null,
        Description = null,
        ProductBrand = null,
        ProductIsCloseOut = null,
        PrimaryMaterial = null,
        ProductCategory = null,
        ProductSubCategory = null,
        Color = null,
        Size = null,
        MinPrice = null,
        MaxPrice = null,
        MinQuantity = null,
        MaxQuantity = null,
    }, skip, take, includeCount);

    var partsAdvanced = await _supplierIndexClient.GetPartsAdvanced(skip, take, state, filters, sorts, includeCount);

    var products = await _supplierIndexClient.GetProducts(new GetProductsRequest
    {
        Supplier = null,
        ProductId = null,
        ProductName = null,
        Description = null,
        ProductBrand = null,
        IsCloseOut = null,
        Category = null,
        SubCategory = null,
        Color = null,
        Size = null,
        MaxLastChangeDate = null,
        MinLastChangeDate = null,
        MinPrice = null,
        MaxPrice = null,
        MinQuantity = null,
        MaxQuantity = null
    }, skip, take, includeCount);

    var productsAdvanced = await _supplierIndexClient.GetProductsAdvanced(skip, take, state, filters, sorts, includeCount);

    var supplier = "SanMar";
    var productId = "";

    var product = await _supplierIndexClient.GetProduct(supplier, productId);

    var inventory = await _supplierIndexClient.GetProductInventory(supplier, productId);

    var media = await _supplierIndexClient.GetProductMedia(supplier, productId);

    var pricing = await _supplierIndexClient.GetProductPricing(supplier, productId);


Portal
---------------

Supplier Index Startup.cs
-------------------------

.. code-block:: csharp
   :linenos:

    using CreateAnAPI.SupplierIndex.Client;
    services.AddMvc().AddPromoSupplierIndex(Configuration);

Portal Endpoints
----------------

.. code-block:: csharp
   :linenos:

    $"api/promo/supplier-index/suppliers"
    $"api/promo/supplier-index/parts"
    $"api/promo/supplier-index/advanced/parts"
    $"api/promo/supplier-index/products"
    $"api/promo/supplier-index/advanced/products"
    $"api/promo/supplier-index/supplier/{supplier}/products/{productId}"
    $"api/promo/supplier-index/supplier/{supplier}/products/{productId}/inventory"
    $"api/promo/supplier-index/supplier/{supplier}/products/{productId}/media"
    $"api/promo/supplier-index/supplier/{supplier}/products/{productId}/pricing"


Supplier
---------------

Related Template Tasks
----------------------

https://github.com/createanapi-clients/createanapi-dev-docs/wiki/PromoStandards-Inventory-2.0.0-To-CreateAnAPI

https://github.com/createanapi-clients/createanapi-dev-docs/wiki/PromoStandards-Media-1.0.0-To-CreateAnAPI

https://github.com/createanapi-clients/createanapi-dev-docs/wiki/PromoStandards-Media-1.1.0-To-CreateAnAPI

https://github.com/createanapi-clients/createanapi-dev-docs/wiki/PromoStandards-Part-2.0.0-To-CreateAnAPI

https://github.com/createanapi-clients/createanapi-dev-docs/wiki/PromoStandards-PPC-1.0.0-To-CreateAnAPI

https://github.com/createanapi-clients/createanapi-dev-docs/wiki/PromoStandards-Product-2.0.0-To-CreateAnAPI

Supplier Index API Config - New Supplier
----------------------------------------

.. code-block:: json
   :linenos:

    "Config": {
        "Suppliers": [
        {
            "ShortCode": "sanmar",
            "Name": "SanMar",
            "ProductDataRepositoryId": "62ec0e265f3d995ff233a6d6",
            "PartDataRepositoryId": "62ec0eb15f3d995ff233a6db",
            "InventoryRepositoryId": "62ec0e335f3d995ff233a6d7",
            "PPCRepositoryId": "62ec0e665f3d995ff233a6d9",
            "MediaRepositoryId": "62ec0e465f3d995ff233a6d8"
        }
        ]
    }
