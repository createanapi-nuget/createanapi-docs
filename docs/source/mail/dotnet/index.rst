Mail .NET Client
================

This section of the documentation details the public API
usable to get details of projects, builds, versions and other details
from Read the Docs.


Post Mail
---------------

Posts a mail based on the given template.

.. code-block:: csharp
   :linenos:

    var postMail = await _createAnAPIClient.PostMail("", new MailItemRequest());
