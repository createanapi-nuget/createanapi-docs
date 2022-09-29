Authentication .NET Client
==========================

The ``CreateAnAPI.Client`` nuget package has the necessary functions to get and refresh access token.


.. code-block:: json
   :linenos:
   :caption: Example .NET appconfig.json setup

    "CreateAnAPI": {
        "APIUrl": "https://apiv2.createanapi.com",
        "Authority": "https://identity.createanapi.com",
        "ClientId": "{{CLIENT_ID}}",
        "ClientSecret": "{{CLIENT_SECRET}}",
        "Scope": "createanapi_full_access"
    },

    
.. code-block:: csharp
   :linenos:
   :caption: Dependency injection of CreateAnAPI.Client

    services.AddSingleton(
        new CreateAnAPIClient(
            configuration["CreateAnAPI:APIUrl"],
            configuration["CreateAnAPI:Authority"],
            configuration["CreateAnAPI:ClientId"],
            configuration["CreateAnAPI:ClientSecret"],
            configuration["CreateAnAPI:Scope"]
        )
    );