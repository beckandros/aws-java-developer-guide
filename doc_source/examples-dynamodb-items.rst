.. Copyright 2010-2017 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

###########################
Working with Items in |DDB|
###########################

.. meta::
   :description: How to retrieve (get), add, and update items in Amazon DynamoDB tables.
   :keywords: AWS for Java SDK code examples, items from DynamoDB tables


In |ddb|, an item is a collection of *attributes*, each of which has a *name* and a *value*. An
attribute value can be a scalar, set, or document type. For more information, see :ddb-dg:`Naming
Rules and Data Types <HowItWorks.NamingRulesDataTypes>` in the |ddb-dg|.

.. _dynamodb-get-item:

Retrieve (Get) an Item from a Table
===================================

Call the |ddbclient|'s :methodname:`getItem` method and pass it a
:aws-java-class:`GetItemRequest <services/dynamodbv2/model/GetItemRequest>` object with the table
name and primary key value of the item you want. It returns a `GetItemResult
<services/dynamodbv2/model/GetItemResult>` object.

You can use the returned :classname:`GetItemResult` object's :methodname:`getItem()` method to
retrieve a :javase-ref:`Map <java/util/Map>` of key (String) and value
(:aws-java-class:`AttributeValue <services/dynamodbv2/model/AttributeValue>`) pairs that are associated
with
the item.

**Imports**

.. literalinclude:: example_code/dynamodb/src/main/java/aws/example/dynamodb/GetItem.java
   :lines: 15-21
   :language: java

**Code**

.. literalinclude:: example_code/dynamodb/src/main/java/aws/example/dynamodb/GetItem.java
   :lines: 68-102
   :dedent: 8
   :language: java

See the :sdk-examples-java-dynamodb:`complete sample <GetItem.java>`.


.. _dynamodb-add-item:

Add a New Item to a Table
=========================

Create a :javase-ref:`Map <java/util/Map>` of key-value pairs that
represent the item's attributes. These must include values for the table's primary key fields. If the
item identified by the primary key already exists, its fields are *updated* by the request.

.. note:: If the named table doesn't exist for your account and region, a
   :aws-java-class:`ResourceNotFoundException <services/dynamodbv2/model/ResourceNotFoundException>` is
   thrown.

**Imports**

.. literalinclude:: example_code/dynamodb/src/main/java/aws/example/dynamodb/PutItem.java
   :lines: 15-20
   :language: java

**Code**

.. literalinclude:: example_code/dynamodb/src/main/java/aws/example/dynamodb/PutItem.java
   :lines: 76-96
   :dedent: 8
   :language: java

See the :sdk-examples-java-dynamodb:`complete sample <PutItem.java>`.


.. _dynamodb-update-item:

Update an Existing Item in a Table
==================================

You can update an attribute for an item that already exists in a table by using the |ddbclient|'s
:methodname:`updateItem` method, providing a table name, primary key value, and a map of fields to
update.

.. note:: If the named table doesn't exist for your account and region, or if the item identified by
   the primary key you passed in doesn't exist, a :aws-java-class:`ResourceNotFoundException
   <services/dynamodbv2/model/ResourceNotFoundException>` is thrown.

**Imports**

.. literalinclude:: example_code/dynamodb/src/main/java/aws/example/dynamodb/UpdateItem.java
   :lines: 15-22
   :language: java

**Code**

.. literalinclude:: example_code/dynamodb/src/main/java/aws/example/dynamodb/UpdateItem.java
   :lines: 82-105
   :dedent: 8
   :language: java

See the :sdk-examples-java-dynamodb:`complete sample <UpdateItem.java>`.


More Info
=========

* :ddb-dg:`Guidelines for Working with Items <GuidelinesForItems>` in the |ddb-dg|
* :ddb-dg:`Working with Items in DynamoDB <WorkingWithItems>` in the |ddb-dg|
