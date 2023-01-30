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
$curl = Curl::app("https://www.example.com");
$curl->ssl(false)
     ->headers(true)
     ->follow(true)
     ->userAgent("My User Agent")
     ->postFields(array("field1" => "value1", "field2" => "value2"))
     ->execute();
$response = $curl->get(CURLOPT_RETURNTRANSFER);
```

## **Примечание**

- Обязательно закройте сеанс cURL после использования с **`$curl->__destruct()`** объектом или путем его отмены.
- Все параметры cURL можно найти в **[официальной документации cURL](https://curl.haxx.se/libcurl/c/curl_easy_setopt.html)**
