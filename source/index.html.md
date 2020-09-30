---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell: cURL
  - python: Python
  - ruby: Ruby
  - javascript: Nodejs
  - php: PHP

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Integrity.st API! You can use our API to access VPN API endpoints, which can get information on various VPN accounts and create and delete information from our database

We have language bindings in Shell, Python, Ruby, Nodejs, and PHP! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

### HTTP HEADERS

Parameter | Description | Required
--------- | ----------- | -----------
API-KEY | Enter your api key, 64 bit string | yes
Content-Type | `application/json` | no
Accept | `application/json` | no

note that a few commands such as ipcheck, locations do not require API-KEY.

## Auth
Test user authentication
> To authorize, use this code:

```javascript
var request = require('request');

request.post(
    'https://api.5july.net/1.0/auth',
	{ headers: { "API-KEY": "ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj",
	"Content-Type": "application/json"},
     json: { username: 'test', password: 'testing123' } },
    function (error, response, body) {
        if (!error && response.statusCode == 200) {
            console.log(body)
        } else  { console.log(body); }
    }
);

```

```ruby
require 'net/http'
require 'json'

uri = URI('https://api.5july.net/1.0/auth')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Post.new(uri.path, 'Content-Type' => 'application/json')
req['API-KEY'] = 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'
req.body = {username: 'test', password: 'testing123'}.to_json
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'Content-type': 'application/json',
        'API-KEY': 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'}
payload = { 'username': 'test', 'password': 'testing123'}
req = requests.post("https://api.5july.net/1.0/auth", headers=headers, json=payload)
print(req.json())
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.5july.net/1.0/auth" \
  -X POST \
  -H "API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj" \
  -H "Content-Type: application/json" \
  -d '{"username": "test", "password": "testing123"}'
```

```php
<?php
$data_string = json_encode(array("username" => "test", "password" => "testing123"));

$result = file_get_contents('https://api.5july.net/1.0/auth', null, stream_context_create(array(
'http' => array(
        'method' => 'POST',
        'ignore_errors' => TRUE,
        'header' =>  
        'API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj' . "\r\n"
        .'Content-Type: application/json' . "\r\n"
        .'Content-Length: ' . strlen($data_string) . "\r\n",
        'content' => $data_string,
),
)));
print_r(json_decode($result))
?>
```

> The above command returns JSON structured like this:

```json
{
  "username": "test", 
  "success": "ok", 
  "reseller_id": 1, 
  "created_at": "Wed, 05 Dec 2018 10:31:41 GMT", 
  "enable": true
}
```

### HTTP Request

`POST https://api.5july.net/1.0/auth`

### JSON Parameters

Parameter | Description | Required
--------- | ----------- | -----------
username | enter user username to authenticate with | yes
password | enter user password to authenticate with | yes


<aside class="notice">
You must replace <code>ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj</code> with your personal API key.
</aside>

# User

## Get All Users
```javascript
var request = require('request');

request.get(
    'https://api.5july.net/1.0/user',
        { headers: { "API-KEY": "ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj",
        "Accept": "application/json"},
      },  
    function (error, response, body) {
        if (!error && response.statusCode == 200) {
            console.log(body)
        } else  { console.log(body); }
    }   
);

```

```ruby
require 'net/http'

uri = URI('https://api.5july.net/1.0/user')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Get.new(uri.path, 'Accept' => 'application/json')
req['API-KEY'] = 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'accept': 'application/json',
        'API-KEY': 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'}
req = requests.get("https://api.5july.net/1.0/user", headers=headers)
print(req.json())
```

```shell
curl "https://api.5july.net/1.0/user" \
  -H "API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj" \
  -H  "accept: application/json" 
```

```php
<?php
$result = file_get_contents('https://api.5july.net/1.0/user', null, stream_context_create(array(
'http' => array(
        'method' => 'GET',
        'ignore_errors' => TRUE,
        'header' =>  
        'API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj' . "\r\n"
        .'Accept: application/json' . "\r\n"
),
)));


?>
```

> The above command returns JSON structured like this:

