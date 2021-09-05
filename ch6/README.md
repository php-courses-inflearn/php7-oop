# PHP 7+ Blog Application Examples

* *php >= 7.4*
* Extended Coding Style: [PSR-12](https://www.php-fig.org/psr/psr-12/)

## Branches

* [Beginning](https://github.com/pronist/phpblog/tree/beginning) - **Classic - Legacy**
* [Basic](https://github.com/pronist/phpblog/tree/basic) - **VC(View, Controller) - Functional**
* [Intermediate](https://github.com/pronist/phpblog/tree/intermediate) - **MVC(Model, View, Controller) - OOP**

## Getting started

```bash
# PHP Built-in Server
php -S localhost:8080 -t public
```

## Database (MySQL)

```sql
CREATE DATABASE phpblog;

use phpblog;

CREATE TABLE sessions (
    `id` VARCHAR(255) UNIQUE NOT NULL,
    `payload` TEXT,
    `created_at` TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    `updated_at` TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

CREATE TABLE users (
    `id` INT PRIMARY KEY AUTO_INCREMENT,
    `email` VARCHAR(255) UNIQUE NOT NULL,
    `password` VARCHAR(255) NOT NULL,
    `created_at` TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    `updated_at` TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

CREATE TABLE posts (
    `id` INT AUTO_INCREMENT PRIMARY KEY,
    `user_id` INT NOT NULL,
    `title` VARCHAR(255) NOT NULL,
    `content` TEXT NOT NULL,
    `created_at` TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    `updated_at` TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,

    FOREIGN KEY(`user_id`) REFERENCES users(`id`)
);
```

## Commands

Name|Description|
----|-----------|
composer run **lint**|*PHPCS* with *[PSR-12](https://www.php-fig.org/psr/psr-12/)*

## Intermediate - MVC(Model, View, Controller)

<p>
    <img src="https://travis-ci.com/pronist/phpblog.svg?branch=intermediate">
    <img src="https://github.styleci.io/repos/231950937/shield?branch=intermediate" alt="StyleCI">
</p>

### Features

<https://github.com/pronist/phpblog/tree/intermediate/bootstrap/app.php>

#### Index

* [/](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/IndexController.php) - **Show** Posts (GET)

#### Auth

* [/auth/login](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/AuthController.php) - Login **Form** for a User (GET)
* [/auth](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/AuthController.php) - Create a User **Session** (POST)
* [/auth/logout](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/AuthController.php) - Delete a User **Session** (POST)

#### User

* [/users/register](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/UserController.php) - Register **Form** for a new User (GET)
* [/users](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/UserController.php) - **Create** a new User (POST)

#### Post

* [/posts/write](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/PostController.php) - Write **Form** for a new Post (GET)
* [/posts](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/PostController.php) - **Write** a new Post (POST)
* [/posts/{id}](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/PostController.php) - **Read** a Post by a post id (GET)
* [/posts/{id}/edit](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/PostController.php) - Update **Form** for Post informations (GET)
* [/posts/{id}](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/PostController.php) - **Update** for Post informations (PATCH)
* [/posts/{id}](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/PostController.php) - **Delete** a Post (DELETE)

#### Image

* [/images/{path}](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/ImageController.php) - **Get** a Image (GET)
* [/images](https://github.com/pronist/phpblog/blob/intermediate/app/Controllers/ImageController.php) - **Upload** a Image (POST)

## License

[MIT](https://github.com/pronist/phpblog/blob/intermediate/LICENSE)

Copyright 2020. [SangWoo Jeong](https://github.com/pronist). All rights reserved.
