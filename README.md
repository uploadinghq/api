Uploading.com API
=================

#### REST API

description ....

REST API URL https://api.dev.uploading.com

You should login with https authorizion by passing your email/login and password.

#### 

#### Response data formats
JSON and XML are supported for now. 


#### Error codes

Error codes are returned as standard HTTP response headers . Any additional info is included in the body of HTTP response, JSON or XML-formatted.
Below you can see errors codes and short description.

400 - Bad input parameter

403 - Forbidden

404 - Not Found

405 - Request method is not expected

406 - Data not found

500 - Internal server error

#### API methods

######GET /user/info

description: Gets info of authed user

required request http headers:

request fields:none


success response sample in XML

<code><pre>{"user":{"user_id":"1990936","email":"alexeygeno@gmail.com","account_status":"active",
"nick_name":"","last_billing_id":"0","files_size":"249.67527580261245",
"files_size_limit":"0","files_count":"153","language_id":"1","is_affiliate":"0","enable_ip_blocking":"0",
"user_agent":"Mozilla\/5.0 (Windows NT 6.0; rv:10.0) Gecko\/20100101 Firefox\/10.0",
"referer_file_id":"49876729","referer_url":"","registered":"1333121238","premium_expire":"1333698313",
"last_login":"1337781131","registration_ip":"212.92.243.39","user_ip":"192.168.1.1",
"session_id":"724ee9e91c1052e6577b12c8c654380c","comment":"","is_verified":"0","verified_code":"",
"premium_count":"0"}}</pre></code>

######GET /user/files

Description:gets folders/files tree for authed user

request http headers:
request fields:

folder_id - not required. If it is not passed then all folders and files will  be returned.

description: Gets info of authed user

success response sample in XML





