Bucket API
==========

/api/bucket/:id/blob/:key [DEL]
""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request DELETE '/api/bucket/{{BUCKET_ID}}/blob/{{KEY}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/bucket/:id/blob/:key [GET]
""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request GET '/api/bucket/{{BUCKET_ID}}/blob/{{KEY}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'


/api/bucket/:id/blob/:key [POST]
""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request POST '/api/bucket/{{BUCKET_ID}}/blob/{{KEY}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/bucket/:id/blob/:key/exists [GET]
""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request GET '/api/bucket/{{BUCKET_ID}}/blob/{{KEY}}/exists' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/bucket/:id/blob/:key/metadata [GET]
""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request GET '/api/bucket/{{BUCKET_ID}}/blob/{{KEY}}/metadata' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/bucket/:id/blob/search [GET]
""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request GET '/api/bucket/{{BUCKET_ID}}/blob/search?query={{QUERY}}&continuationToken={{CONTINUATION_TOKEN}}' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'
