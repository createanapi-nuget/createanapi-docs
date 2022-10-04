Bucket API
==========

/api/bucket/:id/blob/:key [DEL]
""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request DELETE '//api/bucket/dolor Lorem/blob/dolor Lorem' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/bucket/:id/blob/:key [GET]
""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request GET '//api/bucket/dolor Lorem/blob/dolor Lorem' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'


/api/bucket/:id/blob/:key [POST]
""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request POST '//api/bucket/dolor Lorem/blob/dolor Lorem' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/bucket/:id/blob/:key/exists [GET]
""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request GET '//api/bucket/dolor Lorem/blob/dolor Lorem/exists' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/bucket/:id/blob/:key/metadata [GET]
""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request GET '//api/bucket/dolor Lorem/blob/dolor Lorem/metadata' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'

/api/bucket/:id/blob/search [GET]
""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request GET '//api/bucket/dolor Lorem/blob/search?query=dolor Lorem&continuationToken=dolor Lorem' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}'
