:original_name: en-us_topic_0173938834.html

.. _en-us_topic_0173938834:

Authentication
==============

Requests for calling an API can be authenticated using a token.

Token Authentication
--------------------

.. note::

   The validity period of a token is 24 hours. When using a token for authentication, cache it to prevent frequently calling the IAM API used to obtain a user token.

A token specifies temporary permissions in a computer system. During API authentication using a token, the token is added to requests to get permissions for calling the API. You can obtain a token by calling the `Obtaining User Token <https://docs.sc.otc.t-systems.com/api/iam/en-us_topic_0057845583.html>`__ API.

A cloud service can be deployed as either a project-level service or global service.

-  For a project-level service, you need to obtain a project-level token. When you call the API, set **auth.scope** in the request body to **project**.
-  For a global service, you need to obtain a global token. When you call the API, set **auth.scope** in the request body to **domain**.

TMS is a global service. When you call the API, set **auth.scope** in the request body to **domain**. For details about how to obtain the user token, see `Obtaining a User Token <https://docs.sc.otc.t-systems.com/api/iam/en-us_topic_0057845583.html>`__.

.. code-block::

   {
       "auth": {
           "identity": {
               "methods": [
                   "password"
               ],
               "password": {
                   "user": {
                       "name": "username",   // IAM user name
                       "password": "********",  // IAM user password
                       "domain": {
                           "name": "domainname"  // Name of the account to which the IAM user belongs
                       }
                   }
               }
           },
           "scope": {
               "domain": {
                   "name": "xxxxxxxx"    // Project name
               }
           }
       }
   }

After a token is obtained, the **X-Auth-Token** header field must be added to requests to specify the token when calling other APIs. For example, if the token is **ABCDEFJ....**, **X-Auth-Token: ABCDEFJ....** can be added to a request as follows:

.. code-block:: text

   POST https://{{endpoint}}/v3/auth/projects
   Content-Type: application/json
   X-Auth-Token: ABCDEFJ....
