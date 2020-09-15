## Flash message

`flash()` method will help you create and get flash message. Is for temporary, once the message shown to client then immidiately remove from session.

The global `flash()` method is a object of Flash class.

### Flash Class Definition

```php
class Flash{
    public add(key: string, message: string): void
    public has(key: string): bool
    public get(key: string): string|mixed
    public clear(): void
}
```


<br/>

### Examples

```php
$app->get('/test', function () {
    return flash()->add('error', 'You have some validation error.!!');
});
```

**In twig template**

```html
{% if flash()->has('error') %}
    <div class="error">
        {{ flash()->get('error') }}
    </div>
{% endif %}
```