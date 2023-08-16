:original_name: en-us_topic_0060929630.html

.. _en-us_topic_0060929630:

Modifying Predefined Tags
=========================

Function
--------

This API is used for modifying predefined tags.

URI
---

PUT /v1.0/predefine_tags

Request
-------

-  Parameter description

   .. table:: **Table 1** Parameters in the request

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                    |
      +=================+=================+=================+================================================================================+
      | old_tag         | Yes             | Object          | Specifies the tag to be modified.                                              |
      |                 |                 |                 |                                                                                |
      |                 |                 |                 | For details, see :ref:`Table 2 <en-us_topic_0060929630__table62639743182827>`. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+
      | new_tag         | Yes             | Object          | Specifies the tag that has been modified.                                      |
      |                 |                 |                 |                                                                                |
      |                 |                 |                 | For details, see :ref:`Table 3 <en-us_topic_0060929630__table39454339814>`.    |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------+

-  **old_tag** field description

   .. _en-us_topic_0060929630__table62639743182827:

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                            |
      +=================+=================+=================+========================================================================================================================================================+
      | key             | Yes             | String          | Specifies the key.                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                        |
      |                 |                 |                 | It cannot be left blank and can contain a maximum of 36 Unicode characters. Only digits, letters, hyphens (-), and underscores (_) are allowed.        |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value           | Yes             | String          | Specifies the value.                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                        |
      |                 |                 |                 | Each value contains a maximum of 43 Unicode characters and can be an empty string. Only digits, letters, hyphens (-), and underscores (_) are allowed. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

-  **new_tag** field description

   .. _en-us_topic_0060929630__table39454339814:

   .. table:: **Table 3** Parameter description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name            | Mandatory       | Type            | Description                                                                                                                                            |
      +=================+=================+=================+========================================================================================================================================================+
      | key             | Yes             | String          | Specifies the key.                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                        |
      |                 |                 |                 | It cannot be left blank and can contain a maximum of 36 Unicode characters. Only digits, letters, hyphens (-), and underscores (_) are allowed.        |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value           | Yes             | String          | Specifies the value.                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                        |
      |                 |                 |                 | Each value contains a maximum of 43 Unicode characters and can be an empty string. Only digits, letters, hyphens (-), and underscores (_) are allowed. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      PUT https://{TMS endpoint}/v1.0/predefined_tags

   .. code-block::

      {
          "new_tag": {
              "key": "ENV1",
              "value": "DEV1"
          },
          "old_tag": {
              "key": "ENV2",
              "value": "DEV2"
          }
      }

Response
--------

-  Parameter description

   None

-  Example response

   None

Status Codes
------------

See :ref:`Status Codes <en-us_topic_0130578970>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0057939857>`.
