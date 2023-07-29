---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell
  # - ruby
  # - python
  # - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the SwapWallet API
---

# پیش‌گفتار
این صفحه حاوی مستندات مربوط به API [سواپ‌ولت]() است که به شما کمک می‌کند تا بتوانید بیشترین بهره را از حساب کاربری سواپ‌ولت خود ببرید. (نیاز داره که یه خلاصه‌ای از اینکه چه کارهایی می‌تونن باهاش انجام بدن رو داشته باشه)

لطفاً پیش از استفاده از APIها، اطمینان حاصل کنید که [قوانین استفاده از سواپ‌ولت]() و هم‌چنین [قوانین استفاده از API سواپ‌ولت]() را مطالعه کرده و پذیرفته‌اید. همچنین با عضویت در [کانال رسمی اطلاع‌رسانی سواپ‌ولت]()، به صورت مستمر تغییرات ایجاد شده در APIها را رصد کنید تا در صورت نیاز، تغییرات لازم را اعمال کنید.

پیشنهاد می‌کنیم که در کدهای خود، راه‌هایی برای مواجهه با انواع خطاها، که در ادامه توضیح داده می‌شوند، در نظر بگیرید تا بتوانید عکس‌العمل مناسبی در هنگام برخورد با این خطاها داشته باشید.
اگر برای اولین بار قصد استفاده از APIها سواپ‌ولت را دارید، پیشنهاد می‌کنیم ابتدا قسمت [راهنمای شروع به کار با API]() را بررسی کنید.

# دریافت توکن

برای استفاده از APIها، نیاز دارید تا ابتدا توکن خود را از طریق [بات تلگرامی سواپ‌ولت]() دریافت کنید. برای این کار، به قسمت **`تنظیمات`** &larr; **`توسعه‌دهندگان`** &larr; **`ایجاد کلید توسعه`** بروید؛ کلید خود را از پیام داخل بات دریافت کنید و در ادامه برای استفاده از APIها، از این توکن استفاده کنید.

همچنین برای منقضی کردن کردن توکن خود، می‌توانید در [بات]() به قسمت **`تنظیمات`** &larr; **`توسعه‌دهندگان`** &larr; **`منقضی کردن توکن`** بروید؛ با این کار توکن قبلی شما منقضی می‌شود و یک توکن جدید جایگزین قبلی در پیام ارسالی می‌شود. 

این توکن باید در Header درخواست‌های شما به صورت ‍‍`Authorization: ‌Bearer YourToken` ارسال شود.

<aside class="notice">
 لطفاً تحت هیچ شرایطی توکن خود را با دیگران به اشتراک نگذارید؛ در صورت اشتراک، مسئولیت هرگونه سواستفاده از این کلید بر عهده‌ی شما می‌باشد.

همچنین در صورت دسترسی تصادفی سایر افراد به توکن مربوط به شما، فوراً اقدام به منقضی کردن کرده و از یک توکن جدید برای ادامه استفاده کنید.
</aside>

پیشنهاد می‌کنیم تنها در صورتی که با روش‌های امن ذخیره‌ی گذرواژه در کد آشنایی دارید، اقدام به استفاده از توکن بکنید.

<!-- ```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

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
curl "http://example.com/api/kittens/2" \
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
curl "http://example.com/api/kittens/2" \
  -X DELETE \
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
ID | The ID of the kitten to delete
 -->
