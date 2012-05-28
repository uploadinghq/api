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

For any action you should pass such https headers

login password (https authorization)
Content-type (text/xml and application/json are supported for now)

######GET /user/info

description: Gets info of authed user

request fields:none

success response sample in JSON<code><pre>{"user":
            {
             "email":"alexeygeno@gmail.com","account_status":"active",
             "nick_name":"","files_size":"249.67527580261245",
             "files_size_limit":"0","files_count":"153","premium_expire":"1333698313"
            }
}</pre></code>

######GET /user/files

--TODO--

Description:gets folders/files tree for authed user


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





