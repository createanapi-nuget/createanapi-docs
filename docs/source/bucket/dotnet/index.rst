.NET
==========

This section of the documentation details the public API
usable to get details of projects, builds, versions and other details
from Read the Docs.


.. code-block:: csharp
   :linenos:

    var key = "csv/product-1.csv";
    var bucketId = "62e2cb155f3d995ff233a48c";

Upload Blob
-----------

.. code-block:: csharp
   :linenos:

    var uploadFromPathResponse = await _createAnAPIClient.UploadBlob(bucketId, $"csv/product-1.csv", @"C:\Repositories\createanapi-apiclient\src\CreateAnAPI.Client\CreateAnAPI.Customer.BlobTask\bin\Debug\net6.0\product.csv");

    
Upload From Memory
------------------

.. code-block:: csharp
   :linenos:

    var blob = File.ReadAllBytes(@"C:\Repositories\createanapi-apiclient\src\CreateAnAPI.Client\CreateAnAPI.Customer.BlobTask\bin\Debug\net6.0\product.csv");
    var uploadFromMemoryResponse = await _createAnAPIClient.UploadBlob(bucketId, $"csv/product-1.csv", blob);
    
Upload Text
-----------

.. code-block:: csharp
   :linenos:

    var uploadAsTextResponse = await _createAnAPIClient.UploadBlobAsText(bucketId, $"csv/product-1.csv", "1,2,3");

    
Blob Exists
-----------

.. code-block:: csharp
   :linenos:

    var existsResponse = await _createAnAPIClient.BlobExists(bucketId, key);

    
Read Blob as Text
-----------------

.. code-block:: csharp
   :linenos:

    var textResponse = await _createAnAPIClient.ReadBlobAsText(bucketId, key);

Read Blob as Byte Array
-----------------------

.. code-block:: csharp
   :linenos:

    var blobResponse = await _createAnAPIClient.ReadBlob(bucketId, key);
    

Download Blob to Path
-----------------------

.. code-block:: csharp
   :linenos:

    await _createAnAPIClient.DownloadBlob(bucketId, key, @"C:\Repositories\createanapi-apiclient\src\CreateAnAPI.Client\CreateAnAPI.Customer.BlobTask\bin\Debug\net6.0\product2.csv");
    

Blob Metadata
-----------------------

.. code-block:: csharp
   :linenos:

    var metadataResponse = await _createAnAPIClient.GetBlobMetadata(bucketId, key);

    
Blob Search
-----------------------

.. code-block:: csharp
   :linenos:
   
    var searchResponse = await _createAnAPIClient.SearchBlob(bucketId, "csv/");

    
Blob Delete
-----------------------

.. code-block:: csharp
   :linenos:
   
    var deleteResponse = await _createAnAPIClient.DeleteBlob(bucketId, key);
    

