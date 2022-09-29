Repository .NET Client
======================

This section of the documentation details the public API
usable to get details of projects, builds, versions and other details
from Read the Docs.

Post Data
---------

Creates a new data.

.. code-block:: csharp
   :linenos:

    var post = await _createAnAPIClient.Post(_config.RepositoryId, new PostDataRequest<Order>
    {
        Data = GenerateFakeData<Order>(),
        Logs = new List<object>()
        {
            new
            {
                Success=true,
            }
        },
        State = 1
    });



Post Data List
---------------

Creates a new data in bulk. Max 250 items.

.. code-block:: csharp
   :linenos:

    var postList = await _createAnAPIClient.PostList(_config.RepositoryId, new PostBatchDataRequest<Order>()
    {
        Items = new List<PostDataRequest<Order>>()
        {
            new PostDataRequest<Order>()
            {
                Data = GenerateFakeData<Order>(),
                Logs = new List<object>()
                {
                    new
                    {
                        Success=true,
                    }
                },
                State = 1
            },
            new PostDataRequest<Order>()
            {
                Data = GenerateFakeData<Order>(),
                Logs = new List<object>()
                {
                    new
                    {
                        Success=true,
                    }
                },
                State = 1
            },
            new PostDataRequest<Order>()
            {
                Data = GenerateFakeData<Order>(),
                Logs = new List<object>()
                {
                    new
                    {
                        Success=true,
                    }
                },
                State = 1
            },
        }
    });



Update Data
---------------

Updates a data by id.

.. code-block:: csharp
   :linenos:

    var update = await _createAnAPIClient.Update(_config.RepositoryId, post.Data.DataId, new PutDataRequest<Order>()
    {
        Data = GenerateFakeData<Order>(),
        State = 1,
        Logs = new List<object>()
    });



Update Data List
----------------

Updates multiple items in bulk. Max 250 items.

.. code-block:: csharp
   :linenos:

    var updateList = await _createAnAPIClient.UpdateList(_config.RepositoryId, new PutBatchDataRequest<Order>()
    {
        Items = new List<PutBatchDataItemRequest<Order>>()
        {
            new PutBatchDataItemRequest<Order>()
            {
                Data = GenerateFakeData<Order>(),
                State = 1,
                Logs = new List<object>()
                {
                    new
                    {
                        success=true
                    }
                },
                Id = post.Data.DataId
            },
            new PutBatchDataItemRequest<Order>()
            {
                Data = GenerateFakeData<Order>(),
                State = 1,
                Logs = new List<object>()
                {
                    new
                    {
                        success=true
                    }
                },
                Id = post.Data.DataId
            },
            new PutBatchDataItemRequest<Order>()
            {
                Data = GenerateFakeData<Order>(),
                State = 1,
                Logs = new List<object>()
                {
                    new
                    {
                        success=true
                    }
                },
                Id = post.Data.DataId
            }
        }
    });



Change State
---------------

Changes data states in bulk based on states and / or data filters.

.. code-block:: csharp
   :linenos:

    var changeState = await _createAnAPIClient.ChangeState(_config.RepositoryId, new ChangeStateRequest()
    {
        Filters = new List<DataFilter>(),
        NewState = 1,
        OldState = null
    });



Get Data
---------------

Returns an item by id.

.. code-block:: csharp
   :linenos:

    var get = await _createAnAPIClient.Get<Order>(_config.RepositoryId, post.Data.DataId);


Get Data List
---------------

Returns item list by states and / or data filters. Max 250 items.

.. code-block:: csharp
   :linenos:

    var getList = await _createAnAPIClient.GetList<Order>(_config.RepositoryId, 0, 10, null, new List<DataFilter>());


Get All Data
---------------

Returns all item list by states and / or data filters. 

.. code-block:: csharp
   :linenos:

    var getAll = await _createAnAPIClient.GetAll<Order>(_config.RepositoryId, null, new List<DataFilter>(), 250);


Get First Data
---------------

Returns first item in list by states and / or data filters. 

.. code-block:: csharp
   :linenos:
   
    var first = await _createAnAPIClient.First<Order>(_config.RepositoryId, null, new List<DataFilter>());


Get Data Count
---------------

Returns count of items in list by states and / or data filters. 

.. code-block:: csharp
   :linenos:

    var count = await _createAnAPIClient.Count(_config.RepositoryId);


Get Sum of a given Field
------------------------

Returns sum of items given field in list by states and / or data filters. 

.. code-block:: csharp
   :linenos:

    var sum = await _createAnAPIClient.Sum<decimal>(_config.RepositoryId, "totalAmount", null, new List<DataFilter>());


Get AVG of a given Field
------------------------

Returns average of items given field in list by states and / or data filters. 

.. code-block:: csharp
   :linenos:

    var avg = await _createAnAPIClient.Avg<decimal>(_config.RepositoryId, "totalAmount", null, new List<DataFilter>());


Get Min of a given Field
------------------------

Returns minimum of items given field in list by states and / or data filters. 

.. code-block:: csharp
   :linenos:

    var min = await _createAnAPIClient.Min<DateTime>(_config.RepositoryId, "orderDate", null, new List<DataFilter>());


