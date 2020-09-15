# Routing

#### Basic Routing

You will define all of the routes for your application in the `routes.php` file. The most basic MiniPHP routes simply accept a URI and a Closure:

```php
$app->get('foo', function () {
    return 'Hello World';
});

$app->post('foo', function () {
    //
});
```

#### Available Router Methods
The router allows you to register routes that respond to any HTTP verb:

```php
$app->get($uri, $callback);
$app->post($uri, $callback);
$app->put($uri, $callback);
$app->delete($uri, $callback);
$app->map($uri, $callback , [/* Array of methods */]);
```

#### Route Parameters
> Comming Soon...


#### Named Route
> Comming Soon...