Auth Repository .NET Client
=============================

CreateAnAPI.Client nuget package contains functions for all available CreateAnAPI Core Auth Repository API endpoints.

Auth Repository Functions
--------------------------------


AuthRepositoryCreate
"""""""""""""""""""""""""""""""""""""""""""

Returns an item by id.

.. code-block:: csharp
   :linenos:

    var repoCreateResponse = await _createAnAPIClient.AuthRepositoryCreate(new AuthRepository()
    {
        Name = "Test",
        Domains = new List<string>()
        {
            "localhost:5001"
        }
    });

AuthRepositoryUpdate
"""""""""""""""""""""""""""""""""""""""""""

Returns an item by id.

.. code-block:: csharp
   :linenos:

    var repoUpdateResponse = await _createAnAPIClient.AuthRepositoryUpdate(repoCreateResponse.Data.Id, new AuthRepository()
    {
        Name = "Test 2"
    });

AuthRepositoryGet
"""""""""""""""""""""""""""""""""""""""""""

Returns an item by id.

.. code-block:: csharp
   :linenos:

    var repoGetResponse = await _createAnAPIClient.AuthRepositoryGet(repoCreateResponse.Data.Id);

AuthRepositoryGetList
"""""""""""""""""""""""""""""""""""""""""""

Returns an item by id.

.. code-block:: csharp
   :linenos:

    var repoGetListResponse = await _createAnAPIClient.AuthRepositoryGetList();

AuthRepositoryDelete
"""""""""""""""""""""""""""""""""""""""""""

Returns an item by id.

.. code-block:: csharp
   :linenos:

    var repoDeleteResponse = await _createAnAPIClient.AuthRepositoryDelete(repoCreateResponse.Data.Id);

Auth Repository User Functions
--------------------------------

AuthRepositoryUserRegister
"""""""""""""""""""""""""""""""""""""""""""

Returns an item by id.

.. code-block:: csharp
   :linenos:


    var userRegisterResponse = await _createAnAPIClient.AuthRepositoryUserRegister(repoCreateResponse.Data.Id, new AuthRepositoryUserRegisterRequest()
    {
        Username = "username",
        Password = "password",
        Config = new
        {
            success = true
        }
    });

AuthRepositoryUserGet
"""""""""""""""""""""""""""""""""""""""""""

Returns an item by id.

.. code-block:: csharp
   :linenos:

    var userGetResponse = await _createAnAPIClient.AuthRepositoryUserGet(repoCreateResponse.Data.Id, "username");

AuthRepositoryUserGetList
"""""""""""""""""""""""""""""""""""""""""""

Returns an item by id.

.. code-block:: csharp
   :linenos:

    var userGetListResponse = await _createAnAPIClient.AuthRepositoryUserGetList(repoCreateResponse.Data.Id);

AuthRepositoryUserLogin
"""""""""""""""""""""""""""""""""""""""""""

Returns an item by id.

.. code-block:: csharp
   :linenos:

    var userLoginResponse = await _createAnAPIClient.AuthRepositoryUserLogin(repoCreateResponse.Data.Id, "username","password");

AuthRepositoryUserUpdate
"""""""""""""""""""""""""""""""""""""""""""

Returns an item by id.

.. code-block:: csharp
   :linenos:

    var userUpdateResponse = await _createAnAPIClient.AuthRepositoryUserUpdate(repoCreateResponse.Data.Id, "username", new AuthRepositoryUserUpdateRequest()
    {
        Password = "password",
        Config = new
        {
            success=false,
            success2=true
        },
        Username = "username",
    });

AuthRepositoryUserDelete
"""""""""""""""""""""""""""""""""""""""""""

Returns an item by id.

.. code-block:: csharp
   :linenos:

    var userDeleteResponse = await _createAnAPIClient.AuthRepositoryUserDelete(repoCreateResponse.Data.Id, "username");
