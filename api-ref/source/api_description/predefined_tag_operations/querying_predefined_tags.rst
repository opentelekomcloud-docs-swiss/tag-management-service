:original_name: en-us_topic_0056765936.html

.. _en-us_topic_0056765936:

Querying Predefined Tags
========================

Function
--------

This API is used to query predefined tags.

URI
---

GET /v1.0/predefine_tags

Request
-------

-  Parameter description

   .. table:: **Table 1** Parameters in the request

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                           |
      +=================+=================+=================+=======================================================================================================================================================================================================================================================================================================================+
      | key             | No              | String          | Specifies the key.                                                                                                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | Supports fuzzy search and is case insensitive. If this parameter value contains non-URL-safe characters, it must be URL encoded.                                                                                                                                                                                      |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value           | No              | String          | Specifies the value.                                                                                                                                                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | Supports fuzzy search and is case insensitive. If this parameter value contains non-URL-safe characters, it must be URL encoded.                                                                                                                                                                                      |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit           | No              | Integer         | Specifies the number of query records.                                                                                                                                                                                                                                                                                |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The value ranges from **1** to **1000**. If no value is specified, the value is **10** by default. If the value is set to **0**, the number of query records is not limited.                                                                                                                                          |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | marker          | No              | String          | Specifies the paging location identifier (index).                                                                                                                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The query starts from the next piece of data indexed by this parameter.                                                                                                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | .. note::                                                                                                                                                                                                                                                                                                             |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 |    When querying the data on the first page, you do not need to specify this parameter. When querying the data on subsequent pages, set this parameter to the value in the response body returned by querying data of the previous page. When the returned **tags** is an empty list, the last page has been queried. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | order_field     | No              | String          | Specifies the field for sorting.                                                                                                                                                                                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The parameter value is case sensitive and can be **update_time**, **key**, or **value**.                                                                                                                                                                                                                              |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | Its default value is **update_time**.                                                                                                                                                                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | You can choose only one of the three values and based on the value of **order_method** to sort the remaining two default fields.                                                                                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | For example:                                                                                                                                                                                                                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  If **order_field** is set to **update_time**, both **key** and **value** are sorted in the ascending order.                                                                                                                                                                                                        |
      |                 |                 |                 | -  If **order_field** is set to **key**, **update_time** is sorted in the descending order, and **value** is sorted in the ascending order.                                                                                                                                                                           |
      |                 |                 |                 | -  If **order_field** is set to **value**, **update_time** is sorted in the descending order, and **key** is sorted in the ascending order.                                                                                                                                                                           |
      |                 |                 |                 | -  If **order_field** is not specified, its default value **update_time** is taken. In this case, **key** and **value** are sorted in the ascending order.                                                                                                                                                            |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | order_method    | No              | String          | Specifies the sorting method of the **order_field** field.                                                                                                                                                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | The method can be (case sensitive):                                                                                                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | -  **asc**: ascending order                                                                                                                                                                                                                                                                                           |
      |                 |                 |                 | -  **desc**: descending order                                                                                                                                                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | Only one of the preceding sorting methods can be selected.                                                                                                                                                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                       |
      |                 |                 |                 | If this parameter is not specified, the default value is **desc**.                                                                                                                                                                                                                                                    |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      GET https://{TMS endpoint}/v1.0/predefine_tags?key=ENV&value=DEV&limit=10&marker=9&order_field=key&order_method=asc

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameters in the response

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                               |
      +=======================+=======================+===========================================================================================================+
      | tags                  | Array of objects      | Specifies the tags.                                                                                       |
      |                       |                       |                                                                                                           |
      |                       |                       | For details, see :ref:`Table 3 <en-us_topic_0056765936__en-us_topic_0056765543_table36783718>`.           |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
      | total_count           | Integer               | Specifies the total number of tags that meet the filtering criteria, which is not affected by pagination. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+
      | marker                | String                | Specifies the paging location identifier.                                                                 |
      |                       |                       |                                                                                                           |
      |                       |                       | It indicates the location of the last query record.                                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------+

-  **tags** field description

   .. _en-us_topic_0056765936__en-us_topic_0056765543_table36783718:

   .. table:: **Table 3** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                            |
      +=======================+=======================+========================================================================================================================================================+
      | key                   | String                | Specifies the key.                                                                                                                                     |
      |                       |                       |                                                                                                                                                        |
      |                       |                       | It cannot be left blank and can contain a maximum of 36 Unicode characters. Only digits, letters, hyphens (-), and underscores (_) are allowed.        |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value                 | String                | Specifies the value.                                                                                                                                   |
      |                       |                       |                                                                                                                                                        |
      |                       |                       | Each value contains a maximum of 43 Unicode characters and can be an empty string. Only digits, letters, hyphens (-), and underscores (_) are allowed. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | update_time           | String                | Specifies the update time, which must be the UTC time, for example, 2016-12-09T00:00:00Z.                                                              |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "marker": "12",
          "total_count": 13,
          "tags": [
              {
                  "key": "ENV1",
                  "value": "DEV1",
                  "update_time": "2017-04-12T14:22:34Z"
              },
              {
                  "key": "ENV2",
                  "value": "DEV2",
                  "update_time": "2017-04-12T14:22:34Z"
              }
          ]
      }

Status Codes
------------

See :ref:`Status Codes <en-us_topic_0130578970>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0057939857>`.
