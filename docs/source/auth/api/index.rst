Identity Server
==================

CreateAnAPI.com resources are protected with Identity Server (https://identity.createanapi.com/).

Authorization
-------------

Authorization request contains account's ``client_id``, ``client_secret`` and a ``grant_type`` and returns an ``access_token`` which is valid for one hour. 
After the expiration, the access token should be renewed.

.. code-block::
   :linenos:
   :caption: Example Authorization Request

    curl --location --request POST 'https://identity.createanapi.com/connect/token' \
    --header 'Content-Type: application/x-www-form-urlencoded' \
    --data-urlencode 'client_id={{CLIENT_ID}}' \
    --data-urlencode 'client_secret={{CLIENT_SECRET}}' \
    --data-urlencode 'grant_type=client_credentials'

.. code-block:: json
   :caption: Example Authorization Response
   :linenos:

    {
        "access_token": "{{ACCESS_TOKEN}}",
        "expires_in": 3600,
        "token_type": "Bearer",
        "scope": "createanapi_full_access"
    }

Token Usage
-------------

The access token is passed to the resource api via ``Authorization`` Key with ``Bearer`` prefix in the headers.

.. code-block:: 
   :caption: Example Access Token Usage
   :linenos:
    
    curl --location --request GET 'https://apiv2.createanapi.com/api/repository/{{REPOSITORY_ID}}/data' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'