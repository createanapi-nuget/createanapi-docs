ODBC
==========

ODBC API Setup
--------------

C:\inetpub\wwwroot\createanapi-odbc\appsettings.Production.json

.. code-block:: json
   :linenos:

    {
        "ODBC": {
            "APIs": [
                {
                    "Id": "{{API_SHORTCODE}}",
                    "AccountId": "{{CAA_ACCOUNT_ID}}",
                    "DSN": "{{ODBC_DSN}}"
                }
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
            "ClientId": "{{CLIENT_ID}}",
            "ClientSecret": "{{CLIENT_SECRET}}",
            "Scope": "createanapi_full_access"
        }
    }