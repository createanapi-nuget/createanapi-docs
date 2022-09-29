ODBC
==========

This section of the documentation details the public API
usable to get details of projects, builds, versions and other details
from Read the Docs.

ODBC API Setup
--------------

C:\inetpub\wwwroot\createanapi-odbc\appsettings.Production.json

.. code-block:: json
   :linenos:

    {
    "ODBC": {
        "APIs": [
        {
            "Id": "level10",
            "AccountId": "5e1f559d1ca17a343cc7c1fd",
            "DSN": "DSN=level10;uid=extro;pwd=extro;"
        },
        {
            "Id": "moxie",
            "AccountId": "5e1f559d1ca17a343cc7c1fd",
            "DSN": "DSN=Moxie;uid=extro;pwd=extro;"
        },
        {
            "Id": "nationalink",
            "AccountId": "5e1f559d1ca17a343cc7c1fd",
            "DSN": "DSN=NationalInk;uid=extro;pwd=extro;"
        },
        {
            "Id": "protowels",
            "AccountId": "5e1f559d1ca17a343cc7c1fd",
            "DSN": "DSN=ProTowels;uid=extro;pwd=extro;"
        },
        {
            "Id": "seacost",
            "AccountId": "5e1f559d1ca17a343cc7c1fd",
            "DSN": "DSN=SeaCost;uid=extro;pwd=extro;"
        },
        {
            "Id": "seaside",
            "AccountId": "5e1f559d1ca17a343cc7c1fd",
            "DSN": "DSN=SeaSideSilkScreening;uid=extro;pwd=extro;"
        },
        {
            "Id": "wolfmark",
            "AccountId": "5e1f559d1ca17a343cc7c1fd",
            "DSN": "DSN=Wolfmark;uid=extro;pwd=extro;"
        },
        ] 
    }
    }


Client Usage
--------------

.. code-block:: csharp
   :linenos:

    public class AllTask : ScheduledTaskService
    {
        private readonly TaskConfig _config;
        private readonly CreateAnAPIODBCClient _createAnAPIODBCClient;

        public AllTask(IOptions<TaskConfig> config, CreateAnAPIClient createAnAPIClient, CreateAnAPIODBCClient createAnAPIODBCClient) : base(createAnAPIClient)
        {
            _createAnAPIODBCClient = createAnAPIODBCClient;
            _config = config.Value;
        }

        public override async Task Process()
        {
            var result1 = await _createAnAPIODBCClient.Query<object>("level10", "SELECT * FROM Cust where sts_Active = 1");
        }


        public override ScheduledTaskConfig GetConfig()
        {
            return _config;
        }
    }

Client appconfig.json
---------------------

.. code-block:: json
   :linenos:
   
    {
        "CreateAnAPI": {
            "APIUrl": "https://apiv2.createanapi.com",
            "ODBCAPIUrl": "http://52.15.35.208:5000",
            "Authority": "https://identity.createanapi.com",
            "ClientId": "api-client",
            "ClientSecret": "SuperSecretPassword",
            "Scope": "createanapi_full_access"
        }
    }