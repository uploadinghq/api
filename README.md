Uploading.com REST API
=================

#### REST API

REST API HOST https://api.uploading.com

#### HTTP authentication
You should login with http authentication by passing your email and password.

REQUEST
```bash
curl -k --user  alexeygeno@gmail.com:123456 https://sluggard.api.dev.uploading.com/user/info
```

RESPONSE
```xml
<?xml version="1.0"?>
<user>
            <user_id>1990936</user_id>
            <account_status>active</account_status>
            <nick_name></nick_name>
            <files_size>177.86605358123796</files_size>
            <files_size_limit>0</files_size_limit>
            <files_count>108</files_count>
            <premium_expire>1333698313</premium_expire><
/user>

```
####

#### Response data formats
JSON and XML are supported for now. By default it is XML. To get response in JSON pass at HTTP header "Accept: aplication/json" 

#####Sample wrong authorization with JSON response

REQUEST
```bash
curl -k --header "Accept:application/json" --user  alexeygeno@gmail.com:wrongpass https://sluggard.api.dev.uploading.com/user/info
```
RESPONSE
```json
{"error":{"message":"Access denied","hint":"Use correct email\/password"}}
```

#### HTTP statuses and error codes
Success status is standart HTTP status 200.

Error codes are returned as standard HTTP status response header.
Any additional info about error and hint about how tofix it are included in the body of HTTP response.

Below you can see codes and short description.

400 - Bad input parameter

403 - Forbidden

404 - Not Found

405 - Request method is not expected

406 - Data error

500 - Internal server error

#####Sample to do POST request that is not supported for method

REQUEST
```bash
 curl -k -v --data "field=val"  --header  "Accept:text/xml" --user  alexeygeno@gmail.com:123456 https://sluggard.api.dev.uploading.com/user/info
```

HEADER STATUS
```bash
< HTTP/1.1 405 Request method is not expected
```

RESPONSE

```xml
<?xml version="1.0"?>
<error>
 <message>Request method not expected (generally should be GET or POST)</message>
 <hint>Use correct method for this url</hint>
</error>
```


#### API methods

######GET /user/info

description: gets user info

request fields:none

sample

REQUEST
```bash
curl -k --user  alexeygeno@gmail.com:123456 https://sluggard.api.dev.uploading.com/user/info
```

RESPONSE
```xml
<?xml version="1.0"?>
<user>
            <user_id>1990936</user_id>
            <account_status>active</account_status>
            <nick_name></nick_name>
            <files_size>177.86605358123796</files_size>
            <files_size_limit>0</files_size_limit>
            <files_count>108</files_count>
            <premium_expire>1333698313</premium_expire>
</user>
```



######GET /user/files  --NOT COMPLETED--

Description: gets folders/files tree

request fields:

folder_id - requireed, 0 - root folder.

sample

REQUEST
```bash
curl -k --get --data "folder_id=3434" --user alexeygeno@gmail.com:123456 https://sluggard.api.dev.uploading.com/user/files
```

RESPONSE
```xml
<?xml version="1.0"?>
<files>
           
</files>
```


######POST /files/rename 

Description: renames file

request fields:

file_id - requireed, int

file_name - required

sample

REQUEST
```bash
curl -k --data "file_id=124&file_name=new_name.txt" --user alexeygeno@gmail.com:123456 https://sluggard.api.dev.uploading.com/files/rename
```

RESPONSE
```xml
<?xml version="1.0"?>
<file>
   <file_id>124</file_id>
   <file_name>new_name.txt</file_name>
   <old_file_name>name.txt</old_file_name>               
</file>
```


######GET /files/link 

Description: gets download file link

request fields:

file_id - requireed, int

sample

REQUEST
```bash
curl -k --get --data "file_id=124" --user alexeygeno@gmail.com:123456 https://sluggard.api.dev.uploading.com/files/link
```

RESPONSE
```xml
<?xml version="1.0"?>
<file>
   <link>http://fs10.sluggard.www.dev.uploading.com/get_file/%3DMQ0ncR29nSAkGTonbQrteTGAPwTSfrDDW7HPzZpqynJLcDNSAtKmjJyiB2E0blFuvAJxUW2Di4bOkYhc6rbmemBXzZMjgPLnLhhL86Y2QmPd48EB-X5BTKVxbQ71AcXeYfp6yTXQXC6eqVJrQd7jlJ4I6RUG28Ww1JCfH5Zud7X7mTWhJqPS1tInA442tA0JlkXpcoNMlLCHK6yPHsLgSgk5BneaprWCrFd%7ChMi1Tp36%7Cs3Fj15SaeqLm8LvLMWQvKA0JwXQBiS1fSYIWyie5ieAxOwRm5pWsnDM-vQ0shBgv5aTj08PUlbxmAEzpdTJLzgGyk2Ufu2Au5zfcD4GUyHv7%7CWBKIe%7CuGO1Gd4hy-z</link>
   <session_id>5f218f903c6519b57c3e3e71c7c4ab0c</session_id>
</file>
```





