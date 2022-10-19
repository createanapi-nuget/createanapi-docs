Mail .NET Client
================


Post Mail
---------------

Posts a mail based on the given template.


AfterHtml
""""""""""""

The html to render after the template content.

PreHtml
""""""""""""

The html to render before the template content.

Receivers
""""""""""""

List of mail receivers to be included on top of the template receivers.

Data
""""""""""""

The data to set dynamic strings. Every json key in a data will be available to use as a dynamic string in content and subject. 

.. code-block:: json
   :linenos:
   
   {
      "firstName": "Mehmet",
      "lastName": "Buber",
      "orderId": "order-1"
   }

Available dynamic strings for this data are ``{{firstName}}``, ``{{lastName}}`` and ``{{orderId}}``.

.. code-block:: csharp
   :linenos:

   var mailResponse = await _createAnAPIClient.PostMail(mailTemplateId, new Client.Models.Mail.MailItemRequest
   {
         FromEmail = "no-reply@createanapi.com",
         FromName = "CreateAnAPI.com",
         PreHtml = "<p>This will be rendered before the content</p>",
         AfterHtml = "<p>This will be rendered after the content</p>",
         Receivers = new List<string>()
         {
            "mehmetbuber@webservicespros.com"
         },
         Data = new
         {
            name = "Mehmet"
         }
   });
