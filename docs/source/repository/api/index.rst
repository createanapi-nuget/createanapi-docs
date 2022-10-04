Repository API
==============

Query Endpoints
---------------

/api/repository/:id/data [GET]
""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/data?skip=0&take=20&state={{STATE}}&filters={{FILTERS}}&sorts={{SORTS}}&include={{INCLUDE_FIELDS}}&exclude={{EXCLUDE_FIELDS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'


/api/repository/:id/data/:dataId [GET]
""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/data/{{DATA_ID}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/repository/:id/data/first [GET]
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/data/first?state={{STATE}}&filters={{FILTERS}}&sorts={{SORTS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/repository/:id/data/count [GET]
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/data/count?state={{STATE}}&filters={{FILTERS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'


.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/aggregate/{{FIELD_NAME}}/avg?aggregation={{AGGREGATION}}&state={{STATE}}&filters={{FILTERS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/repository/:id/:field/sum [GET]
""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/{{FIELD_NAME}}/sum?state={{STATE}}&filters={{FILTERS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/repository/:id/:field/min [GET]
""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/{{FIELD_NAME}}/min?state={{STATE}}&filters={{FILTERS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/repository/:id/:field/max [GET]
""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/{{FIELD_NAME}}/max?state={{STATE}}&filters={{FILTERS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/repository/:id/:field/avg [GET]
""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/{{FIELD_NAME}}/avg?state={{STATE}}&filters={{FILTERS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

Insert Endpoints
----------------

/api/repository/:id/data [POST]
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request POST '/api/repository/{{REPOSITORY_ID}}/data' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
    --data-raw '{
        "data": {},
        "state": 1,
        "logs":[
            {
                
            }
        ]
    }'

/api/repository/:id/data/batch [POST]
""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request POST '/api/repository/{{REPOSITORY_ID}}/data/batch' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
    --data-raw '{
        "items": [
            {
                "data": {},
                "state": 1,
                "logs":[
                    {

                    }
                ]
                },
                {
                "data": {},
                "state": 1,
                "logs":[
                    {
                        
                    }
                ]
            }
        ]
    }'
    
Update Endpoints
----------------

/api/repository/:id/data/:dataId [PUT]
""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request PUT '/api/repository/{{REPOSITORY_ID}}/data/{{DATA_ID}}' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
    --data-raw '{
        "id": "ipsum cillum",
        "data": {},
        "state": -60142556,
        "logs":[
            {
                
            }
        ]
    }'


/api/repository/:id/data/batch/changeState [POST]
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request POST '/api/repository/{{REPOSITORY_ID}}/data/batch/changeState' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
    --data-raw '{
    "oldState": 1,
    "newState": 2,
    "filters": [
        {
        "key": "{{KEY}}",
        "operation": "eq",
        "value": ""
        }
    ]
    }'

/api/repository/:id/data/batch [PUT]
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request PUT '/api/repository/{{REPOSITORY_ID}}/data/batch' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
    --data-raw '{
        "items": [
            {
                "id": "{{DATA_ID}}",
                "data": {},
                "state": 1,
                "logs":[
                    {
                        
                    }
                ]
                },
                {
                "id": "{{DATA_ID}}",
                "data": {},
                "state": 1,
                "logs":[
                    {
                        
                    }
                ]
            }
        ]
    }'


Delete Endpoints
----------------

/api/repository/:id/data/:dataId [DELETE]
""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request DELETE '/api/repository/{{REPOSITORY_ID}}/data/{{DATA_ID}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/repository/:id/data/batch/delete [POST]
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:
    
    curl --location -g --request POST '/api/repository/{{REPOSITORY_ID}}/data/batch/delete' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
    --data-raw '{
    "state": 1,
    "filters": [
        {
        "key": "{{KEY}}",
        "operation": "eq",
        "value": ""
        }
    ]
    }'

Aggregate Endpoints
-------------------

/api/repository/:id/aggregate/first [GET]
""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/aggregate/first?aggregation={{AGGREGATION}}&state={{STATE}}&filters={{FILTERS}}&sorts={{SORTS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/repository/:id/aggregate/count [GET]
""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/aggregate/count?aggregation={{AGGREGATION}}&state={{STATE}}&filters={{FILTERS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/repository/:id/aggregate [GET]
""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/aggregate?aggregation={{AGGREGATION}}&skip={{SKIP}}&take={{TAKE}}&includeCount={{INCLUDE_COUNT}}&state={{STATE}}&filters={{FILTERS}}&sorts={{SORTS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/repository/:id/aggregate/:field/sum [GET]
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/aggregate/{{FIELD_NAME}}/sum?aggregation={{AGGREGATION}}&state={{STATE}}&filters={{FILTERS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/repository/:id/aggregate/:field/min [GET]
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/aggregate/{{FIELD_NAME}}/min?aggregation={{AGGREGATION}}&state={{STATE}}&filters={{FILTERS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/repository/:id/aggregate/:field/max [GET]
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/aggregate/{{FIELD_NAME}}/max?aggregation={{AGGREGATION}}&state={{STATE}}&filters={{FILTERS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/repository/:id/aggregate/:field/avg [GET]
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location -g --request GET '/api/repository/{{REPOSITORY_ID}}/aggregate/{{FIELD_NAME}}/avg?aggregation={{AGGREGATION}}&state={{STATE}}&filters={{FILTERS}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'