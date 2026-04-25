# No Framework — Custom PHP MVC

A fully functional PHP web application built **without Laravel or Symfony** — constructed from scratch using best-in-class standalone libraries. Demonstrates deep understanding of how modern PHP frameworks work under the hood: service containers, middleware pipelines, routing, templating, authentication, and CSRF protection.

## What This Demonstrates

- Manual **dependency injection container** wiring (League\Container)
- Custom **routing layer** with middleware support (League\Route)
- **PSR-7 HTTP messages** and PSR-15 middleware (Laminas Diactoros)
- **Twig templating** engine integration
- **Eloquent ORM** used standalone (without Laravel)
- **Authentication & authorization** via Cartalyst Sentinel
- **CSRF protection** with Slim\Csrf
- **Validation** with Respect\Validation
- **Pagination** via Illuminate Pagination (standalone)
- **Environment config** via vlucas/phpdotenv

## Tech Stack

| Component | Library |
|---|---|
| DI Container | `league/container` |
| Router | `league/route` |
| HTTP Messages | `laminas/laminas-diactoros` |
| HTTP Runner | `laminas/laminas-httphandlerrunner` |
| Templates | `twig/twig` |
| ORM | `illuminate/database` (Eloquent) |
| Auth | `cartalyst/sentinel` |
| CSRF | `slim/csrf` |
| Validation | `respect/validation` |
| Pagination | `illuminate/pagination` |
| Env Config | `vlucas/phpdotenv` |
| Error Handling | `spatie/ignition` |

## Project Structure

```
app/
├── Config/
│   └── Config.php                    # App configuration
├── Core/
│   ├── App.php                       # Bootstrap: binds container, runs router
│   └── Container.php                 # DI container setup
├── Exceptions/
│   └── ExceptionHandler.php
├── Http/
│   ├── Controllers/
│   │   ├── Auth/
│   │   │   ├── LoginController.php
│   │   │   ├── LogoutController.php
│   │   │   └── RegisterController.php
│   │   ├── DashboardController.php
│   │   ├── HomeController.php
│   │   └── UserController.php
│   └── Middleware/
│       ├── RedirectIfAuthenticated.php
│       ├── RedirectIfGuest.php
│       ├── FlashOldDataMiddleware.php
│       └── ExampleMiddleware.php
├── Models/
│   └── User.php                      # Eloquent model (standalone)
└── Providers/
    ├── AppServiceProvider.php
    ├── AuthServiceProvider.php
    ├── ConfigServiceProvider.php
    └── CsrfServiceProvider.php
```

## Installation

```bash
git clone https://github.com/Ma7moud1599/No_Framework.git
cd No_Framework

composer install
cp .env.example .env

# Configure DB credentials in .env, then:
php artisan migrate   # or run migrations manually
php -S localhost:8000 -t public
```

## Key Design Patterns

- **Service Providers** — each concern (auth, config, CSRF) registers its own bindings
- **Single-action Controllers** — each controller handles exactly one HTTP action
- **Middleware pipeline** — auth guard and CSRF check applied per route group
- **Repository-ready** — models are separated from controllers, ready for repository pattern

## License

MIT
