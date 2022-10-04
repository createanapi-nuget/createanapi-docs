Mail API
==========

/api/mail/:id [POST]
""""""""""""""""""""""""""""""""""""""""""""

.. code-block::
   :linenos:

    curl --location --request POST '/api/mail/{{MAIL_ID}}' \
    --header 'Content-Type: application/json' \
    --header 'Authorization: Bearer {{ACCESS_TOKEN}}' \
    --data-raw '{
    "preHtml": "ex est ut ullamco",
    "data": {},
    "afterHtml": "ut",
    "receivers": [
        "officia Ut",
        "nostrud s"
    ]
    }'