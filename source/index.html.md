---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell: cURL
  - python
  - ruby
  - javascript: nodejs
  - php

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Integrity.st API! You can use our API to access VPN API endpoints, which can get information on various VPN accounts and create and delete information from our database

We have language bindings in Shell, Ruby, Python, and PHP! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

## Auth
Test user authentication
> To authorize, use this code:

```javascript
var request = require('request');

request.post(
    'https://api2.integrity.st/1.0/Auth',
	{ headers: { "API-KEY": "356a192b7913b04c54574d18c28d46e6395428ab",
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

uri = URI('https://api2.integrity.st/1.0/Auth')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Post.new(uri.path, 'Content-Type' => 'application/json')
req['API-KEY'] = '356a192b7913b04c54574d18c28d46e6395428ab'
req.body = {username: 'test', password: 'testing123'}.to_json
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'Content-type': 'application/json',
	'accept': 'application/json',
        'API-KEY': '356a192b7913b04c54574d18c28d46e6395428ab'}
payload = { 'username': 'demodemo', 'password': 'abc1234'}
req = requests.get("https://api2.integrity.st/1.0/Auth", headers=headers, json=payload)
print(req.json())
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api2.integrity.st/1.0/Auth" \
  -X POST \
  -H "API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab" \
  -H "Content-Type: application/json" \
  -H "accept: application/json" \
  -d '{"username": "demodemo", "password": "abc1234"}'
```

```php
<?php
$data_string = json_encode(array("username" => "test", "password" => "testing123"));

$result = file_get_contents('https://api2.integrity.st/1.0/Auth', null, stream_context_create(array(
'http' => array(
        'method' => 'POST',
        'ignore_errors' => TRUE,
        'header' =>  
        'API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab' . "\r\n"
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
    "success": ok,
    "user_id": 2
  } 
```

### HTTP Request

`POST https://api2.integrity.st/1.0/Auth`

### JSON Parameters

Parameter | Description | Required
--------- | ----------- | -----------
username | enter user username to authenticate with | yes
password | enter user password to authenticate with | yes


<aside class="notice">
You must replace <code>356a192b7913b04c54574d18c28d46e6395428ab</code> with your personal API key.
</aside>

# User

## Get All Users
```javascript
var request = require('request');

request.get(
    'https://api2.integrity.st/1.0/User',
        { headers: { "API-KEY": "356a192b7913b04c54574d18c28d46e6395428ab",
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

uri = URI('https://api2.integrity.st/1.0/User')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Get.new(uri.path, 'Accept' => 'application/json')
req['API-KEY'] = '356a192b7913b04c54574d18c28d46e6395428ab'
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'accept': 'application/json',
        'API-KEY': '356a192b7913b04c54574d18c28d46e6395428ab'}
req = requests.get("https://api2.integrity.st/1.0/User", headers=headers)
print(req.json())
```

```shell
curl "https://api2.integrity.st/1.0/User" \
  -H "API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab" \
  -H  "accept: application/json" 
```

```php
<?php
$result = file_get_contents('https://api2.integrity.st/1.0/User', null, stream_context_create(array(
'http' => array(
        'method' => 'GET',
        'ignore_errors' => TRUE,
        'header' =>  
        'API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab' . "\r\n"
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

`GET https://api2.integrity.st/1.0/User`

### URL Parameters

Parameter | Description | Required
--------- | ----------- | -----------
order | DESC or ASC | no
sort | sort result by ["userid", "username", "enable"] | no
page | enter which result page to display | no
search | enter a string to search for username | no


<aside class="notice">
Example URL request with multiple parameters:<br>
https://api2.integrity.st/1.0/User?sort=userid&order=desc&page=1&search=user
</aside>


## Get a Specific User

```javascript
var request = require('request');

request.get(
    'https://api2.integrity.st/1.0/User/25',
        { headers: { "API-KEY": "356a192b7913b04c54574d18c28d46e6395428ab",
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

uri = URI('https://api2.integrity.st/1.0/User/25')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Get.new(uri.path, 'Accept' => 'application/json')
req['API-KEY'] = '356a192b7913b04c54574d18c28d46e6395428ab'
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'accept': 'application/json',
        'API-KEY': '356a192b7913b04c54574d18c28d46e6395428ab'}
req = requests.get("https://api2.integrity.st/1.0/User/25", headers=headers)
print(req.json())


```

```shell
curl "https://api2.integrity.st/1.0/User/25" \
-H "API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab" \
-H  "accept: application/json"
```

