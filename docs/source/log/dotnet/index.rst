Log .NET Client
===============

This section of the documentation details the public API
usable to get details of projects, builds, versions and other details
from Read the Docs.


********
Config
********

.. code-block:: json
   :linenos:

    {
        "Log": {
            "MinimumLogLevel": "Debug",
            "Console": {
                "Enabled": false
            },
            "CreateAnAPI": {
                "Enabled": true,
                "FlushTimeSpan": 60,
                "QueueLimit": 10000,
                "BatchSizeLimit": 250
            },
            "File": {
                "Enabled": false,
                "Path": "log-.txt",
                "RollingInterval": "Day",
                "FlushTimeSpan": 60
            }
        }
    }

CreateAnAPI
---------------
CreateAnAPI logging enabled/disabled. Always enabled on AWS Init tasks.

Console
---------------
Console logging enabled/disabled. Always disabled on AWS Init tasks.

File
------------
File logging enabled/disabled. Always disabled on AWS Init tasks.

MinimumLogLevel
---------------
The minimum level of logs to be sent to the sink. Fatal > Error > Warning > Information > Debug > Verbose

**********
Log Levels
**********

Fatal
---------------

For errors that break all integration (E.g. Could not get the product data to be iterated)

.. code-block:: csharp
   :linenos:

    var initial = false;
    var first = await _createAnAPIClient.First<object>(_config.RepositoryId);
    if (first.IsSuccessful)
    {
        initial = first.Data?.Exists == false;
    }
    else
    {
        Log.Fatal(first.ErrorException, $"{nameof(Customer)} error, could not get the first response");
        throw first.ErrorException;
    }
    
Error
---------------

For errors that break single transaction (E.g. Could not get the exists response for a single product)


.. code-block:: csharp
   :linenos:

    var existing = await _createAnAPIClient.First<Inventory>(repositoryId, null, new List<DataFilter>
    {
        new()
        {
            Value = data.IDInvLevel.ToString(),
            Key = _config.PrimaryKey,
            Operation = StringOperation.Equals
        }
    });

    if (!existing.IsSuccessful)
    {
        Log.Error(existing.ErrorException, $"Could not get existing for: {data.IDInvLevel}");
        throw existing.ErrorException;
    }

    if (existing.Data == null)
    {
        Log.Error(existing.ErrorException, $"Could not serialize existing data for: {data.IDInvLevel}");
        throw existing.ErrorException;
    }

Warning
---------------

For mismatches for single transaction (E.g. Could not match the colors for a given product)

.. code-block:: csharp
   :linenos:

    Log.Warning($"Could not match po. {invoice.Data.invoiceNumber} {poFirst.StatusCode} {poFirst.Content}");
    
Information
---------------
For general health of the task (E.g. Task started, ended)

.. code-block:: csharp
   :linenos:

    Log.Information("Task started.");
    Log.Information("Task ended.");

Debug
---------------
For detailed debug info. Every action needs to be debug logged. (E.g. All successful attempts, SQL queries)

.. code-block:: csharp
   :linenos:

    Log.Debug($"{invoice.Data.invoiceNumber} - Product data processed successfully.");

    var query = $"SELECT * from {tableName} WHERE date_Modification > '{thresholdDateTime.ToString("MM/dd/yyyy")}'";
    Log.Debug(query);

Verbose
---------------

Unusually detailed output for diagnostic purposes (E.g. Detailed response or diagnostic data)

****************
Platform Logging
****************

.. code-block:: csharp
   :linenos:

    public class Program
    {
        public static void Main(string[] args)
        {
            CreateHostBuilder(args).Build().Run();
        }

        public static IHostBuilder CreateHostBuilder(string[] args)
        {
            return Host.CreateDefaultBuilder(args)
                .UseSerilog()
                .ConfigureWebHostDefaults(webBuilder => { webBuilder.UseStartup<Startup>(); });
        }
    }

.. code-block:: csharp
   :linenos:

    using CreateAnAPI.Logging.Platform;
    public class Startup
    {
        public void ConfigureServices(IServiceCollection services)
        {
            services.AddPlatformLogging(Configuration);
        }

        public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
        {
            app.UsePlatformLogging();
        }
    }

****************
Notes
****************
* Always try/catch for each transaction to be processed, so that if one of the items has an error, the integration continues.
* Never do a "continue" or "return" without logging.
* Always log the if and else sections of an if clauses
* Always log success as Debug
* Never suppress an error
* Always throw rest response errors
* Always use fatal for the errors that block the entire integration
* If the process has warning, error, or fatal logs, the mailing system will trigger even if the integration ends with success.
* Don't over-log or over-estimate the log levels for not to be desensitized to logs.
* If a decision is made to reduce the logs on an integration due to over-logging, note the decision on notes.
* Warning, Error, and Fatal logs are for Dev and PM before launch, for PM after launch.
* Information, Debug, and Verbose logs are for troubleshooting and giving a broader context to the next developer.