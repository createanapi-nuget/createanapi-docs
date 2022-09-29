Platform .NET Client
====================

This section of the documentation details the public API
usable to get details of projects, builds, versions and other details
from Read the Docs.

Get Platform
---------------

Returns the platform configuration.

.. code-block:: csharp
   :linenos:

    var getPlatform = await _createAnAPIClient.GetPlatform("61f2b0df0c1de4b87ab802ef");


Update Platform
---------------

Updates the platform configuration.

.. code-block:: csharp
   :linenos:
    
    var updatePlatform = await _createAnAPIClient.UpdatePlatform("61f2b0df0c1de4b87ab802ef", "promoPurchaseOrder", new
    {
        success = true
    });


Get Platform User
-----------------

Updates the platform user.

.. code-block:: csharp
   :linenos:
   
    var getPlatformUser = await _createAnAPIClient.GetProfile("61f2b0df0c1de4b87ab802ef", "mehmetbuber@gmail.com");


Create Platform User
---------------------

Creates the platform user.

.. code-block:: csharp
   :linenos:

    var createProfile = await _createAnAPIClient.CreateProfile("61f2b0df0c1de4b87ab802ef", new PlatformUserDTO());


Update Platform User
---------------------

Updates the platform user.

.. code-block:: csharp
   :linenos:

    var updateProfile = await _createAnAPIClient.UpdateProfile("61f2b0df0c1de4b87ab802ef", "mehmetbuber@gmail.com", new PlatformUserDTO());
