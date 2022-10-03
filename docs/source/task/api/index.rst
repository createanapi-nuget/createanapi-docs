Task API
==========

/api/task/:id/process/start [POST]
""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
    :linenos:

    curl --location --request POST '//api/task/{{TASK_ID}}/process/start' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/task/:id/process/:processId/end [POST]
""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
    :linenos:
    
    curl --location --request POST '//api/task/{{TASK_ID}}/process/{{PROCESS_ID}}/end' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
    --data-raw '{
    "success": false,
    "exceptionMessage": "velit est",
    "exceptionStackTrace": "aliquip Excepteur pariatur",
    "innerExceptionMessage": "occaecat mollit aut",
    "innerExceptionStackTrace": "aliqua "
    }'

/api/task/:id/latestRun [GET]
""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
    :linenos:

    curl --location --request GET '//api/task/{{TASK_ID}}/latestRun' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/task/:id/run/:processId [GET]
""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
    :linenos:

    curl --location --request GET '//api/task/{{TASK_ID}}/run/{{PROCESS_ID}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/task/:id/trigger [POST]
""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
    :linenos:

    curl --location --request POST '//api/task/{{TASK_ID}}/trigger' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
    --data-raw '{
    "environmentVariables": [
        {
        "key": "magna id irure",
        "value": "amet in tempor"
        },
        {
        "key": "sit ex irure",
        "value": "exercitation ut"
        }
    ]
    }'