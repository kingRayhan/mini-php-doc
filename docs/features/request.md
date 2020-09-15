# HTTP Requests

## Accessing The Request
To obtain an instance of the current HTTP request via dependency injection, you should type-hint the `MiniPHP\Request` class on your controller method. The current request instance will automatically be injected by the service container on method first parameter:

**In route callback closure**
```php
use MiniPHP\Request;
use MiniPHP\Response;

$app->get('/test', function (Request $request, Response $response) {
    $name = $request->query('name');

    //
});
```

**In controller method**
```php
<?php
namespace MiniPHP\Controllers;

use MiniPHP\Request;
use MiniPHP\Response;

class HomeController
{
    public function index(Request $request, Response $response)
    {
        $name = $request->query('name');

        //
    }
}
```


### The `Request` object


```php
class Request{
    public all(): array
    public only(array $keys): array
    public except(array $keys): array
    public query([, string $key]): string
    public method(): string
    public path(): string
    public protocol(): string
    public host(): string
    public fullPUrl(): string
}
```