```json
[
  {
    "data": [
      {
        "account_type": 1, 
        "account_typename": "PREMIUM", 
        "created_at": "Wed, 31 Oct 2018 04:41:28 GMT", 
        "enable": true, 
        "reseller_id": 1, 
        "updated_at": "Wed, 31 Oct 2018 06:13:11 GMT", 
        "user_id": 28, 
        "username": "roxyroxy"
      }, 
      {
        "account_type": 1, 
        "account_typename": "PREMIUM", 
        "created_at": "Wed, 31 Oct 2018 04:41:14 GMT", 
        "enable": true, 
        "reseller_id": 1, 
        "updated_at": "Wed, 31 Oct 2018 04:41:14 GMT", 
        "user_id": 27, 
        "username": "vfsw381711"
      }
    ], 
    "max_row_limit_per_page": 10, 
    "rows_on_this_page": 10, 
    "success": "ok", 
    "this_page": 0, 
    "total_pages": 3, 
    "total_rows": 24
  }
]

```

This endpoint retrieves all users.

### HTTP Request

`GET https://api.5july.net/1.0/user`

### URL Parameters

Parameter | Description | Required
--------- | ----------- | -----------
order | DESC or ASC | no
sort | sort result by ["userid", "username", "enable"] | no
page | enter which result page to display | no
search | enter a string to search for username | no


<aside class="notice">
Example URL request with multiple parameters:<br>
https://api.5july.net/1.0/user?sort=userid&order=desc&page=1&search=abc123
</aside>


## Get a Specific User

```javascript
var request = require('request');

request.get(
    'https://api.5july.net/1.0/user/25',
        { headers: { "API-KEY": "ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj",
        "Accept": "application/json"},
      },  
    function (error, response, body) {
        if (!error && response.statusCode == 200) {
            console.log(body)
        } else  { console.log(body); }
    }   
);

```

```ruby
require 'net/http'

uri = URI('https://api.5july.net/1.0/user/25')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Get.new(uri.path, 'Accept' => 'application/json')
req['API-KEY'] = 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'accept': 'application/json',
        'API-KEY': 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'}
req = requests.get("https://api.5july.net/1.0/user/25", headers=headers)
print(req.json())


```

```shell
curl "https://api.5july.net/1.0/user/25" \
-H "API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj" \
-H  "accept: application/json"
```

```php
<?php
$result = file_get_contents('https://api.5july.net/1.0/user/25', null, stream_context_create(array(
'http' => array(
        'method' => 'GET',
        'ignore_errors' => TRUE,
        'header' =>  
        'API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj' . "\r\n"
        .'Accept: application/json' . "\r\n"
),
)));
?>

```

> The above command returns JSON structured like this:

```json
{
  "created_at": "Wed, 31 Oct 2018 04:40:37 GMT", 
  "enable": true, 
  "reseller_id": 1, 
  "reseller_name": "", 
  "updated_at": "Wed, 31 Oct 2018 04:40:37 GMT", 
  "user_id": 25, 
  "username": "heao902376"
}
```

This endpoint retrieves a specific user.


### HTTP Request

`GET https://api.5july.net/user/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to retrieve

## Create a new user

```javascript
var request = require('request');

request.post(
    'https://api.5july.net/1.0/user',
        { headers: { "API-KEY": "ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj",
        "Content-Type": "application/json"},
     json: { password: 'testing123' } },
    function (error, response, body) {
        if (!error && response.statusCode == 200) {
            console.log(body)
        } else  { console.log(body); }
    }   
);

```

```ruby
require 'net/http'
require 'json'

uri = URI('https://api.5july.net/1.0/user')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Post.new(uri.path, 'Content-Type' => 'application/json')
req['API-KEY'] = 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'
req.body = {password: 'testing123'}.to_json
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'Content-type': 'application/json',
        'API-KEY': 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'}
payload = {'password' : 'abc1234'}
req = requests.post("https://api.5july.net/1.0/user", headers=headers, json=payload)
```

```shell
curl "https://api.5july.net/1.0/user" \
  -X POST \
  -H "API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj" \
  -H  "Content-type: application/json" \
  -d '{"password": "abc1234"}'
```

```php
<?php
$data_string = json_encode(array("password" => "abc1234"));

$result = file_get_contents('https://api.5july.net/1.0/user', null, stream_context_create(array(
	'http' => array(
	'method' => 'POST',
	'ignore_errors' => TRUE,
	'header' =>  
	'API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj' . "\r\n"
	.'Content-Type: application/json' . "\r\n"
	.'Content-Length: ' . strlen($data_string) . "\r\n",
	'content' => $data_string,
),
)));