```php
<?php
$result = file_get_contents('https://api2.integrity.st/1.0/User/25', null, stream_context_create(array(
'http' => array(
        'method' => 'GET',
        'ignore_errors' => TRUE,
        'header' =>  
        'API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab' . "\r\n"
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

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET https://api2.integrity.st/User/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to retrieve

## Create a new user

```javascript
var request = require('request');

request.post(
    'https://api2.integrity.st/1.0/User',
        { headers: { "API-KEY": "356a192b7913b04c54574d18c28d46e6395428ab",
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

uri = URI('https://api2.integrity.st/1.0/User')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Post.new(uri.path, 'Content-Type' => 'application/json')
req['API-KEY'] = '356a192b7913b04c54574d18c28d46e6395428ab'
req.body = {password: 'testing123'}.to_json
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'accept': 'application/json',
        'Content-type': 'application/json',
        'API-KEY': '356a192b7913b04c54574d18c28d46e6395428ab'}
payload = {'password' : 'abc1234'}
req = requests.post("https://api2.integrity.st/1.0/User", headers=headers, json=payload)
```

```shell
curl "https://api2.integrity.st/1.0/User" \
  -X POST \
  -H "API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab" \
  -H  "accept: application/json" \
  -H  "Content-type: application/json" \
  -d '{"password": "abc1234"}'
```

```php
<?php
$data_string = json_encode(array("password" => "abc1234"));

$result = file_get_contents('https://api2.integrity.st/1.0/User', null, stream_context_create(array(
	'http' => array(
	'method' => 'POST',
	'ignore_errors' => TRUE,
	'header' =>  
	'API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab' . "\r\n"
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

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE https://api.integrity.st/1.0/User`

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
    'https://api2.integrity.st/1.0/User/40',
        { headers: { "API-KEY": "356a192b7913b04c54574d18c28d46e6395428ab",
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

uri = URI('https://api2.integrity.st/1.0/User/23')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Put.new(uri.path, 'Content-Type' => 'application/json')
req['API-KEY'] = '356a192b7913b04c54574d18c28d46e6395428ab'
req.body = {password: 'abc1234', username: 'Johnny2', enable: 1}.to_json
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'accept': 'application/json',
        'Content-type': 'application/json',
        'API-KEY': '356a192b7913b04c54574d18c28d46e6395428ab'}
payload = {'username': 'Johnny2', 'password' : 'abc1234', 'enable': 1}
req = requests.put("https://api2.integrity.st/User/<userid>", headers=headers, json=payload)
```

```shell
curl "https://api.integrity.st/1.0/User/<userid>" \
  -X PUT \
  -H "API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab" \
  -H  "accept: application/json" \
  -H  "Content-Type: application/json" \
  -d '{"username": "roxyroxy", "password": "abc1234", enable: 1}'
```

```php
<?php
$data_string = json_encode(array("password" => "123456789","username" => "roxyroxy12", "enable" => 0));

$result = file_get_contents('https://api2.integrity.st/1.0/User/23', null, stream_context_create(array(
'http' => array(
        'method' => 'PUT',
        'ignore_errors' => TRUE,
        'header' =>  
        'API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab' . "\r\n"
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

`PUT https://api.integrity.st/1.0/User/<userid>`

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
    'https://api2.integrity.st/1.0/User/40',
        { method: 'delete',
                headers: { "API-KEY": "356a192b7913b04c54574d18c28d46e6395428ab",
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

uri = URI('https://api2.integrity.st/1.0/User/21')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Delete.new(uri.path, 'Accept' => 'application/json')
req['API-KEY'] = '356a192b7913b04c54574d18c28d46e6395428ab'
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'accept': 'application/json',
        'API-KEY': '356a192b7913b04c54574d18c28d46e6395428ab'}
req = requests.delete("http://127.0.0.1:5000/1.0/User/username", headers=headers)
print(req.json())

```

```shell
curl "https://api.integrity.st/1.0/User/<userid>" \
  -X DELETE \
  -H "API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab" \
  -H  "accept: application/json" 
```

```php
<?php
$result = file_get_contents('https://api2.integrity.st/1.0/User/25', null, stream_context_create(array(
'http' => array(
        'method' => 'DELETE',
        'ignore_errors' => TRUE,
        'header' =>
        'API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab' . "\r\n"
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

`DELETE https://api.integrity.st/1.0/User/<userId>`

### URL Parameters

Parameter | Description
--------- | -----------
userid | The userid of the user to delete

# Stats

## Get all stats

```javascript
var request = require('request');

request.get(
    'https://api2.integrity.st/1.0/Stats/all',
        { headers: { "API-KEY": "356a192b7913b04c54574d18c28d46e6395428ab",
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

uri = URI('https://api2.integrity.st/1.0/Stats/all')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Get.new(uri.path, 'Accept' => 'application/json')
req['API-KEY'] = '356a192b7913b04c54574d18c28d46e6395428ab'
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'accept': 'application/json',
        'API-KEY': '356a192b7913b04c54574d18c28d46e6395428ab'}
req = requests.get("https://api2.integrity.st/1.0/Stats/all", headers=headers)
print(req.json())
```

```shell
curl "https://api2.integrity.st/1.0/Stats/all" \
  -H "API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab" \
  -H  "accept: application/json"
```

```php
<?php
$result = file_get_contents('https://api2.integrity.st/1.0/Stats/all', null, stream_context_create(array(
'http' => array(
        'method' => 'GET',
        'ignore_errors' => TRUE,
        'header' =>  
        'API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab' . "\r\n"
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

`GET https://api2.integrity.st/1.0/Stats/<option>`

### URL Parameters

Parameter | Description
--------- | -----------
option | all = fetch everything

# OpenVPN

# Wireguard

## wireguard
Create an wireguard pubkey
> To add key, use this code:

```javascript
var request = require('request');

request.post(
    'https://api2.integrity.st/1.0/Wireguard',
        { headers: { "API-KEY": "356a192b7913b04c54574d18c28d46e6395428ab",
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

uri = URI('https://api2.integrity.st/1.0/Wireguard')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Post.new(uri.path, 'Content-Type' => 'application/json')
req['API-KEY'] = '356a192b7913b04c54574d18c28d46e6395428ab'
req.body = {username: 'test', password: 'testing123', pubkey: 'qPTi/SUqY36cEimdbRraqp4PJcrLIPiKtovaEUPPEFY='}.to_json
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'Content-type': 'application/json',
        'accept': 'application/json',
        'API-KEY': '356a192b7913b04c54574d18c28d46e6395428ab'}
payload = { 'username': 'demodemo', 'password': 'abc1234', 'pubkey': 'qPTi/SUqY36cEimdbRraqp4PJcrLIPiKtovaEUPPEFY='}
req = requests.get("https://api2.integrity.st/1.0/Wireguard", headers=headers, json=payload)
print(req.json())
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api2.integrity.st/1.0/Wireguard" \
  -X POST \
  -H "API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab" \
  -H "Content-Type: application/json" \
  -H "accept: application/json" \
  -d '{"username": "demodemo", "password": "abc1234", "pubkey": "qPTi/SUqY36cEimdbRraqp4PJcrLIPiKtovaEUPPEFY="}'
```

```php
<?php
$data_string = json_encode(array("username" => "test", "password" => "testing123", "pubkey" => "qPTi/SUqY36cEimdbRraqp4PJcrLIPiKtovaEUPPEFY="));

$result = file_get_contents('https://api2.integrity.st/1.0/Wireguard', null, stream_context_create(array(
'http' => array(
        'method' => 'POST',
        'ignore_errors' => TRUE,
        'header' =>
        'API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab' . "\r\n"
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
    "success": ok, 
    "user_id": 2
  }   
```

### HTTP Request

`POST https://api2.integrity.st/1.0/Wireguard`




#IP Check

##ipcheck

```javascript
var request = require('request');

request.get(
    'https://api2.integrity.st/1.0/Ipcheck',
        { headers: { "API-KEY": "356a192b7913b04c54574d18c28d46e6395428ab",
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

uri = URI('https://api2.integrity.st/1.0/Ipcheck')
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true
req = Net::HTTP::Get.new(uri.path, 'Accept' => 'application/json')
req['API-KEY'] = '356a192b7913b04c54574d18c28d46e6395428ab'
res = http.request(req)
puts "#{res.body}"

```

```python
import requests

headers = {'user-agent': 'python script',
        'accept': 'application/json',
        'API-KEY': '356a192b7913b04c54574d18c28d46e6395428ab'}
req = requests.get("https://api2.integrity.st/1.0/Ipcheck", headers=headers)
print(req.json())
```

```shell
curl "https://api2.integrity.st/1.0/Ipcheck" \
  -H "API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab" \
  -H  "accept: application/json"
```

```php
<?php
$result = file_get_contents('https://api2.integrity.st/1.0/Ipcheck', null, stream_context_create(array(
'http' => array(
        'method' => 'GET',
        'ignore_errors' => TRUE,
        'header' =>
        'API-KEY: 356a192b7913b04c54574d18c28d46e6395428ab' . "\r\n"
        .'Accept: application/json' . "\r\n"
),
)));

print_r(json_decode($result))

?>
```


> The above command returns JSON structured like this:

```json
{"ip": "127.0.0.1", "connected": false}

```

### HTTP Request

`GET https://api2.integrity.st/1.0/Ipcheck`

