Mail .NET Client
================


Post Mail
---------------

Posts a mail based on the given template.

.. code-block:: csharp
   :linenos:

    var postMail = await _createAnAPIClient.PostMail("", new MailItemRequest());
