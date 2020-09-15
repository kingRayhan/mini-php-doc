# Installation

#### System Requirements
- Web server with URL rewriting
- PHP 7.4 or newer
- OpenSSL PHP Extension
- PDO PHP Extension


## Installing Lumen

**Step 1**

Clone the repo

```bash
git clone https://github.com/kingRayhan/mini-php.git MyCoolProject
```

Install dependencies

```bash
composer install
```

### Serving Your Application
To serve your project locally you may use the built-in PHP development server:

```bash
php -S localhost:8000
```

Or any php local server application like [Xampp](https://www.apachefriends.org/index.html).


### Configuration

All of the configuration options for the `MiniPHP` framework are stored in the `.env` file. Once `MiniPHP` is installed, you should also configure your local environment.

Copy the `.env.example` to make `.env` file and change values as your need

```env
DB_DRIVER=
DB_HOST=
DB_NAME=
DB_USER=
DB_PASS=
```