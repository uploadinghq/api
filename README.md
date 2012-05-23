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


success response sample in JSON

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

success response sample in JSON

<code><pre>{"files":{"size":135198738,"folder":
            [{"folder_id":"3394","name":"aaaa",
            "create_date":"2012-04-27 18:42:30","access_type":"public","size":3422268,
            "file":[{"file_id":"319","size":"1711134","downloads_count":"0",
            "create_date":"2012-04-27 18:42:30","status":"active",
            "name":"Dscn0162 - \u043a\u043e\u043f\u0438\u044f.jpg",
            "code":"c72a2de1","description":"","storage_id":"1","folder_id":"3394"},
            {"file_id":"329","size":"1711134","downloads_count":"0",
            "create_date":"2012-04-27 18:42:31","status":"active",
            "name":"Dscn0162 - \u043a\u043e\u043f\u0438\u044f.jpg",
            "code":"em79c514","description":"","storage_id":"1","folder_id":"3394"}]},
            {"folder_id":"3330","name":"aaaa","create_date":"2012-04-23 12:48:36","access_type":
            "public","size":3422268,"file":[{"file_id":"67","size":"1711134","downloads_count":"0",
            "create_date":"2012-04-19 21:09:46","status":"active",
            "name":"Dscn0162 - \u043a\u043e\u043f\u0438\u044f.jpg","code":"4m66abde","description":"",
            "storage_id":"1","folder_id":"3330"},{"file_id":"105","size":"1711134",
            "downloads_count":"0","create_date":"2012-04-23 18:18:03","status":"active",
            "name":"Dscn0162 - \u043a\u043e\u043f\u0438\u044f.jpg","code":"ccd8ce4m",
            "description":"","storage_id":"1","folder_id":"3330"}]},{"folder_id":"3375",
            "name":"aaaaaa","create_date":"2012-04-27 13:55:49","access_type":"public","size":0},
            {"folder_id":"3422","name":"aaaaaa","create_date":"2012-04-27 18:42:30","access_type":"public","size":0},
            {"folder_id":"3367","name":"dsfsfsdf","create_date":"2012-04-27 13:37:25","access_type":"public","size":0}
            ]}}</pre></code>





