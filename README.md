Uploading.com REST API
=================

The all-new Uploading.com API revealed. This is a REST-style API that uses JSON and XML for serialization and of course authentication.

#### REST API

REST API URL https://api.uploading.com

#### HTTP authentication
You should login with http authentication by passing your email and password.

REQUEST
```bash
curl -k --user  testuser@uploading.com:123456 https://api.uploading.com/user/info
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
####

#### Response data formats
JSON and XML are supported for now. By default we're using XML. To get response in JSON fromat, pass additional HTTP header "Accept: aplication/json" 

#####Sample wrong authorization with JSON response

REQUEST
```bash
curl -k --header "Accept:application/json" --user  testuser@uploading.com:wrongpass https://api.uploading.com/user/info
```
RESPONSE
```json
{"error":{"message":"Access denied","hint":"Use correct email\/password"}}
```

#### HTTP statuses and error codes
Success status is standart HTTP status 200.

Error codes are returned as standard HTTP status response header.
Any additional info about errors and hints how to fix it are included in the body of HTTP response.

Below you can check status codes and short description.

400 - Bad input parameter

403 - Forbidden

404 - Not Found

405 - Request method is not expected

406 - Data error

500 - Internal server error

#####Sample to do POST request that is not supported for method

REQUEST
```bash
 curl -k -v --data "field=val"  --header  "Accept:text/xml" --user  testuser@uploading.com:123456 https://api.uploading.com/user/info
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

Description: gets user info

Request fields: none

#####Sample

REQUEST
```bash
curl -k --user  testuser@uploading.com:123456 https://api.uploading.com/user/info
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

######GET /user/folders

Description: gets data for building folders tree and info about active, inactive, banned, blocked, deleted and favorites files count. And info about all user files size.

Request fields: none

#####Sample

#####

REQUEST
```bash
curl -k --user  testuser@uploading.com:123456 https://api.uploading.com/user/folders
```

RESPONSE
```xml
<?xml version="1.0"?>
<tree>
   <files_count>
      <active>77</active>
      <inactive>0</inactive>
      <banned>0</banned>
      <blocked>0</blocked>
      <deleted>99</deleted>
      <favourite>0</favourite>
      <files_size>123737512</files_size>
   </files_count>
   <folders>
      <folder_id>3433</folder_id>
      <name>eeee</name>
      <create_date>1335541350</create_date>
      <access_type>public</access_type>
      <parent_id>0</parent_id>
      <files_count>2</files_count>
   </folders>
   <folders>
      <folder_id>3438</folder_id>
      <name>eeee</name>
      <create_date>1335541420</create_date>
      <access_type>shared</access_type>
      <parent_id>0</parent_id>
      <files_count>2</files_count>
   </folders>  
</tree>
```

######GET /user/files  --NOT COMPLETED--

Description: gets folders/files tree

Request fields:

folder_id - requireed, 0 - root folder.

#####

REQUEST
```bash
curl -k --get --data "folder_id=3434" --user testuser@uploading.com:123456 https://api.uploading.com/user/files
```

RESPONSE
```xml
<?xml version="1.0"?>
<files>
           
</files>
```


######POST /files/rename 

Description: renames file

Request fields:

file_id - requireed, int

file_name - required

#####Sample

REQUEST
```bash
curl -k --data "file_id=124&file_name=new_name.txt" --user testuser@uploading.com:123456 https://api.uploading.com/files/rename
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

Request fields:

file_id - requireed, int

#####Sample

REQUEST
```bash
curl -k --get --data "file_id=124" --user testuser@uploading.com:123456 https://api.uploading.com/files/link
```

RESPONSE
```xml
<?xml version="1.0"?>
<file>
   <link>http://fs10.sluggard.www.dev.uploading.com/get_file/%3DMQ0ncR29nSAkGTonbQrteTGAPwTSfrDDW7HPzZpqynJLcDNSAtKmjJyiB2E0blFuvAJxUW2Di4bOkYhc6rbmemBXzZMjgPLnLhhL86Y2QmPd48EB-X5BTKVxbQ71AcXeYfp6yTXQXC6eqVJrQd7jlJ4I6RUG28Ww1JCfH5Zud7X7mTWhJqPS1tInA442tA0JlkXpcoNMlLCHK6yPHsLgSgk5BneaprWCrFd%7ChMi1Tp36%7Cs3Fj15SaeqLm8LvLMWQvKA0JwXQBiS1fSYIWyie5ieAxOwRm5pWsnDM-vQ0shBgv5aTj08PUlbxmAEzpdTJLzgGyk2Ufu2Au5zfcD4GUyHv7%7CWBKIe%7CuGO1Gd4hy-z</link>
   <session_id>5f218f903c6519b57c3e3e71c7c4ab0c</session_id>
</file>
```

######POST /files/upload 

Description: prepares upload, gets storage file link

Request fields:

folder_id - required, int

file_name - required

file_size - required, int

#####Sample

REQUEST
```bash
curl -k --data "folder_id=3432&file_name=sample.txt&file_size=11112" --user testuser@uploading.com:123456 https://api.uploading.com/files/upload
```

RESPONSE
```xml
<?xml version="1.0"?>
<file>
   <code>1172aec8</code>
   <name>sample.txt</name>
   <size>11112</size>
   <file_id>1607</file_id>
   <upload_url>http://fs19.sluggard.www.dev.uploading.com/upload_file/%3D%3Dgs-FQYCplBXunFVu3BsPj%7CKYuvdqFLPKn8XKIwmWA7Seig5nmXx0iEQsPzGMVOX822z1aap-t%7CketAKnz9BBcj5GnkchBnrDk6YGhYCXjy4wOpl-ngpZmF0A5OgHVT9u87XZUnhK9IvGp4yVO99Tz5vMW8pQ1oUkb7ul3g3QaCuDlAgKhMPNqc</upload_url>
   <progress_url>http://fs19.sluggard.www.dev.uploading.com/api_progress/%3D%3Dgs-FQYCplBXunFVu3BsPj%7CKYuvdqFLPKn8XKIwmWA7Seig5nmXx0iEQsPzGMVOX822z1aap-t%7CketAKnz9BBcj5GnkchBnrDk6YGhYCXjy4wOpl-ngpZmF0A5OgHVT9u87XZUnhK9IvGp4yVO99Tz5vMW8pQ1oUkb7ul3g3QaCuDlAgKhMPNqc</progress_url>
   <session_id>004c20d90c2db36a2f074666c4ec45ed</session_id>               
</file>
```