print_r(json_decode($result))
?>
```
> The above command returns JSON structured like this:

```json
{
    "user_id": 29,
    "username": "jlgu468206",
    "password": "abc1234",
    "reseller_id": 1,
    "enable": true,
    "account_type": 1,
    "success": "ok"
}
```

This endpoint create a new user

### HTTP Request

`POST https://api.5july.net/1.0/user`

### json Parameters

Parameter | Description | Required
--------- | ----------- | -----------
password | choose a password for the user | no

<aside class="notice">
an empty json payload will autogenerate a password for you.
</aside>



## Update a specific User
```javascript
var request = require('request');

request.put(
    'https://api.5july.net/1.0/user/40',
        { headers: { "API-KEY": "ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj",
        "Content-Type": "application/json"},
     json: { username: "roxyroxy14", password: 'testing123', enable: 0 } },
    function (error, response, body) {
        if (!error && response.statusCode == 200) {
            console.log(body)
        } else  { console.log(body); }
    }   
);
```

```ruby
require 'net/http'
require 'json'

uri = URI('https://api.5july.net/1.0/user/23')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Put.new(uri.path, 'Content-Type' => 'application/json')
req['API-KEY'] = 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'
req.body = {password: 'abc1234', username: 'Johnny2', enable: 1}.to_json
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'Content-type': 'application/json',
        'API-KEY': 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'}
payload = {'username': 'Johnny2', 'password' : 'abc1234', 'enable': 1}
req = requests.put("https://api.5july.net/user/<userid>", headers=headers, json=payload)
```

```shell
curl "https://api.5july.net/1.0/user/<userid>" \
  -X PUT \
  -H "API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj" \
  -H  "Content-Type: application/json" \
  -d '{"username": "roxyroxy", "password": "abc1234", enable: 1}'
```

```php
<?php
$data_string = json_encode(array("password" => "123456789","username" => "roxyroxy12", "enable" => 0));

$result = file_get_contents('https://api.5july.net/1.0/user/23', null, stream_context_create(array(
'http' => array(
        'method' => 'PUT',
        'ignore_errors' => TRUE,
        'header' =>  
        'API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj' . "\r\n"
        .'Content-Type: application/json' . "\r\n"
        .'Content-Length: ' . strlen($data_string) . "\r\n",
        'content' => $data_string,
),
)));
print_r(json_decode($result))

?>
```

> The above command returns JSON structured like this:

```json
{
    "success": "ok"
}

```

This endpoint update a specific user.

### HTTP Request

`PUT https://api.5july.net/1.0/user/<userid>`

### URL Parameters

Parameter | Description
--------- | -----------
userid | The userid of the user to update

### JSON Parameters

Parameter | Description
--------- | -----------
username | specify new username for the user
password | specify a new password for the user
enable | specifiy 1 to enable and 0 to disable the user





## Delete a Specific User

```javascript
var request = require('request');

request(
    'https://api.5july.net/1.0/user/40',
        { method: 'delete',
                headers: { "API-KEY": "ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj",
        "Accept": "application/json"},
      },  
    function (error, response, body) {
        if (!error && response.statusCode == 200) {
            console.log(body)
        } else  { console.log(body); }
    }   
);
```

```ruby
require 'net/http'

uri = URI('https://api.5july.net/1.0/user/21')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Delete.new(uri.path, 'Accept' => 'application/json')
req['API-KEY'] = 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'accept': 'application/json',
        'API-KEY': 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'}
req = requests.delete("http://127.0.0.1:5000/1.0/user/username", headers=headers)
print(req.json())

```

```shell
curl "https://api.5july.net/1.0/user/<userid>" \
  -X DELETE \
  -H "API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj" \
  -H  "accept: application/json" 
```

```php
<?php
$result = file_get_contents('https://api.5july.net/1.0/user/25', null, stream_context_create(array(
'http' => array(
        'method' => 'DELETE',
        'ignore_errors' => TRUE,
        'header' =>
        'API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj' . "\r\n"
        .'Accept: application/json' . "\r\n"
),
)));

print_r(json_decode($result))

?>
```

> The above command returns JSON structured like this:

```json
{
    "success": "ok"
}
```

This endpoint deletes a specific user.

### HTTP Request

`DELETE https://api.5july.net/1.0/user/<userId>`

### URL Parameters

Parameter | Description
--------- | -----------
userid | The userid of the user to delete

# Stats

