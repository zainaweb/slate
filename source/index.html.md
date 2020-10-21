---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  # - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://sate.com.au'></a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the Sate API! This document describes how 3rd party applications can integrate with Sate, to create and monitor a wealth of services that we offer.

We currently have language bindings in Shell! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

If you would like to request any additional bindings, then please contact the Technology Team at tech@sate.com.au and we will aim to add them in the near future.

# Authentication

> To authorize, use this code:

```ruby
require 'sate'

api = Sate::APIClient.authorize!('your_api_key')
```

```python
import sate

api = sate.authorize('your_api_key')
```

```shell
# With shell, you can just pass the correct header with each request
curl --header "Authorization: Bearer [YOUR_TOKEN]" https://app.sate.com.au/api/v1/
   
```

```javascript
const sate = require('yourapikey');

let api = sate.authorize('yourapikey');
```

> Make sure to replace `your api key` with your API key.

Sate uses API Bearer Tokens to permit access to our API. You can register for a new Lendflow API key on our [client portal](http://sate.com.au) in less than 60 seconds.

Sate expects for the Bearer Token to be included in all API requests made to the server in the header that takes the following form:

`Authorization: Bearer [YOUR_TOKEN]`

<aside class="notice">
You must replace <code>[YOUR_TOKEN]</code> with your personal API key.
</aside>

# Application

## Apply for Capital

```ruby
require 'sate'

api = Sate::APIClient.authorize!('your_api_key')
api.sate.get
```

```python
import sate

api = sate.authorize('your_api_key')
api.sate.get()
```

```shell
curl --header "Content-Type: application/json" \
  --header "Authorization: Bearer [YOUR_TOKEN]" \
  --request POST \
  --data '{
    "sandbox": "false",
    "uuid": "CUSTOM-IDENTIFIER-123456789",
    "dba_name": "Jonathan Parks Travel",
    "first_name": "Joe",
    "last_name": "Client",
    "phone_number":0404 888 888,
    "email_address": "jclient@afsllicencedco.com.au",
    "owner_date_of_birth": "01/12/1982",
    "owner_home_address": "12 Home Street",
    "owner_city": "Sydney",
    "owner_state": "NSW",
    "owner_postcode": 2000,
    "owner_tfn": 123321232,
    "use_of_funds": "Own use",
    "amount_needed": 10000,
    "business_entity_type": "Travel Agency",
    "business_start_date": "22/12/2000",
    "business_address": "21 George Street",
    "business_city": "Sydney",
    "business_state": "NSW",
    "business_postcode": 2000,
    "number_of_owners": 1,
    "other_owners": [
        {
            "first_name": "Jack",
            "last_name": "Palance",
            "address": "12 Western st",
            "city": "Sydney",
            "state": "NSW",
            "postcode": 2000,
            "tfn": 432343234,
            "dob": "02/02/1981",
            "ownership": "50"
        }
    ]
  }' https://app.sate.com.au/api/v1/application
 


```

```javascript
const sate = require('sate');

let api = sate.authorize('yourapikey');
let api = api.application.get();
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "application_identifier": "6ojd9c373-2v87-4177-8b189-c2w8aa24g221"
    }
}
```

This endpoint, allows registered users, to efficiently and securely submit a request for funding in the Sate system.

### HTTP Request

`POST https://app.sate.com.au/api/v1/application`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
sandbox	| false	| Perform a test run.
uuid | false | Custom identifier to attach to application.
dba_name	| true	| Business name of the company applying for funding.
first_name | true	| First name of the primary business holder.
last_name	| true	| Last name of the primary business holder.
phone_number	| true	| Phone number of the primary business owner.
email_address	| true	| Email address of the primary business owner.
owner_date_of_birth	| true | Date of birth of the primary business owner.
owner_home_address	| true | First line of address of the primary business owner.
owner_city	| true	| The city of the primary business owner.
owner_state	| true	| The state of the primary business owner.
owner_postcode	| true	| The postcode of the primary business owner.
owner_tfn |	true	| The tax file number of the primary business owner.
use_of_funds	| true	| The reason the business is applying for funding.
amount_needed	| true	| The requested amount to be funded.
business_entity_type	| true	| The type of business.
business_start_date	| true	| The date the business was started.
business_address	| true	| The first line of the business address.
business_city	| true	| The city that the business is regestered in.
business_state	| true	| The state that the business is regestered in.
business_postcode	| true	| The post code that the business is regestered in.
number_of_owners	| false	| The number of business owners.
other_owners.*.first_name	| false	| The first name of the additional business owner.
other_owners.*.last_name	| false	| The last name of the additional business owner.
other_owners.*.address	| false	| The first line of address of the additonal business owner.
other_owners.*.city	| false	| The city of the additional business owner.
other_owners.*.state	| false	| The state of the additonal business owner.
other_owners.*.postcode	| false	| The post code of the additonal business owner.
other_owners.*.tfn	| false	| The tax file number of the additonal business owner.
other_owners.*.dob	| false	| The date of birth of the additional business owner.
other_owners.*.ownership	| false	| The percentage of onwership of the additional business owner.


<aside class="success">
Remember — all requests made to the API, need to be authenticated.
</aside>

<!-- ## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete -->

