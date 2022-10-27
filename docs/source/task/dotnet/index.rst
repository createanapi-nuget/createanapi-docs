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




    
Create Task
"""""""""""""""""""""""""""""""""""""""""""

Creates a new task. If the task is based on a template, it can be runned instantly. If it is a custom task, GitHub actions should be triggered before run.

.. code-block:: csharp
    :linenos:

    var create = await _createAnAPIClient.CreateTask(new Client.Models.Task.ScheduledTask
    {
        Type = "template",
        Name = "Test",
        MailReceivers = new List<string>() { "mehmetbuber@gmail.com" },
        CPU = "256",
        Memory = "1024",
        StaticIp = true,
        TimeSpan = new ScheduleTimeSpan()
        {
            Day = 1,
            Hour = 1,
            Minute = 1
        },
        MaxTimeSpan = new ScheduleTimeSpan()
        {
            Day = 1,
            Hour = 1,
            Minute = 1
        },
        EnvironmentVariables = new List<EnvironmentVariable>()
        {
            new EnvironmentVariable()
            {
                Key = "Key",
                Value = "Value"
            }
        },
        Notes = "test",
        //Config = "{}",
        TemplateId = "62bbbfd82245c7441afa103f",
        ScheduleEnabled = true
    });


    
Get Task
"""""""""""""""""""""""""""""""""""""""""""

Returns the details of the task.

.. code-block:: csharp
    :linenos:

    var get = await _createAnAPIClient.GetTask(create.Data.Id);


    
Get Task List
"""""""""""""""""""""""""""""""""""""""""""

Returns a list of tasks

.. code-block:: csharp
    :linenos:

    var getList = await _createAnAPIClient.GetTaskList();


    
UpdateTask
"""""""""""""""""""""""""""""""""""""""""""

Updates a task.

.. code-block:: csharp
    :linenos:

    var update = await _createAnAPIClient.UpdateTask(create.Data.Id, new Client.Models.Task.ScheduledTask()
    {
        Type = "template",
        Name = "Test 2",
        MailReceivers = new List<string>() { "mehmetbuber@webservicespros.com" },
        CPU = "512",
        Memory = "2048",
        StaticIp = true,
        TimeSpan = new ScheduleTimeSpan()
        {
            Day = 2,
            Hour = 2,
            Minute = 2
        },
        MaxTimeSpan = new ScheduleTimeSpan()
        {
            Day = 2,
            Hour = 2,
            Minute = 2
        },
        EnvironmentVariables = new List<EnvironmentVariable>()
        {
            new EnvironmentVariable()
            {
                Key = "Key2",
                Value = "Value2"
            }
        },
        Notes = "test2",
        Config = "{}",
        TemplateId = "62bbbfd82245c7441afa103f",
        ScheduleEnabled = false
    });


    
Delete Task
"""""""""""""""""""""""""""""""""""""""""""

Deletes a task

.. code-block:: csharp
    :linenos:

    var delete = await _createAnAPIClient.DeleteTask(create.Data.Id);