## Get all stats

```javascript
var request = require('request');

request.get(
    'https://api.5july.net/1.0/stats/all',
        { headers: { "API-KEY": "ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj",
        "Accept": "application/json"},
      },  
    function (error, response, body) {
        if (!error && response.statusCode == 200) {
            console.log(body)
        } else  { console.log(body); }
    }   
);

```

```ruby
require 'net/http'

uri = URI('https://api.5july.net/1.0/stats/all')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Get.new(uri.path, 'Accept' => 'application/json')
req['API-KEY'] = 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'accept': 'application/json',
        'API-KEY': 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'}
req = requests.get("https://api.5july.net/1.0/Stats/all", headers=headers)
print(req.json())
```

```shell
curl "https://api.5july.net/1.0/stats/all" \
  -H "API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj" \
  -H  "accept: application/json"
```

```php
<?php
$result = file_get_contents('https://api.5july.net/1.0/stats/all', null, stream_context_create(array(
'http' => array(
        'method' => 'GET',
        'ignore_errors' => TRUE,
        'header' =>  
        'API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj' . "\r\n"
        .'Accept: application/json' . "\r\n"
),
)));

print_r(json_decode($result))

?>
```

> The above command returns JSON structured like this:

```json
{
    "tdata": [
        {
            "current_online": 78,
            "premium_online": 71,
            "lex_online": 327,
            "total_user": 24,
            "total_lexuser": 0,
            "total_premium": 24,
            "total_deleted": 1,
            "today_signups": 8,
            "week_signup": 13,
            "avg_user": 4,
            "total_enable": 23,
            "total_disable": 1
        }
    ],
    "data": [
        {
            "users": 23,
            "users_lex": 0,
            "users_premium": 23,
            "deluser": 9999,
            "total_enable": 22,
            "total_disable": 1,
            "month": "2018-October"
        },
        {
            "users": 1,
            "users_lex": 0,
            "users_premium": 1,
            "deluser": 9999,
            "total_enable": 1,
            "total_disable": 0,
            "month": "2018-September"
        }
    ]
}

```

This endpoint display stats for your API account

### HTTP Request

`GET https://api.5july.net/1.0/stats/<option>`

### URL Parameters

Parameter | Description
--------- | -----------
option | all = fetch everything

# OpenVPN

# Wireguard

## Add key
Push an wireguard public key to the server (This should be your public key).
Basically you want to run this on the client side. either in a bashscript. you can see example here: https://wg.beta.5july.net/dl/integrity-wg.sh

> To add key, use this code:

```javascript
var request = require('request');

request.post(
    'https://api.5july.net/1.0/wireguard',
        { headers: { "API-KEY": "ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj",
        "Content-Type": "application/json"},
     json: { username: 'test', password: 'testing123', pubkey: "qPTi/SUqY36cEimdbRraqp4PJcrLIPiKtovaEUPPEFY=" } },
    function (error, response, body) {
        if (!error && response.statusCode == 200) {
            console.log(body)
        } else  { console.log(body); }
    }   
);

```

```ruby
require 'net/http'
require 'json'

uri = URI('https://api.5july.net/1.0/wireguard')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Post.new(uri.path, 'Content-Type' => 'application/json')
req['API-KEY'] = 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'
req.body = {username: 'test', password: 'testing123', pubkey: 'qPTi/SUqY36cEimdbRraqp4PJcrLIPiKtovaEUPPEFY='}.to_json
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'Content-type': 'application/json',
        'API-KEY': 'ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj'}
payload = { 'username': 'demodemo', 'password': 'abc1234', 'pubkey': 'qPTi/SUqY36cEimdbRraqp4PJcrLIPiKtovaEUPPEFY='}
req = requests.post("https://api.5july.net/1.0/wireguard", headers=headers, json=payload)
print(req.json())
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.5july.net/1.0/wireguard" \
  -X POST \
  -H "API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj" \
  -H "Content-Type: application/json" \
  -d '{"username": "demodemo", "password": "abc1234", "pubkey": "qPTi/SUqY36cEimdbRraqp4PJcrLIPiKtovaEUPPEFY="}'
```

