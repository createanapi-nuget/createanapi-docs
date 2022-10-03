Task .NET Client
================


StartProcess
"""""""""""""""""""""""""""""""""""""""""""

Lets CreateAnAPI know a task started, it also needs to be marked as Ended after process. 

.. code-block:: csharp
    :linenos:

    var startResponse = await _createAnAPIClient.StartProcess(taskId);

EndProcess
"""""""""""""""""""""""""""""""""""""""""""

Lets CreateAnAPI know a task ended. Success key is required. If in case of errors, exception messages can be added to the request.

.. code-block:: csharp
    :linenos:

    var endResponse = await _createAnAPIClient.EndProcess(taskId, startResponse.Data.ProcessId, new EndProcessRequest()
    {
        Success = true,
        ExceptionMessage = "",
        ExceptionStackTrace = "",
        InnerExceptionMessage = "",
        InnerExceptionStackTrace = ""
    });


TriggerTask
"""""""""""""""""""""""""""""""""""""""""""

Starts an instance of another task. StartProcess and EndProcess requests are not required. The task will let CreateAnAPI know on itself.


.. code-block:: csharp
    :linenos:

    var triggerResponse = _createAnAPIClient.TriggerTask(taskId, new TriggerTaskRequest()
    {
        EnvironmentVariables = new List<EnvironmentVariable>()
        {
            new EnvironmentVariable()
            {
                Key = "Key",
                Value = "Value"
            }
        },
        Source = ""
    });

Trigger is also available via default Task Config for all ``AWS Initialized`` tasks.

.. code-block:: json
    :linenos:

    "Config": {
        "Trigger": {
            "OnSuccess": [
                {
                    "ScheduledTaskId": "{{NEXT_TASK_ID}}",
                    "EnvironmentVariables":[
                        {
                            "Key":"{{KEY}}",
                            "Value":"{{VALUE}}",
                        }
                    ]
                }
            ],
            "OnError": [
                {
                    "ScheduledTaskId": "{{NEXT_TASK_ID}}",
                    "EnvironmentVariables":[
                        {
                            "Key":"{{KEY}}",
                            "Value":"{{VALUE}}",
                        }
                    ]
                }
            ]
        }
    },


.. Hint:: By setting ``ASPNETCORE_ENVIRONMENT``, task instance's appconfig.json file can be overriden.


    

GetRun
"""""""""""

Returns a specific process details.

.. code-block:: csharp
    :linenos:

    var processResponse = await _createAnAPIClient.GetRun(taskId, processId);

GetLatestRun
"""""""""""""""""""""""""""""""""""""""""""

Returns the details of the last process of a task.

.. code-block:: csharp
    :linenos:

    var latestRunResponse = await _createAnAPIClient.GetLatestRun(taskId);