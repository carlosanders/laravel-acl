
# Kodeine/Laravel-ACL - Tradução e Alterações para o Laravel 5.4 

[![Laravel](https://img.shields.io/badge/Laravel-~5.0-orange.svg?style=flat-square)](http://laravel.com)
[![Source](http://img.shields.io/badge/source-kodeine/laravel--acl-blue.svg?style=flat-square)](https://github.com/kodeine/laravel-acl/)
[![Build Status](http://img.shields.io/travis/kodeine/laravel--acl/master.svg?style=flat-square)](https://travis-ci.org/kodeine/laravel-acl)
[![License](http://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](https://tldrlegal.com/license/mit-license)
[![Total Downloads](http://img.shields.io/packagist/dt/kodeine/laravel-acl.svg?style=flat-square)](https://packagist.org/packages/kodeine/laravel-acl)

O Laravel ACL acrescenta Permissões(Permissions) baseadas em Função(Role) construído no **Auth System de Laravel 5**. O middleware ACL protege rotas e até mesmo métodos CRUD do Controller.


# Índice
* [Requisitos](#requirements)
* [Guia de Introdução](#getting-started)
* [Documentação](#documentation)
* [Roteiro](#roadmap)
* [Registros de alterações](#change-logs)
* [Diretrizes de contribuição](#contribution-guidelines)


# <a name="requirements"></a>Requisitos

* This package requires PHP 5.5+

# <a name="getting-started"></a>Guia de Introdução

1. Adicione o pacote no seu `composer.json` e atualize sua dependência com `composer update`:

```
"require": {
...
"kodeine/laravel-acl": "~1.0@dev",
...
},
```

2. Adicione o pacote ao seu application service providers em `config/app.php`.

```php
'providers' => [

'Illuminate\Foundation\Providers\ArtisanServiceProvider',
'Illuminate\Auth\AuthServiceProvider',
...
'Kodeine\Acl\AclServiceProvider',

],
```

3. Publique as migrações de pacotes para o seu aplicativo e execute-as com o `php artisan migrate`.

```
$ php artisan vendor:publish --provider="Kodeine\Acl\AclServiceProvider"
```

> **Use seus próprios models.**
> Depois de publicar, ele publica o arquivo de configuração onde você pode definir seus próprios Models que devem se estender aos Models do ACL.

4. Adicione o middleware em seu arquivo `app/Http/Kernel.php`.

```php
protected $routeMiddleware = [

....
'acl' => 'Kodeine\Acl\Middleware\HasPermission',

];
```

5. Adicione a trait HasRole em seu `User` Model.

```php
use Kodeine\Acl\Traits\HasRole;

class User extends Model implements AuthenticatableContract, CanResetPasswordContract
{
use Authenticatable, CanResetPassword, HasRole;
}
```

# <a name="documentation"></a>Documentação

Acesse o [Wiki](https://github.com/kodeine/laravel-acl/wiki) para mais informações.

# <a name="roadmap"></a>Roteiro

Aqui está a lista TODO para a próxima versão (**2.0**).

* [ ] Refactoring the source code.
* [ ] Correct all issues.
* [ ] Adding cache to final user permissions.

# <a name="change-logs"></a>Registros de alterações

**22 de Setembro 2016**
* [x] Adicionado testes unitários

**20 de setembro de 2016**
* [X] Adicionado suporte para Laravel 5.3

*19 de setembro de 2016*
* [X] Adicionado suporte de cache para as Roles e Permissions.

*14 de junho de 2015*
* [X] Adicionado a compatibilidade com versões anteriores para o laravel 5.0 e para o método lists().
* [X] Adicionado [Blade Template Extensions] (https://github.com/carlosanders/laravel-acl/wiki/Blade-Extensions).

*28 de março de 2015*
* [X] Adicionado a Role Scope para que todos os usuários tenham um papel específico. Por exemplo, `User::role('admin')->get();` listará todos os usuários com a função(Role) `admin`.

*7 de março de 2015*
* [X] `is()` e `can()` agora suportam vírgula para `AND` e PIPE para operador `OR`. Ou passar um operador como um segundo parâmetro. [Mais informações] (https://github.com/carlosanders/laravel-acl/wiki/Validate-Permissions-and-Roles)
* [X] Você pode vincular várias permissões para que eles herdam a Permissão. [Mais informações] (https://github.com/carlosanders/laravel-acl/wiki/Permissions-Inheritance)


# <a name="contribution-guidelines"></a>Diretrizes de contribuição

O suporte segue os padrões de codificação PHP PSR-2 e a versão semântica.

Informe qualquer problema que você encontrar na página de edições.
Os pedidos de pull são bem-vindos.