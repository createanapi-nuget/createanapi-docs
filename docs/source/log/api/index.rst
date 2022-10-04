Log API
==========

/api/log [POST]
""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request POST '/api/log' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
    --data-raw '{
    "message": "id officia pariatur dolor",
    "logEventLevel": 1,
    "exceptionMessage": "i",
    "exceptionStackTrace": "nisi dolor in",
    "innerExceptionMessage": "sunt qui",
    "innerExceptionStackTrace": "deserunt nostrud",
    "processId": "dolore exercita",
    "taskId": "eiusmod dolore"
    }'

/api/log/batch [POST]
""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request POST '/api/log/batch' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
    --data-raw '{
    "items": [
        {
        "message": "ea in ex",
        "logEventLevel": 3,
        "exceptionMessage": "quis ad nulla",
        "exceptionStackTrace": "proident anim veniam irure",
        "innerExceptionMessage": "in velit in",
        "innerExceptionStackTrace": "est enim Excepteur culpa",
        "processId": "dolore",
        "taskId": "officia in"
        },
        {
        "message": "ullamco tempor Excepteur amet",
        "logEventLevel": 0,
        "exceptionMessage": "adipisicing ut ex",
        "exceptionStackTrace": "irure",
        "innerExceptionMessage": "et amet ea quis",
        "innerExceptionStackTrace": "tempor labore",
        "processId": "adipisicing do Lorem sed",
        "taskId": "elit ex fugiat Lorem"
        }
    ]
    }'