Get Max of a given Field
------------------------

Returns maximum of items given field in list by states and / or data filters. 

.. code-block:: csharp
   :linenos:

    var max = await _createAnAPIClient.Max<DateTime>(_config.RepositoryId, "orderDate", null, new List<DataFilter>());


Delete Data
---------------

Deletes a single data by id

.. code-block:: csharp
   :linenos:

    var result = await _createAnAPIClient.Delete(repositoryId, dataId);


Delete Data List
----------------

Deletes items based on states and / or filters

.. code-block:: csharp
   :linenos:

    var result = await _createAnAPIClient.DeleteList(repositoryId, new DeleteListRequest()
    {
        Filters = new List<DataFilter>()
        {
            new DataFilter()
            {
                Key = "field",
                Value = "eq",
                Operation = "5"
            }
        },
        State = 1
    });
 


Filter Operations
---------------------

.. code-block:: csharp
   :linenos:

    var filter = new DataFilter()
    {
        Key = "status",
        Operation = StringOperation.Equals,
        Value = "Active"
    };



Available Filter Operations
---------------------------

.. code-block:: csharp
   :linenos:

    StringOperation.Contains;
    StringOperation.EndsWith;
    StringOperation.Equals;
    StringOperation.NotContains;
    StringOperation.NotEquals;
    StringOperation.StartsWith;

    DateTimeOperation.Between;
    DateTimeOperation.Equals;
    DateTimeOperation.Greater;
    DateTimeOperation.GreaterThenOrEqual;
    DateTimeOperation.Less;
    DateTimeOperation.LessThenOrEqual;
    DateTimeOperation.NotEquals;

    DecimalOperation.Between;
    DecimalOperation.Equals;
    DecimalOperation.Greater;
    DecimalOperation.GreaterThenOrEqual;
    DecimalOperation.Less;
    DecimalOperation.LessThenOrEqual;
    DecimalOperation.NotEquals;
                
    IntegerOperation.Between;
    IntegerOperation.Equals;
    IntegerOperation.Greater;
    IntegerOperation.GreaterThenOrEqual;
    IntegerOperation.Less;
    IntegerOperation.LessThenOrEqual;
    IntegerOperation.NotEquals;
    
Aggregate Union Step
---------------------

Combines multiple repositoryies as one

.. code-block:: csharp
   :linenos:

    var unionList = await _createAnAPIClient.AggregateGetList<Product>(_config.Product1RepositoryId, new Aggregation()
    {
        Steps = new List<AggregationStep>()
        {
            new AggregationStep()
            {
                Type = "union",
                UnionRepositoryId = _config.Product2RepositoryId
            },
        }
    }, 0, 20, null, null, new List<DataSort>()
    {
        new DataSort()
        {
            Desc = true,
            Selector = "Quantity"
        }
    });


Aggregate Lookup Step
---------------------

Left joins another repository by matching given fields. 

.. code-block:: csharp
   :linenos:

    var lookupList = await _createAnAPIClient.AggregateGetList<LookupProduct>(_config.Product1RepositoryId, new Aggregation()
    {
        Steps = new List<AggregationStep>()
        {
            new AggregationStep()
            {
                Type = "lookup",
                As = "Parts",
                ForeignField = "ProductId",
                LocalField = "ProductId",
                LookupRepositoryId = _config.PartRepositoryId
            }
        }
    }, 0, 20, null, new List<DataFilter>(), new List<DataSort>()
    {
        new DataSort()
        {
            Desc = true,
            Selector = "Quantity"
        }
    });


Aggregate Unwind Step
---------------------

Unwinds an item array and lets user to filter array items.

.. code-block:: csharp
   :linenos:

    var unwindList = await _createAnAPIClient.AggregateGetList<UnwindProduct>(_config.Product1RepositoryId, new Aggregation()
    {
        Steps = new List<AggregationStep>()
        {
            new AggregationStep()
            {
                Type = "unwind",
                Field = "Warehouses"
            },
        }
    });




Convensions
---------------------

.. code-block:: csharp
   :linenos:

    //Service
    public class PascalCase 
    {
        //Injected Service
        private readonly Service _underScoreCamelCase;

        //Public Property
        public string PascalCase { get; set; }

        //Constructor
        public void PascalCase(string camelCase)
        {
            //Local variable
            var camelCase = 5;
        }
    }

    //Endpoint
    [HTTPPost("/api/kebab-case")]

    //DTO
    public class Order
    {
        [JsonPropertyName("customerId")]
        public int? CustomerId { get; set; }

        [JsonPropertyName("shippingCost")]
        public decimal? ShippingCost { get; set; }

        [JsonPropertyName("lines")]
        public List<Line> Lines{ get; set; }
    }


Rules
---------------------

Create C# Class for each repository

Keep the Class in the shared library of customer

Use First to check if entity inserted before

Don't overuse GetAll, instead do First request to match items. GetAll is only applicable when dealing with all items in a repository such as "Get all orders with State 1".

Define fields to be filtered or sorted to the Repository Fields

Use Logs

Development Log Level: Debug

Production Log Level Task: Warning

Production Log Level Web: Warning

New NuGet Server: http://3.136.213.197:8081/nuget