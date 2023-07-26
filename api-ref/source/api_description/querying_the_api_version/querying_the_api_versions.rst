:original_name: en-us_topic_0133313256.html

.. _en-us_topic_0133313256:

Querying the API Versions
=========================

Function
--------

This API is used to query the versions of all TMS APIs.

URI
---

GET /

Request
-------

Example request

.. code-block:: text

   GET https://{TMS endpoint}/

.. note::

   Obtain the regions and endpoints from the enterprise administrator.

   Domain-level tokens are required for invoking TMS APIs. For details, see :ref:`Obtaining the Domain-Level Token <en-us_topic_0186103096>`.

Response
--------

-  Parameter description

   .. table:: **Table 1** Parameters in the response

      +-----------------------+-----------------------+------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                  |
      +=======================+=======================+==============================================================================+
      | versions              | Array                 | Specifies all API versions.                                                  |
      |                       |                       |                                                                              |
      |                       |                       | For details, see :ref:`Table 2 <en-us_topic_0133313256__table374991515234>`. |
      +-----------------------+-----------------------+------------------------------------------------------------------------------+

-  **versions** field description

   .. _en-us_topic_0133313256__table374991515234:

   .. table:: **Table 2** Parameter description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                       |
      +=======================+=======================+===================================================================================================================================================+
      | id                    | String                | Specifies the version ID, for example, v1.0.                                                                                                      |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | links                 | List<Link>            | Specifies the API URL.                                                                                                                            |
      |                       |                       |                                                                                                                                                   |
      |                       |                       | For details, see :ref:`Table 3 <en-us_topic_0133313256__table87796151239>`.                                                                       |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | version               | String                | If the APIs of this version support microversions, set this parameter to the supported latest microversion. If not, leave this parameter blank.   |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Specifies the version status.                                                                                                                     |
      |                       |                       |                                                                                                                                                   |
      |                       |                       | Possible statuses are as follows:                                                                                                                 |
      |                       |                       |                                                                                                                                                   |
      |                       |                       | -  **CURRENT**: indicates that the version is the primary version.                                                                                |
      |                       |                       | -  **SUPPORTED**: indicates that the version is an old version, but it is still supported.                                                        |
      |                       |                       | -  **DEPRECATED**: indicates a deprecated version which may be deleted later.                                                                     |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | updated               | String                | Specifies the version release time, which must be the UTC time. For example, the release time of TMS 1.0 is 2016-12-09T00:00:00Z.                 |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | min_version           | String                | If the APIs of this version support microversions, set this parameter to the supported earliest microversion. If not, leave this parameter blank. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

-  **Links** field description

   .. _en-us_topic_0133313256__table87796151239:

   .. table:: **Table 3** Parameter description

      ==== ====== ======================
      Name Type   Description
      ==== ====== ======================
      href String Specifies the API URL.
      rel  String self
      ==== ====== ======================

-  Example response

   .. code-block::

      {
          "versions": [
              {
                  "id": "v1.0",
                  "links": [
                      {
                          "rel": "self",
                          "href": "https://API URL/v1.0"
                      }
                  ],
                  "version": "",
                  "status": "CURRENT",
                  "updated": "2016-12-09T00:00:00Z",
                  "min_version": ""
              }
          ]
      }

Status Codes
------------

See :ref:`Status Codes <en-us_topic_0130578970>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0057939857>`.
