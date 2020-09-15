# Welcome
MiniPHP is a PHP micro framework that helps you quickly write simple yet powerful web applications and APIs. At its core, MiniPHP is a dispatcher that receives an HTTP request, invokes an appropriate callback routine, and returns an HTTP response. That’s it.

## What’s the point?

MiniPHP is an ideal tool to create APIs that consume, repurpose, or publish data. MiniPHP is also a great tool for rapid prototyping. Heck, you can even build full-featured web applications with user interfaces. More importantly, MiniPHP is super fast and has very little code. In fact, you can read and understand its source code in only an afternoon!

You don’t always need a kitchen-sink solution like [Symfony](https://symfony.com/) or [Laravel](https://laravel.com/). These are great tools, for sure. But they are often overkill. Instead, MiniPHP provides only a minimal set of tools that do what you need and nothing else.


## Request and response
When you build a MiniPHP app, you are often working directly with Request and Response objects. These objects represent the actual HTTP request received by the web server and the eventual HTTP response returned to the client.