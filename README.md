## ****Curl PHP Class****

Класс PHP для простых и удобных запросов cURL.

## **Функции**

- Инициализирует сеанс cURL с параметрами по умолчанию, такими как CURLOPT_RETURNTRANSFER, для которых задано значение true.
- Позволяет устанавливать и получать параметры cURL
- Предоставляет методы для общих параметров cURL, таких как настройка файлов cookie, проверка SSL, заголовки, отслеживание местоположения, referer, user agent, post поля и многое другое.

## **Применение**

```php
$curl = Curl::app("https://www.example.com");
```

Чтобы установить параметры:

```php
$curl->set(CURLOPT_COOKIEFILE, '/path/to/cookie/file');
```

Чтобы получить параметры:

```
$value = $curl->get(CURLOPT_COOKIEFILE);
```

Доступные методы:

- cookie
- ssl
- headers
- follow
- referer
- userAgent
- postFields
- execute

## **Пример**

```php
<?php
include_once('lib/Curl.php');
include_once('api-key.php');
$json = '{"model": "text-davinci-003", "prompt": "Say this is a test", "temperature": 0, "max_tokens": 7}';
$c = Curl::app('https://api.openai.com')
    ->add_headers([
        "Authorization: Bearer " . API_KEY,
        "Content-Type: application/json",
    ])
    ->set(CURLOPT_POST, 1)
    ->set(CURLOPT_POSTFIELDS, $json);
$response = $c->request('/v1/completions');
var_dump($response);
```

## **Примечание**

- Дополнительную информацию об API OpenAI и о том, как получить к нему доступ, можно найти на их веб-сайте по адресу https://beta.openai.com/docs/api-reference/introduction
- Все параметры cURL можно найти в **[официальной документации cURL](https://curl.haxx.se/libcurl/c/curl_easy_setopt.html)**