```php
<?php
$data_string = json_encode(array("username" => "test", "password" => "testing123", "pubkey" => "qPTi/SUqY36cEimdbRraqp4PJcrLIPiKtovaEUPPEFY="));

$result = file_get_contents('https://api.5july.net/1.0/wireguard', null, stream_context_create(array(
'http' => array(
        'method' => 'POST',
        'ignore_errors' => TRUE,
        'header' =>
        'API-KEY: ibpebspx0ihcgwvbgms27q-89xk5hkelc63db71vpwbcy70jlwi.61s0jvh1j.lj' . "\r\n"
        .'Content-Type: application/json' . "\r\n"
        .'Content-Length: ' . strlen($data_string) . "\r\n",
        'content' => $data_string,
),
)));
print_r(json_decode($result))
?>
```

> The above command returns JSON structured like this:

```json
{
  "success": "ok", 
  "dns": "1.1.1.1", 
  "ipv4": "10.0.0.4/24", 
  "ipv6": "fdab:1337:1337:1::4/64"
}

```

### HTTP Request

`POST https://api.5july.net/1.0/wireguard`


## List keys


> The above command returns JSON structured like this:

```json
[
  {
    "ipv4": "10.0.0.25/32", 
    "ipv6": "fdab:1337:1337:1::25/128", 
    "public_key": "qDpB/McJDkL9YuNINuuvupB1tADJrva/g/phwfQrWBw="
  }, 
  {
    "ipv4": "10.0.0.28/32", 
    "ipv6": "fdab:1337:1337:1::28/128", 
    "public_key": "SN5qj4uyO9JUcqLhmevSTfxm3ATwud3TDi8xG5pjEwE="
  }
]
```

### HTTP Request

`GET https://api.5july.net/1.0/wireguard`


## Delete key
This command is used to delete an public key from the servers

### HTTP Request

`DELETE https://api.5july.net/1.0/wireguard/<id>`


#IP Check

##ipcheck

```javascript
var request = require('request');

request.get(
    'https://api.5july.net/1.0/ipcheck',
        "Accept": "application/json"},
      },  
    function (error, response, body) {
        if (!error && response.statusCode == 200) {
            console.log(body)
        } else  { console.log(body); }
    }   
);

```

```ruby
require 'net/http'

uri = URI('https://api.5july.net/1.0/ipcheck')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Get.new(uri.path, 'Accept' => 'application/json')
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'accept': 'application/json'}
req = requests.get("https://api.5july.net/1.0/ipcheck", headers=headers)
print(req.json())
```

```shell
curl "https://api.5july.net/1.0/ipcheck" \
  -H  "accept: application/json"
```

```php
<?php
$result = file_get_contents('https://api.5july.net/1.0/ipcheck', null, stream_context_create(array(
'http' => array(
        'method' => 'GET',
        'ignore_errors' => TRUE,
        'header' =>
        'Accept: application/json' . "\r\n"
),
)));

print_r(json_decode($result))

?>
```


> The above command returns JSON structured like this:

```json
{
"ip": "127.0.0.1", 
"connected": false
}

```

### HTTP Request

`GET https://api.5july.net/1.0/ipcheck`


# Locations

## locations

```javascript
var request = require('request');

request.get(
    'https://api.5july.net/1.0/locations',
        "Accept": "application/json"},
      },  
    function (error, response, body) {
        if (!error && response.statusCode == 200) {
            console.log(body)
        } else  { console.log(body); }
    }   
);

```

```ruby
require 'net/http'

uri = URI('https://api.5july.net/1.0/locations')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Get.new(uri.path, 'Accept' => 'application/json')
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'accept': 'application/json'}
req = requests.get("https://api.5july.net/1.0/locations", headers=headers)
print(req.json())
```

```shell
curl "https://api.5july.net/1.0/locations" \
  -H  "accept: application/json"
```

```php
<?php
$result = file_get_contents('https://api.5july.net/1.0/locations', null, stream_context_create(array(
'http' => array(
        'method' => 'GET',
        'ignore_errors' => TRUE,
        'header' =>
        'Accept: application/json' . "\r\n"
),
)));

print_r(json_decode($result))

?>
```


> The above command returns JSON structured like this:

```json
[
  {
    "city": "Malmo", 
    "country": "Sweden", 
    "dest_addr": "155.4.89.133", 
    "hostname": "seML", 
    "port": 48574, 
    "public_key": "ipW9/ysMc9vQbg/x7WK/udnl06+NJioWZZ4XIqz4PQY="
  }
]

```

### HTTP Request

`GET https://api.5july.net/1.0/locations`

