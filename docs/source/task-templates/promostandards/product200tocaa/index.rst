PromoStandards Product 2.0.0 To CreateAnAPI
===========================================

The task pushes the given vendor's product data to a CreateAnAPI Repository. In the initial run, the task gets all products. 
After the initial run, it only gets and creates/updates products that are changed within the given threshold days.

https://github.com/createanapi-nuget/createanapi-promostandards/tree/develop/src/CreateAnApi.PromoStandards/CreateAnAPI.PromoStandards.Product200ToCAA

Config
--------------

.. code-block:: csharp
   :linenos:

    "Config": {
        "Vendors": [
            {
                "Name": "",
                "ProductData200": {
                    "Endpoint": "",
                    "Username": "",
                    "Password": "",
                    "RepositoryId": "",
                    "LocalizationLanguage": "",
                    "LocalizationCountry": "",
                    "Threshold": 0,
                    "Throttling": 0
                }
            }
        ]
    },

Vendors
"""""""""""""""""""""""""""""""""""""""

This field is an array, you can set up multiple vendors which the task will process one by one.

Vendor.Name
"""""""""""""""""""""""""""""""""""""""

Name of the vendor. It will be in the "vendor" field in product data.

Vendor.ProductData200.Endpoint
"""""""""""""""""""""""""""""""""""""""

Product Data 2.0.0 endpoint of the vendor.

Vendor.ProductData200.Username
"""""""""""""""""""""""""""""""""""""""

Product Data 2.0.0 username of the vendor endpoint.

Vendor.ProductData200.Password
"""""""""""""""""""""""""""""""""""""""

Product Data 2.0.0 password of the vendor endpoint.

Vendor.ProductData200.RepositoryId
"""""""""""""""""""""""""""""""""""""""

Id of the Product Data Repository.

Vendor.ProductData200.LocalizationLanguage
"""""""""""""""""""""""""""""""""""""""""""

Product Data 2.0.0 getProduct/localizationLanguage field.

Vendor.ProductData200.LocalizationCountry
"""""""""""""""""""""""""""""""""""""""""

Product Data 2.0.0 getProduct/localizationCountry field.

Vendor.ProductData200.Threshold 
"""""""""""""""""""""""""""""""""""""""

After the initial run, the task uses the threshold to calculate getProductDateModified/changeTimeStamp field and gets only changed products to update.

Vendor.ProductData200.Throttling
"""""""""""""""""""""""""""""""""""""""

Millisecond wait time between getProduct requests.

References
------------

https://staging.promostandards.org/product-data-2-0-0

Notes
-------

All vendor product tasks are set up as "Shared Provider" repositories unless the solution requires otherwise.