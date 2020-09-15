# HTTP Responses

#### Basic Responses

Of course, all routes and controllers should return some kind of response to be sent back to the user's browser. `MiniPHP` provides several different ways to return responses. The most basic response is simply returning a string from a route or controller:

```php
$app->get('/test', function () {
    return "Hello Mini";
});
```
The given string will automatically be converted into an HTTP response by the framework.


<br />
<br />

### `Response` Objects
All routes and controller actions, you will be returning a full `MiniPHP\Response` instance in second parameter. Returning a full Response instance allows you to customize the response's `HTTP` status code and headers.

On the other hand you can get access `Response` object by global `response()` function.

```php
Response{
    public getBody(): mixed
    public setBody($data): Response
    public withJSON($data): Response
    public withStatus($data): Response
    public getStatusCode($data): Response
    public view($template, array $payload = []): string
}
```

<br/><br/><br/>


#### Json respons

```php
$app->get('/test', function () {
    $cats = [
        ["id" => "1", "name" => 'eni'],
        ["id" => "2", "name" => 'mini'],
        ["id" => "3", "name" => 'bini'],
    ]; // There are my three pet cats 😘

    return response()->withJSON($cats);
});


// OR

$app->get('/test', function (Request $request, Response $response) {
    $cats = [
        ["id" => "1", "name" => 'eni'],
        ["id" => "2", "name" => 'mini'],
        ["id" => "3", "name" => 'bini'],
    ]; // There are my three pet cats 😘

    return $response->withJSON($cats);
});
```


#### Set StatusCode to respons

```php
use MiniPHP\StatusCodes;
use MiniPHP\Request;
use MiniPHP\Response;

$app->get('/test', function (Request $request, Response $response) {
    $cats = [
        ["id" => "1", "name" => 'eni'],
        ["id" => "2", "name" => 'mini'],
        ["id" => "3", "name" => 'bini'],
    ]; // There are my three pet cats 😘

    return $response
            ->withJSON($cats)
            ->withStatus(StatusCodes::HTTP_OK);
});
```


### Render template

```php
$app->get('/test', function () {
    $cats = [
        ["id" => "1", "name" => 'eni'],
        ["id" => "2", "name" => 'mini'],
        ["id" => "3", "name" => 'bini'],
    ]; // There are my three pet cats 😘

    return response()->view('welcome' , ['cats' => cats]);
});
```