:original_name: en-us_topic_0133313257.html

.. _en-us_topic_0133313257:

Querying Details About a Specified TMS API Version
==================================================

Function
--------

This API is used to query the details of a specified TMS API version.

URI
---

GET /{api_version}

Request
-------

-  Parameter description

   .. table:: **Table 1** Request parameters

      =========== ========= ====== ==========================
      Parameter   Mandatory Type   Description
      =========== ========= ====== ==========================
      api_version Yes       String Specifies the API version.
      =========== ========= ====== ==========================

-  Example request

   .. code-block:: text

      GET https://{TMS endpoint}/v1.0

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameters in the response

      +-----------------------+-----------------------+-------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                   |
      +=======================+=======================+===============================================================================+
      | version               | object                | Specifies the version of a specified API.                                     |
      |                       |                       |                                                                               |
      |                       |                       | For details, see :ref:`Table 3 <en-us_topic_0133313257__table7480934143011>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------+

-  **version** field data structure

   .. _en-us_topic_0133313257__table7480934143011:

   .. table:: **Table 3** **version** field data structure description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | Name                  | Type                  | Description                                                                                                                                       |
      +=======================+=======================+===================================================================================================================================================+
      | id                    | String                | Specifies the version ID, for example, v1.0.                                                                                                      |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | links                 | List<Link>            | Specifies the API URL.                                                                                                                            |
      |                       |                       |                                                                                                                                                   |
      |                       |                       | For details, see :ref:`Table 4 <en-us_topic_0133313257__table86914347304>`.                                                                       |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | version               | String                | If the APIs of this version support microversions, set this parameter to the supported latest microversion. If not, leave this parameter blank.   |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Specifies the version status.                                                                                                                     |
      |                       |                       |                                                                                                                                                   |
      |                       |                       | Possible values are as follows:                                                                                                                   |
      |                       |                       |                                                                                                                                                   |
      |                       |                       | -  **CURRENT**: indicates that the version is the primary version.                                                                                |
      |                       |                       | -  **SUPPORTED**: indicates that the version is an old version, but it is still supported.                                                        |
      |                       |                       | -  **DEPRECATED**: indicates a deprecated version which may be deleted later.                                                                     |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | updated               | String                | Specifies the version release time, which must be the UTC time. For example, the release time of TMS 1.0 is 2016-12-09T00:00:00Z.                 |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
      | min_version           | String                | If the APIs of this version support microversions, set this parameter to the supported earliest microversion. If not, leave this parameter blank. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

-  **Links** field data structure

   .. _en-us_topic_0133313257__table86914347304:

   .. table:: **Table 4** **Links** field data structure description

      ==== ====== ======================
      Name Type   Description
      ==== ====== ======================
      href String Specifies the API URL.
      rel  String self
      ==== ====== ======================

-  Example response

   .. code-block::

      {
          "version": {
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
      }

Status Codes
------------

See :ref:`Status Codes <en-us_topic_0130578970>`.

Error Codes
-----------

See :ref:`Error Codes <en-us_topic_0057939857>`.
