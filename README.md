<h1 align="center">Laravel Domain Driven Design Template</h1>

## Folder Structure

```bash
/app
└── /Domains
    └── /Domain1
        ├── /Http
        ├── /Migrations
        ├── /Models
        ├── /Providers
    └── /Domain1
        ├── /Http
        ├── /Migrations
        ├── /Models
        ├── /Providers
/bootstrap
/config
/database
/docker
/public
/resources
/routes
├── /domain1
├── /domain2
/storage
/tests
/vendor
.env
```

## Installation

-   Run `cp .env.example .env`.
-   Run the below command to install Composer dependencies:
    ```sh
    docker run --rm \
        -u "$(id -u):$(id -g)" \
        -v $(pwd):/var/www/html \
        -w /var/www/html \
        laravelsail/php81-composer:latest \
        composer install --ignore-platform-reqs
    ```
-   Run `./vendor/bin/sail up -d`.

`sail` is equivalent of `docker-compose`, read [`laravel/sail`](https://laravel.com/docs/8.x/sail) doc.

## Add New Domain

-   Create a domain folder (e.g. _Domain3_) in `app/Domains`.
-   Create `DomainServiceProvider.php` in `App\Domains\Domain3\Providers` namespace and register necessary providers in it.
-   Register the newly created `DomainServiceProvider` in `config/app.php`
-   Create api files in `routes/domain3`.

## Database Migrations

-   To create a new migration for a specific domain:

    ```bash
    php artisan make:migration create_users_table --path=/app/Domains/Domain3/Migrations
    ```

-   To run migrations for a specific domain:

    ```bash
    php artisan migrate --path=/app/Domains/Domain3/Migrations
    ```
