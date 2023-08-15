:original_name: en-us_topic_0186103096.html

.. _en-us_topic_0186103096:

Obtaining the Domain-Level Token
================================

.. code-block::

   POST https://{{endpoint}}/v3/auth/tokens
   Content-Type: application/json

   {
       "auth": {
           "identity": {
               "methods": [
                   "password"
               ],
               "password": {
                   "user": {
                       "name": "username",
                       "password": "********",
                       "domain": {
                           "name": "domainname"
                       }
                   }
               }
           },
           "scope": {
               "domain": {
                   "id": "xxxxxxxxxxxxxxxxxx"
               }
           }
       }
   }
